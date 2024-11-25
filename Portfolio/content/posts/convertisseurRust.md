---
date: '2024-11-25T19:04:44+01:00'
draft: false
title: 'Convertisseur Rust'
summary: Simple rust converter
tags: ['Rust', 'Docker']
categories: ['langage bas niveau']
---

# Mon convertisseur rust dockerisée

Il s'agit d'un projet qui fait suite à un autre projet similaire qui était de créer un convertisseur de base en C. Le but de ce convertisseur en Rust est de comparer quelle langage est le plus rapide entre le C et le Rust.

Ce convertisseur prend en entrée un nombre dans une certaine base, puis la sortie est ce nombre convertis en binaire, octal, decimal et héxadécimal

le lien du dépôt : <https://github.com/Tonguechaude/Convertisseur-Rust>

Le code est amateur, il s'agit d'une première prise en main du langage :)

```Rust
fn welcome_screen ()
{
    loop
    {
        screen_cleaner();

        cool_tag();
        let a = time::Duration::from_millis(4000);
        sleep(a);


        screen_cleaner();
        println!("-------------------------------------------");
        println!(">>> Welcome to Number System Converter <<<");
        println!("------------------------------------------- \n");

        println!(">> Select Conversion Type:");
        println!("> 1. Binary Conversion");
        println!("> 2. Decimal Conversion");
        println!("> 3. Octal Conversion");
        println!("> 4. Hexadecimal Conversion");
        println!("> 5. Exit the Program \n \n");

        println!("Enter the number & Hit ENTER: ");

        let mut input = String::new(); //crée un String
        io::stdin()
            .read_line(&mut input) // lit ce qui est écrit dans l’entrée standard et le met dans input
            .expect("Failed to read line");

        let choice: i32 = match input
            .trim()  // pour supprimer les espaces blancs y compris les \n
            .parse()  // pour transformer la string en int
        {
            Ok(num) => num,
            Err(_) => {
                println!("Error: the number must be between 1 to 5.");
                println!("Press any key to continue...");
                wait_for_keypress();
                continue;
            }
        };

        match choice {
            1 => user_input(1),
            2 => user_input(2),
            3 => user_input(3),
            4 => user_input(4),
            5 => exit_screen(),
            _ => {
                println!("\nError: the number must be between 1 to 5.\n");
                println!("Press any key to continue...");
                wait_for_keypress();
                welcome_screen();
            }
        }
    }

}
```
Pour une rigueur digne d'un bon dev, il dispose de tout une batterie de Test sous cette forme :

```Rust
use Convertisseur_Rust::convertisseur;

#[test]
fn test_binary_to_octal ()
{
    assert_eq!(convertisseur::binary_to_octal(101101), 55);
    assert_eq!(convertisseur::binary_to_octal(111111111111111), 77777);
    assert_eq!(convertisseur::binary_to_octal(110010), 62);
    assert_eq!(convertisseur::binary_to_octal(101010), 52);
}
```

Pour prendre en main la technologie Docker, ce projet dispose aussi d'un DockerFile. Le principale but de cette manoeuvre c'est de lancer mon programme dans un conteneur pour que l'utilisateur n'ai pas besoin de le compiler, ou de chercher une version compilée compatible avec l'architecture de son processeur.

```yml
FROM ubuntu:24.04

# Installer bash pour un shell interactif
RUN apt-get update && apt-get install --no-install-recommends -y bash \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

# Créer un dossier de travail
WORKDIR /usr/src/convertisseur

# Copier le binaire compilé depuis l'environnement CI
COPY . /usr/src/convertisseur

# Définir le point d'entrée par défaut
CMD ["./target/release/convertisseur_rust"]
```

Et la cerise sur le gateau, pour simplifier tout le processus le projet dispose d'un start.sh permettant de build le conteneur pour le projet puis de le lancer dans un shell interactif ...

```bash
cargo build --release \
&& cargo test \
&& docker build -t convertisseur_rust . \
&& docker run --rm -it convertisseur_rust
```
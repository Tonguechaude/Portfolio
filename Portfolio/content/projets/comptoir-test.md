---
date: '2024-11-25T19:04:44+01:00'
draft: false
title: 'Analyse des Logiciels Libres du Comptoir du Libre'
summary: Un outil en Rust pour analyser les logiciels libres du Comptoir du Libre en vérifiant la disponibilité de leurs sites web et de leurs dépôts de code source.
tags: ['Rust', 'SQLite', 'Asynchrone', 'API']
categories: ['Application']
---

# Analyse des Logiciels Libres du Comptoir du Libre

Ce projet en Rust a pour objectif d'analyser les logiciels libres répertoriés sur le site [Comptoir du Libre](https://comptoir-du-libre.org/). Il vérifie la disponibilité des sites web et des dépôts de code source associés à chaque logiciel, en enregistrant les résultats dans une base de données SQLite et en exportant les données au format CSV.
Le **Comptoir du Libre** est une plateforme collaborative qui recense les logiciels libres métiers utiles aux services publics, ainsi que leurs utilisateurs et prestataires. [Lien vers le code source](https://gitlab.adullact.net/echallias/comptoir_tests_urls)

## Contexte du Projet

Ce script a été fait dans le cadre de mon alternance à l'[ADULLACT](https://adullact.org)

Le projet s'inscrit dans le cadre d'une étude visant à évaluer la fiabilité des ressources en ligne des logiciels libres. L'objectif est de fournir une analyse détaillée de la disponibilité des sites web et des dépôts de code source, afin d'aider les utilisateurs à identifier les logiciels dont les ressources en ligne sont les plus fiables.

## Méthodes de Travail et Résultats Obtenus

Le programme suit les étapes suivantes :

1. **Chargement des Données** : Téléchargement du fichier JSON exporté par le Comptoir du Libre, contenant des informations sur les logiciels libres.

2. **Analyse Asynchrone** : Utilisation de la bibliothèque `reqwest` pour effectuer des requêtes HTTP asynchrones, permettant de tester la disponibilité des sites web et des dépôts de code source.

3. **Gestion des Concurrences** : Implémentation d'un sémaphore avec la bibliothèque `tokio` pour limiter le nombre de requêtes concurrentes, évitant ainsi une surcharge du serveur cible.

4. **Stockage des Résultats** : Enregistrement des résultats dans une base de données SQLite, avec une table dédiée aux résultats des tests.

5. **Exportation des Données** : Génération d'un fichier CSV contenant les résultats, facilitant ainsi l'analyse et la présentation des données.

## Compétences Travaillées  

Ce projet a permis de développer et de renforcer les compétences suivantes :

- **Programmation en Rust** : Approfondissement de la maîtrise du langage Rust, notamment en ce qui concerne la gestion des erreurs, la manipulation des fichiers et l'utilisation des bibliothèques externes.

- **Programmation Asynchrone** : Apprentissage de la programmation asynchrone en Rust avec la bibliothèque `tokio`, permettant de gérer efficacement les opérations d'entrée/sortie sans blocage.

- **Gestion des Concurrences** : Mise en œuvre de mécanismes de contrôle de la concurrence, tels que les sémaphores, pour limiter le nombre de requêtes simultanées et éviter la surcharge des serveurs cibles.

- **Interaction avec des APIs Web** : Utilisation de la bibliothèque `reqwest` pour effectuer des requêtes HTTP et analyser les réponses, facilitant ainsi l'interaction avec des services web externes.

- **Manipulation de JSON** : Utilisation de la bibliothèque `serde_json` pour parser et manipuler des données au format JSON, couramment utilisées pour l'échange de données entre applications.

- **Gestion de Bases de Données** : Création et manipulation d'une base de données SQLite avec la bibliothèque `rusqlite`, permettant de stocker et de gérer efficacement les résultats des tests.

- **Exportation de Données** : Génération de fichiers CSV à partir de données structurées, facilitant l'analyse et la présentation des résultats.

## Exemple de Code

Voici un extrait du code source illustrant la vérification de la disponibilité d'une URL :

```rust
use reqwest::Client;
use reqwest::StatusCode;

async fn test_url(client: &Client, url: &str) -> Result<StatusCode, String> {
    println!("Test en cours pour l'URL: {}", url);
    match client
        .head(url)
        .header("User-Agent", "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:132.0) Gecko/20100101 Firefox/132.0")
        .send()
        .await
    {
        Ok(res) => {
            println!("Réponse reçue pour {}: {}", url, res.status());
            Ok(res.status())
        }
        Err(e) => {
            let error_message = if e.is_timeout() {
                format!("Erreur: Timeout pour {}", url)
            } else if e.is_connect() {
                format!("Erreur de connexion pour {}: {}", url, e)
            } else {
                format!("Erreur lors de la requête pour {}: {}", url, e)
            };
            println!("{}", error_message);
            Err(error_message)
        }
    }
}
```

Cet extrait montre comment effectuer une requête HTTP de type HEAD de manière asynchrone pour tester la disponibilité d'une URL.

## Conclusion

Ce projet a permis de développer une application robuste et efficace pour analyser la disponibilité des ressources en ligne des logiciels libres. Il a également offert l'opportunité de renforcer des compétences clés en programmation Rust, en gestion de la concurrence et en interaction avec des APIs web. 
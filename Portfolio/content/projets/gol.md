---
date: '2024-11-25T19:04:44+01:00'
draft: false
title: 'Jeu de la Vie de Conway en Java avec Interface Graphique Swing'
summary: Implémentation du célèbre automate cellulaire en Java avec une interface graphique interactive.
tags: ['Java', 'Swing', 'Jeu']
categories: ['Application']
---

Ce projet est une implémentation en Java du célèbre automate cellulaire "Jeu de la Vie" de John Horton Conway, accompagné d'une interface graphique interactive réalisée avec Swing.

## Contexte du projet

Ce projet a été fait sur mon temps libre car ce jeu m'interesse beaucoup et je voulais avoir le mien

Le "Jeu de la Vie" est un automate cellulaire où chaque cellule d'une grille évolue selon des règles simples, générant des motifs complexes et dynamiques. L'objectif de ce projet était de reproduire ce jeu en Java, en mettant l'accent sur la création d'une interface graphique intuitive et réactive.

## Structure du projet

Le projet est organisé comme suit :

```
├── controlleur
│   └── ControlleurJeu.java
├── Main.java
├── model
│   ├── Cellule.java
│   ├── Grille.java
│   ├── JeuDeLaVie.java
│   └── Motif.java
├── README.md
└── vue
    ├── Fenetre.java
    └── Rendu.java
```

- **`controlleur/ControlleurJeu.java`** : Gère la logique du jeu, y compris l'évolution des générations et la gestion des événements utilisateur.

- **`Main.java`** : Point d'entrée de l'application, initialisant l'interface graphique et le contrôleur.

- **`model/`** : Contient les classes représentant les éléments du jeu :
  - **`Cellule.java`** : Représente une cellule individuelle de la grille.
  - **`Grille.java`** : Gère l'ensemble des cellules et leur état.
  - **`JeuDeLaVie.java`** : Implémente les règles du jeu et l'évolution des générations.
  - **`Motif.java`** : Permet de définir et de charger des motifs prédéfinis.

- **`vue/`** : Contient les classes liées à l'interface graphique :
  - **`Fenetre.java`** : Crée la fenêtre principale de l'application.
  - **`Rendu.java`** : Responsable du rendu graphique de la grille et des cellules.

## Fonctionnalités

- **Interface Graphique Interactive** : L'utilisateur peut interagir avec la grille en cliquant sur les cellules pour les activer ou les désactiver.

- **Contrôle de l'Évolution** : Des boutons permettent de démarrer, arrêter et réinitialiser le jeu, ainsi que de définir la vitesse d'évolution des générations.

- **Chargement de Motifs** : La possibilité de charger des motifs prédéfinis pour observer des comportements complexes.

## Compétences travaillées

- **Programmation Orientée Objet (POO)** : Conception de classes et d'interfaces pour modéliser le jeu et son environnement.

- **Principes SOLID** : Application des principes SOLID pour une conception logicielle robuste et évolutive.

- **Gestion des Événements en Swing** : Implémentation de gestionnaires d'événements pour les interactions utilisateur.

- **Conception d'Interfaces Graphiques** : Création d'une interface utilisateur intuitive et réactive avec Swing.

- **Algorithmes d'Automates Cellulaires** : Implémentation des règles du "Jeu de la Vie" et gestion de l'évolution des générations.

## Exemple de code

Voici un extrait de la classe `Grille.java` illustrant l'évolution des générations :

```java
public void maj() {
    Cellule[][] nouvelleGrille = new Cellule[lignes][colonnes];

    for (int i = 0; i < lignes; i++) {
        for (int j = 0; j < colonnes; j++) {
            int voisinesEnVies = compterVoisineEnVie(i, j);
            boolean enVie = cellules[i][j].estVivante()
                ? (voisinesEnVies == 2 || voisinesEnVies == 3)
                : (voisinesEnVies == 3);

            nouvelleGrille[i][j] = new Cellule(enVie);
        }
    }
    cellules = nouvelleGrille;
}
```

Cette méthode calcule l'état de la grille pour la génération suivante en appliquant les règles du jeu.

## Capture d'écran de l'interface 

![Interface graphique](/img/gol.png)

## Lien vers le dépôt

Le code source complet est disponible sur GitHub : [Jeu De La Vie](https://github.com/Tonguechaude/GOL)

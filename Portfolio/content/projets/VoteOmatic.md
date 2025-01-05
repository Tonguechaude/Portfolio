---
date: '2024-11-25T19:04:44+01:00'
draft: false
title: 'VoteOmatic'
summary: application de vote sécurisée
tags: ['Java', 'Docker', 'Docker compose', 'Spring', 'MariaDB', 'ElGamal']
categories: ['Application', 'Cryptographie']
---

# Application de Vote en Ligne

## Contexte du Projet
Ce projet a été réalisé dans le cadre d’un travail académique en **BUT Informatique**, destiné à simuler un système de vote électronique sécurisé et convivial. L’objectif était de développer une application fonctionnelle qui permettrait à des utilisateurs de voter de manière anonyme tout en respectant des contraintes de sécurité.

### Contexte spécifique :
- **Commande académique** : Créer une application Java pour gérer des sessions des référendums.
- **Contraintes** :
  - **Durée** : 2 mois.
  - **Travail en équipe** : 4 membres au total, chacun ayant des responsabilités spécifiques.
  - **Technologies imposées** : Utilisation de **Java**.
  - **Objectifs principaux** :
    - Assurer la sécurité des votes (confidentialité, intégrité, ElGamal).
    - Proposer une interface utilisateur claire et intuitive.

---

## Méthodes de Travail et Résultats Obtenus

### Étapes du Projet
1. **Analyse des besoins** :
   - Élaboration d’un cahier des charges reprenant les fonctionnalités clés : création de sessions de vote, gestion des utilisateurs et chiffrement des données.
   - Répartition des tâches entre les membres de l’équipe (front-end, back-end, base de données).

2. **Développement technique** :
   - **Front-end** : Conception d’une interface utilisateur ergonomique avec **HTML/CSS**.
   - **Back-end** :
     - Création des fonctionnalités principales en **Java/Spring** : gestion des utilisateurs, stockage des votes dans une base de donnée **MariaDB**.
     - Mise en place d’un système d’authentification sécurisé.
   - **Base de données** :
     - Modélisation et implémentation d’un schéma de base de données relationnelle pour stocker les sessions de vote, les utilisateurs, et les résultats.

3. **Tests et validation** :
   - Réalisation de tests unitaires sur les principales fonctionnalités (Chiffrement, calcul des résultats).
   - Scénarios de test utilisateur pour vérifier l’expérience générale et la facilité d’utilisation.

### Résultats Obtenus
- **Interface utilisateur** :
  - Page de connexion sécurisée.
  - Tableau de bord permettant de créer ou de rejoindre une session de vote.
  - Visualisation des résultats via des graphiques dynamiques.
- **Preuves visuelles** :
  - Capture d’écran de l’interface de vote :  
    ![Interface de vote](/img/interface-vote.png) 
  - Capture des résultats affichés sous forme de graphique :  
    ![Résultats des votes](/img/interface-resultat.png)

---

## Compétences Travaillées

### Compétences Techniques
- **Programmation Web** : Développement full-stack avec **Java**, **HTML/CSS**, **Spring/SpringBoot/Thymeleaf**, **MariaDB**, **Docker**.
- **Sécurité** : Mise en œuvre de techniques pour protéger les données sensibles (hashage des mots de passe, validation des entrées utilisateur et algorithme ElGamal).
- **Base de données** : Conception et optimisation d’une base relationnelle adaptée à un système de vote avec **MariaDB**, **Adminer** et **JDBC**.
- **Gestion de projet** : Organisation du travail en équipe avec des outils de suivi comme **Discord** et **Gitlab**.

### Compétences Humaines
- **Collaboration en équipe** :
  - Communication efficace entre les membres pour résoudre les problèmes techniques.
  - Répartition équitable des tâches en fonction des compétences de chacun.
- **Gestion du temps** :
  - Respect des délais grâce à une bonne planification et à des réunions régulières.
- **Autonomie et apprentissage** :
  - Découverte approfondie des concepts liés à la sécurité informatique et au développement d’applications interactives.

### Contribution Personnelle
Dans ce projet, ma contribution personnelle a porté principalement sur :
1. La conception de l’interface front-end, en veillant à l’ergonomie et à l’esthétique via SpringBoot et Thymeleaf.
2. La mise en œuvre des fonctionnalités de la base de données, incluant la modélisation et la gestion des requêtes SQL.
3. Implémentation d'une CI/CD pour le projet.
4. Gestion des conteneurs Docker nécessaire au projet

---

## Conclusion
Ce projet a été une excellente opportunité pour renforcer mes compétences techniques et humaines. Il m’a permis de mieux comprendre les enjeux de la gestion de projets collaboratifs tout en développant une application concrète et fonctionnelle.

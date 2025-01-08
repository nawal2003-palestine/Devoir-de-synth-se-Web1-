



---

# Gestion École

## Description
Ce projet est une application web développée en PHP qui permet de gérer une liste d'étudiants avec des rôles spécifiques (administrateur et étudiant). L'accès à l'application est sécurisé grâce à un système d'authentification, et les utilisateurs peuvent interagir avec différentes fonctionnalités selon leur rôle.

## Fonctionnalités
### Authentification
- Système de connexion sécurisé via le fichier `login.php`.
- Gestion des sessions utilisateur.
- Redirection basée sur le rôle :
  - **Administrateur** : Gestion des étudiants.
  - **Étudiant** : Consultation et modification de son profil.

### Gestion des Étudiants
#### Rôle : Administrateur
- Afficher la liste des étudiants.
- Ajouter, modifier ou supprimer des étudiants.
- Modifier son mot de passe.

#### Rôle : Étudiant
- Consulter ses informations personnelles.
- Modifier sa photo de profil.
- Modifier son mot de passe.

## Structure du Projet
```plaintext
gestion_ecole/
├── index.php
├── Acces_BD/
│   ├── .env
│   ├── connexion.php
│   ├── Login.php
│   ├── Administrateur.php
│   └── Etudiant.php
├── IHM/
│   ├── Administrateur/
│   │   ├── form.php
│   │   ├── index.php
│   │   └── affichage.php
│   ├── Etudiant/
│   │   ├── form.php
│   │   └── index.php
│   └── public/
│       ├── header.php
│       ├── footer.php
│       ├── nav_barre.php
│       ├── css/
│       │   └── style.css
│       └── photos/
└── Gestion_Actions/
    ├── login.php
    ├── Administrateur.php
    └── Etudiant.php
```

## Configuration
### Base de Données
Fichier `.env` pour la configuration :
```plaintext
Serveur=localhost
Utilisateur=root
Password=
db_name=gestion_ecole
```

### Structure SQL
Créer la base de données et les tables nécessaires :
```sql
CREATE DATABASE gestion_ecole;
USE gestion_ecole;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'etudiant') NOT NULL,
    etudiant_id INT NULL
);

CREATE TABLE etudiant (
    code INT PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(50) NOT NULL,
    prenom VARCHAR(50) NOT NULL,
    sexe ENUM('M', 'F') NOT NULL,
    photo VARCHAR(255),
    email VARCHAR(100) NOT NULL UNIQUE,
    langues TEXT,
    specialite VARCHAR(100) NOT NULL
);
```

## Instructions d'Installation
1. Clonez ce dépôt sur votre machine.
2. Configurez la base de données en utilisant la structure SQL ci-dessus.
3. Modifiez le fichier `.env` pour correspondre à vos paramètres de base de données.
4. Lancez l'application en ouvrant `index.php` via un serveur local (ex. XAMPP ou WAMP).

## Fonctionnalités Futures
- Export des données en format CSV.
- Recherche avancée dans la liste des étudiants.
- Ajout d'une interface utilisateur plus intuitive.

---

Cela permet de documenter votre projet de manière claire et détaillée.

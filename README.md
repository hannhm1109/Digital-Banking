# 🏦 Système Bancaire  - Application Full Stack

Application bancaire numérique complète développée avec **Spring Boot (Java)** et **Angular**. Cette solution reproduit un système bancaire en ligne avec gestion des clients et comptes, authentification sécurisée, opérations financières, contrôle d'accès utilisateur et tableaux de bord analytiques.

## Fonctionnalités Principales

### 🔒 Authentification et Autorisation
- Connexion sécurisée avec authentification JWT
- Contrôle d'accès basé sur les rôles (UTILISATEUR, ADMINISTRATEUR)
- Protection des routes via les Guards Angular
- Sections réservées aux administrateurs (logs et gestion utilisateurs)

### 👤 Gestion des Utilisateurs et Clients
- Administration des utilisateurs internes par les administrateurs
- Activation/désactivation des comptes utilisateurs
- Consultation de la liste complète des clients
- Création, modification et suppression de clients
- Recherche de clients par mot-clé

### 💰 Comptes et Opérations Bancaires
- Consultation des détails de compte (Courant / Épargne)
- Opérations de crédit et débit
- Virements entre comptes
- Historique des opérations par compte
- Traçabilité de l'opérateur pour chaque transaction

### 📊 Tableau de Bord Analytique
- Graphiques interactifs avec Chart.js
- Diagramme circulaire des types de comptes (Courant vs Épargne)
- Graphique en barres des opérations par type (Débit, Crédit, Virement)
- Graphique des clients les plus actifs
- Cartes de statistiques : nombre de clients, comptes, solde total, nombre d'opérations

### 📋 Journalisation des Actions
- Section logs réservée aux administrateurs
- Consultation des journaux backend pour audit et débogage

## Technologies Utilisées

**Frontend**
- Framework : Angular 20
- Graphiques : Chart.js (ng2-charts)
- Langage : TypeScript

**Backend**
- Framework : Spring Boot
- Sécurité : Spring Security + JWT
- Persistance : Spring Data JPA
- Langage : Java 17+

**Infrastructure**
- Base de données : H2 / MySQL
- Build : Maven
- Documentation : Swagger UI
- Authentification : JWT avec intercepteurs

## Architecture du Projet

### Backend : `ebanking-backend/`
```
├── config/             # Configuration Spring Security + JWT
├── controllers/        # APIs REST (auth, customer, account, logs)
├── services/           # Logique métier
├── entities/           # Modèles JPA
├── dtos/               # DTOs Requête/Réponse
├── repositories/       # Spring Data JPA
├── mappers/            # Mapping DTO ↔ Entity
├── logs/               # Endpoints de récupération des logs
└── resources/          # Configuration app & données SQL
```

### Frontend : `ebanking-frontend/`
```
├── app/
│   ├── services/           # Services Auth, Customer, Account, Log
│   ├── guards/             # AuthGuard pour les routes
│   ├── interceptors/       # Injection du token JWT
│   ├── login/              # Formulaire de connexion
│   ├── dashboard/          # Tableau de bord avec graphiques
│   ├── customers/          # CRUD clients
│   ├── accounts/           # Opérations sur comptes
│   ├── admin/              # Logs + Gestion utilisateurs
│   └── layout/             # Templates navbar + sidebar
```

## API REST - Points d'Accès

**Authentification**
- `POST /auth/login` → Connexion utilisateur (JWT)

**Gestion Clientèle**
- `GET /customers` → Liste tous les clients
- `POST /customers` → Ajouter un client
- `PUT /customers/{id}` → Modifier un client
- `DELETE /customers/{id}` → Supprimer un client

**Services Bancaires**
- `POST /accounts/credit` → Créditer un compte
- `POST /accounts/debit` → Débiter un compte
- `POST /accounts/transfer` → Virement entre comptes
- `GET /accounts/{id}` → Détails du compte

**Administration**
- `GET /logs` → Consulter les logs système
- `POST /users/reset-password` → Réinitialiser mot de passe
- `POST /users/change-password` → Changer son mot de passe

*Toutes les routes sont protégées par JWT avec contrôle des rôles.*

## 🚀 Lancement de l'Application

### Démarrage du Backend
```bash
cd ebanking-backend
./mvnw spring-boot:run
```

Documentation Swagger disponible à :  
http://localhost:8085/swagger-ui.html

### Démarrage du Frontend
```bash
cd ebanking-frontend
npm install
ng serve
```

Application frontend accessible à :  
http://localhost:4200

## Caractéristiques de l'Interface

- Interface responsive avec Bootstrap 5
- Graphiques responsifs et animés
- Barre latérale avec liens dynamiques selon le rôle utilisateur
- Identité visuelle SBR Bank cohérente

## Auteur

**Hanane Nahim**

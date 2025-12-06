# Architecture Micro-services avec RestTemplate
<img width="1920" height="1078" alt="eureka-services" src="https://github.com/user-attachments/assets/a1e546f5-6f41-4b87-b905-1893a455d9aa" />
<img width="1920" height="1080" alt="eureka-services1" src="https://github.com/user-attachments/assets/433362b4-1ca2-44aa-bd07-b7330d6f5f0e" />


Ce projet démontre une architecture micro-services complète en Java/Spring Boot utilisant RestTemplate pour la communication entre services.

## Vue d'ensemble

L'architecture est composée de 4 services principaux:

- **Eureka Server**: Serveur de découverte de services
- **Service Gateway**: Passerelle API pour router les requêtes
- **Service Client**: Gestion des clients
- **Service Voiture**: Gestion des véhicules

Les services communiquent entre eux via RestTemplate et sont enregistrés dynamiquement sur le serveur Eureka.

## Structure du projet

```
projectmicro/
├── eureka-server/        # Serveur de découverte (port 8761)
├── service-gateway/      # API Gateway (port 8080)
├── client-service/       # Service clients (port 8001)
└── service-voiture/      # Service véhicules (port 8002)
```

## Prérequis

- Java 11 ou supérieur
- Maven 3.6+
- Une base de données (MySQL/PostgreSQL configurée dans application.yml)

## Installation et démarrage

### 1. Démarrer Eureka Server

```bash
cd eureka-server
mvn spring-boot:run
```

L'interface Eureka sera disponible à: http://localhost:8761

### 2. Démarrer les services

Dans des terminaux séparés:

```bash
cd service-gateway
mvn spring-boot:run
```

```bash
cd client-service
mvn spring-boot:run
```

```bash
cd service-voiture
mvn spring-boot:run
```

## Architecture et communication

```
Client HTTP
    ↓
Service Gateway (8080)
    ↓
Eureka Server (8761)
    ↓
Routing vers Client Service (8001) ou Voiture Service (8002)
```

Les services s'enregistrent automatiquement auprès d'Eureka au démarrage et utilisent RestTemplate pour communiquer entre eux de manière découplée.

## Configuration

Chaque service possède un fichier `application.yml` pour configurer:
- Le port du service
- Le nom du service (pour Eureka)
- Les connexions aux bases de données
- Les paramètres Eureka

## Endpoints principaux

- **Eureka**: http://localhost:8761
- **Gateway**: http://localhost:8080
- **Client Service**: http://localhost:8001
- **Voiture Service**: http://localhost:8002

## Proofs d'exécution

Voir les screenshots dans le dossier du projet pour les démonstrations de:
- L'enregistrement des services sur Eureka
- Les communications inter-services

## Contribution

Ce projet est un TP d'apprentissage sur les architectures micro-services.

## Notes

- Assurez-vous que les ports spécifiés (8080, 8001, 8002, 8761) ne sont pas utilisés
- Configurez les propriétés de base de données avant de lancer les services
- Les services doivent démarrer dans l'ordre: Eureka Server → Gateway → Services métier

# Guide d'Exécution - Architecture Micro-services

## Preuves d'exécution incluses

Le dossier projet contient les screenshots suivants démontrant l'exécution:
- `eureka-services.png` - Interface Eureka avec services enregistrés
- `eureka-services1.png` - Détails des services enregistrés

## État du Repository

✅ **Git Repository Initialisé**
```
Dépôt local: C:\Users\IMADEV\Documents\projectmicro
Branche: main
Commit: 6514052 (HEAD -> main)
Message: Initial commit: Microservices architecture with RestTemplate, Eureka, and API Gateway
```

✅ **Fichiers configurés**
- README.md ✓
- .gitignore ✓
- LICENSE (MIT) ✓

✅ **Remote configuré**
- URL: https://github.com/imadev26/TP-20-Architecture-Micro-services-avec-RestTemplate.git

## Instructions de Push vers GitHub

Pour pousser le code sur GitHub, exécutez:

```bash
cd c:\Users\IMADEV\Documents\projectmicro
git push -u origin main
```

## Architecture des Services

### 1. Eureka Server (Port 8761)
Service de découverte pour enregistrer et localiser les micro-services.

### 2. Service Gateway (Port 8080)
API Gateway qui route les requêtes vers les services appropriés.

### 3. Client Service (Port 8001)
Gestion des clients - enregistré auprès d'Eureka.

### 4. Service Voiture (Port 8002)
Gestion des véhicules - enregistré auprès d'Eureka.

## Ordre de démarrage recommandé

1. **Eureka Server** - Doit démarrer en premier
2. **Service Gateway** - Attendra qu'Eureka soit disponible
3. **Client Service** - S'enregistre auprès d'Eureka
4. **Service Voiture** - S'enregistre auprès d'Eureka

## Vérification de la setup

Après démarrage des services:
- Vérifier Eureka: http://localhost:8761
- Voir les services enregistrés sur la page d'accueil
- Les screenshots fournis montrent cet état fonctionnel

## Notes importantes

- Le code source complet de chaque service est versionnné
- Les configurations d'application.yml sont incluses
- Les dépendances Maven sont définies dans les pom.xml
- Les images de preuve sont versionnées dans le repo

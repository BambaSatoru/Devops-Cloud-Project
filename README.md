# CloudAPI - Infrastructure Cloud-Native avec Kubernetes

Une application REST complète démontrant les meilleures pratiques DevOps et l'orchestration cloud. Ce projet intègre une API Flask, une base de données MySQL et un déploiement Kubernetes, illustrant une architecture microservices moderne et scalable.

## Objectif du Projet

Ce projet showcas une pile technologique complète pour :
- Développer une API REST sécurisée et performante
- Containeriser l'application avec Docker
- Orchestrer les services avec Kubernetes
- Implémenter l'infrastructure-as-code (IaC)
- Démontrer les bonnes pratiques DevOps

## Architecture

```
┌─────────────────────────────────────────────────┐
│          Kubernetes Cluster (Minikube)          │
├─────────────────────────────────────────────────┤
│  ┌──────────────┐         ┌─────────────────┐  │
│  │ Flask API    │◄───────►│  MySQL Database │  │
│  │ Container    │         │   Container     │  │
│  └──────────────┘         └─────────────────┘  │
│  Port: 5000               Port: 3306           │
└─────────────────────────────────────────────────┘
```

## Prérequis

- Docker (≥ 20.0)
- Kubernetes (Minikube pour le développement local)
- kubectl (outil CLI Kubernetes)
- Python 3.8+
- MySQL 8.0+

## Structure du Projet

```
.
├── app.py                      # Application Flask (endpoints REST)
├── requirements.txt            # Dépendances Python
├── Dockerfile                  # Image Docker pour l'API
├── init-job.yaml              # Job Kubernetes pour initialiser la DB
├── mysql-deployment.yaml      # Déploiement MySQL
├── flask-api-deployment.yaml  # Déploiement Flask API
└── README.md
```

## Détails Techniques

### API Flask
- Framework : Flask
- Base de données : MySQL 8.0
- Endpoints :
  - GET /users - Récupère la liste des utilisateurs
  - POST /users - Crée un nouvel utilisateur

### Docker et Kubernetes
- Containerisation avec Docker pour la portabilité
- Déploiement orchestré via Kubernetes
- Gestion des secrets et configurations via ConfigMaps
- Persistance des données avec Persistent Volumes

## Déploiement

### 1. Préparer l'image Docker

```bash
docker build -t <docker-username>/flask-api:latest .
docker login
docker push <docker-username>/flask-api:latest
```

### 2. Démarrer Kubernetes

```bash
minikube start
```

### 3. Déployer l'infrastructure

```bash
# Initialiser la base de données
kubectl apply -f init-job.yaml

# Déployer MySQL
kubectl apply -f mysql-deployment.yaml

# Déployer l'API Flask
kubectl apply -f flask-api-deployment.yaml
```

### 4. Vérifier le déploiement

```bash
# Voir les jobs
kubectl get jobs

# Voir les pods
kubectl get pods

# Voir les services
kubectl get svc

# Vérifier les logs
kubectl logs -f deployment/flask-api
```

### 5. Accéder à l'API

```bash
# Port-forward vers l'API
kubectl port-forward svc/flask-api-service 5000:5000

# Tester les endpoints
curl http://localhost:5000/users
curl -X POST http://localhost:5000/users -H "Content-Type: application/json" -d '{"name":"John"}'
```

## Composition du Projet

- Python : 89.6% (logique applicative)
- Dockerfile : 10.4% (configuration conteneur)

## Concepts DevOps Démontrés

Containerisation - Docker et images optimisées
Orchestration - Déploiements Kubernetes
Infrastructure as Code - YAML manifests
Scalabilité - Répliques de pods configurables
Persistance - Gestion des données dans Kubernetes
Monitoring - Vérification de l'état des services

## Ressources Utiles

- [Documentation Kubernetes](https://kubernetes.io/docs/)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Docker Documentation](https://docs.docker.com/)
- [Minikube Guide](https://minikube.sigs.k8s.io/)

## Licence

Ce projet est libre d'utilisation à des fins éducatives et professionnelles.

---

Développé par : BambaSatoru

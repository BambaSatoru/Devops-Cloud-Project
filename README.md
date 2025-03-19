# API Flask avec MySQL sur Kubernetes

Ce projet propose une API REST simple en Flask, connectée à une base de données MySQL, déployée sur Kubernetes. L'API permet de créer et de récupérer des utilisateurs à partir de la base de données.

## Prérequis

- Docker
- Kubernetes (Minikube pour le développement local)
- kubectl (outil en ligne de commande Kubernetes)
- MySQL

## Structure du Projet

- `app.py`: Application Flask avec deux endpoints (`GET /users` et `POST /users`).
- `Dockerfile`: Dockerfile pour construire l'image de l'API Flask.
- `requirements.txt`: Dépendances Python pour l'API Flask.
- `mysql-deployment.yaml`: Configuration Kubernetes pour le déploiement de MySQL.
- `flask-api-deployment.yaml`: Configuration Kubernetes pour le déploiement de l'API Flask.

## Déploiement
docker build -t <docker-username>/flask-api:latest .
docker login
docker push <docker-username>/flask-api:latest
minikube start
kubectl apply -f init-job.yaml
kubectl apply -f mysql-deployment.yaml
kubectl apply -f flask-api-deployment.yaml
kubectl get jobs
kubectl get pods
kubectl get svc






# CloudAPI - Cloud-Native Infrastructure with Kubernetes

A complete REST application demonstrating DevOps best practices and cloud orchestration. This project integrates a Flask API, a MySQL database, and Kubernetes deployment, illustrating a modern and scalable microservices architecture.

## Project Objective

This project showcases a complete technology stack for:
- Developing a secure and performant REST API
- Containerizing applications with Docker
- Orchestrating services with Kubernetes
- Implementing Infrastructure-as-Code (IaC)
- Demonstrating DevOps best practices

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

## Prerequisites

- Docker (≥ 20.0)
- Kubernetes (Minikube for local development)
- kubectl (Kubernetes CLI tool)
- Python 3.8+
- MySQL 8.0+

## Project Structure

```
.
├── app.py                      # Flask application (REST endpoints)
├── requirements.txt            # Python dependencies
├── Dockerfile                  # Docker image for the API
├── init-job.yaml              # Kubernetes Job to initialize DB
├── mysql-deployment.yaml      # MySQL deployment
├── flask-api-deployment.yaml  # Flask API deployment
└── README.md
```

## Technical Details

### Flask API
- Framework: Flask
- Database: MySQL 8.0
- Endpoints:
  - GET /users - Retrieves the list of users
  - POST /users - Creates a new user

### Docker and Kubernetes
- Containerization with Docker for portability
- Orchestrated deployment via Kubernetes
- Secret and configuration management via ConfigMaps
- Data persistence with Persistent Volumes

## Deployment

### 1. Prepare the Docker Image

```bash
docker build -t <docker-username>/flask-api:latest .
docker login
docker push <docker-username>/flask-api:latest
```

### 2. Start Kubernetes

```bash
minikube start
```

### 3. Deploy the Infrastructure

```bash
# Initialize the database
kubectl apply -f init-job.yaml

# Deploy MySQL
kubectl apply -f mysql-deployment.yaml

# Deploy Flask API
kubectl apply -f flask-api-deployment.yaml
```

### 4. Verify the Deployment

```bash
# View jobs
kubectl get jobs

# View pods
kubectl get pods

# View services
kubectl get svc

# Check logs
kubectl logs -f deployment/flask-api
```

### 5. Access the API

```bash
# Port-forward to the API
kubectl port-forward svc/flask-api-service 5000:5000

# Test the endpoints
curl http://localhost:5000/users
curl -X POST http://localhost:5000/users -H "Content-Type: application/json" -d '{"name":"John"}'
```

## Project Composition

- Python: 89.6% (application logic)
- Dockerfile: 10.4% (container configuration)

## DevOps Concepts Demonstrated

Containerization - Docker and optimized images
Orchestration - Kubernetes deployments
Infrastructure as Code - YAML manifests
Scalability - Configurable pod replicas
Data Persistence - Data management in Kubernetes
Monitoring - Service health verification

## Useful Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Flask Documentation](https://flask.palletsprojects.com/)
- [Docker Documentation](https://docs.docker.com/)
- [Minikube Guide](https://minikube.sigs.k8s.io/)

## License

This project is free to use for educational and professional purposes.

---

Developed by: BambaSatoru

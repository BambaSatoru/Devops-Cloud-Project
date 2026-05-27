# Contributing to CloudAPI

Thank you for your interest in contributing to CloudAPI! This document provides guidelines and instructions for contributing to this project.

## Code of Conduct

Be respectful and professional in all interactions with other contributors and maintainers.

## How to Contribute

### Reporting Bugs

When reporting a bug, please include:
- A clear and descriptive title
- A detailed description of the issue
- Steps to reproduce the problem
- Expected behavior
- Actual behavior
- Your environment (Python version, OS, Docker version, Kubernetes version)

### Suggesting Enhancements

Enhancement suggestions should include:
- A clear and descriptive title
- A detailed description of the enhancement
- Use cases and benefits
- Possible implementation approaches

### Pull Requests

1. Fork the repository
2. Create a new branch for your feature or fix: `git checkout -b feature/your-feature-name`
3. Make your changes and commit them with clear messages
4. Push to your fork: `git push origin feature/your-feature-name`
5. Submit a pull request with a clear description of your changes

## Development Setup

### Prerequisites
- Python 3.8+
- Docker 20.0+
- Kubernetes (Minikube)
- kubectl

### Local Development

1. Clone the repository:
```bash
git clone https://github.com/BambaSatoru/Devops-Cloud-Project.git
cd Devops-Cloud-Project
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run the Flask app locally:
```bash
python app.py
```

### Docker Development

1. Build the Docker image:
```bash
docker build -t cloudapi:dev .
```

2. Run the container:
```bash
docker run -p 5000:5000 cloudapi:dev
```

### Kubernetes Testing

1. Start Minikube:
```bash
minikube start
```

2. Deploy the infrastructure:
```bash
kubectl apply -f init-job.yaml
kubectl apply -f mysql-deployment.yaml
kubectl apply -f flask-api-deployment.yaml
```

3. Verify deployment:
```bash
kubectl get pods
kubectl logs -f deployment/flask-api
```

## Commit Message Guidelines

- Use clear and descriptive commit messages
- Start with a verb (Add, Fix, Update, Remove, etc.)
- Example: "Add user authentication endpoint"

## Code Standards

- Follow PEP 8 style guide for Python code
- Write clear and concise comments
- Keep functions focused and modular
- Add docstrings for classes and functions

## Testing

Ensure your changes do not break existing functionality. Test locally before submitting a pull request.

## License

By contributing to this project, you agree that your contributions will be licensed under the MIT License.

---

For questions, please open an issue or contact the maintainers.

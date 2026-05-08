# Portfolio - Cloud-Native CI/CD Deployment

A simple portfolio website deployed using a full CI/CD pipeline with Docker, Jenkins, and Kubernetes.

## Tech Stack

- **Web Server:** Nginx (Alpine)
- **Containerisation:** Docker
- **Orchestration:** Kubernetes (Minikube)
- **CI/CD:** Jenkins (Pipeline as Code)
- **Version Control:** Git / GitHub

## Project Structure

```
.
├── index.html          # Portfolio website
├── style.css           # Stylesheet
├── nginx.conf          # Nginx configuration (port 8081)
├── Dockerfile          # Docker image definition
├── Jenkinsfile         # Jenkins pipeline definition
├── k8s/
│   ├── deployment.yaml # Kubernetes Deployment (2 replicas)
│   └── service.yaml    # Kubernetes Service (NodePort)
├── .gitignore
└── README.md
```

## Setup Instructions

### Prerequisites

- Docker installed
- Minikube installed and running
- kubectl configured
- Jenkins installed with Docker and Kubernetes plugins

### 1. Clone the Repository

```bash
git clone https://github.com/GITHUB_USERNAME/portfolio.git
cd portfolio
```

### 2. Build and Run with Docker

```bash
docker build -t portfolio:latest .
docker run -d -p 8081:8081 portfolio:latest
```

Access the application at `http://localhost:8081`

### 3. Deploy to Kubernetes

```bash
minikube start
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
kubectl get pods
kubectl get services
```

Access via: `minikube service portfolio-service`

### 4. Jenkins Pipeline

1. Create a new Pipeline job in Jenkins
2. Point it to this repository
3. Jenkins will use the `Jenkinsfile` to run the pipeline stages:
   - Code Pull
   - Build Docker Image
   - Push Image to Docker Hub
   - Deploy to Kubernetes

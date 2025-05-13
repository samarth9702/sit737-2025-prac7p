

# 🧮 Updated Calculator Microservice

This project is a basic calculator microservice built using **Node.js** and **Express**. It supports **addition**, **subtraction**, **multiplication**, and **division** through REST API endpoints. It also includes **logging** using the Winston library and a **simple web UI**.

---

## 🛠️ Features

- REST API for basic arithmetic operations
- Input validation and error handling
- Logging with Winston (console and file logs)
- Minimal web UI for testing operations

---

## 📁 Project Structure
```
├── logs/ │ 
├── combined.log │
    └── error.log 
├── public/ │ 
    └── index.html 
├── docker-compose.yml
├── Dockerfile 
├── deployment.yaml
├── service.yaml
├── logger.js 
├── server.js 
├── package.json 
└── README.md
```

2. Install Dependencies by using - "npm install"

3. Run the Microservice by using - "node server.js"

4. Access it via: http://localhost:3003


# 🐳 Dockerizing the Application
## 🔧 Prerequisites
- Git (https://github.com)
- Visual Studio code (https://code.visualstudio.com/)
- Node.js (https://nodejs.org/en/download/)
- Docker (https://app.docker.com/)
- Kubernetes (computing platform to host your microservice)
- Kubectl (the command-line tool for interacting with Kubernetes cluster)


# 📦 Steps to Dockerize and Run the App
## 1. Clone the repository
```
git clone https://github.com/samarth9702/sit737-2025-prac6c.git

cd sit737-2025-prac6p
```

## 2. Build the Docker image
```
docker build -t sit737-prac6p-app .
```

## 3. Start using Docker Compose
```
docker-compose up
```
Now go to: http://localhost:3003

# ❤️ Docker Health Check + Auto Restart
This app includes a Docker health check and restart: always policy via docker-compose.yml:

```
healthcheck:
  test: ["CMD", "curl", "-f", "http://localhost:3003"]
  interval: 30s
  timeout: 10s
  retries: 3
restart: always
```
This ensures the container is monitored and will restart automatically if it becomes unhealthy.

# 🚀 Push to Docker Hub

## 1. Tag the image
```
docker tag calculator-app your_dockerhub_username/sit737-6p
```
## 2. Login and push
```
docker login
docker push your_dockerhub_username/sit737-6p
```

# ☸️ Kubernetes Deployment & Interaction
## 1️⃣ Apply Deployment and Service
``` 
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml 
```
## 2️⃣ Check Pod and Service
```
kubectl get pods
kubectl get services
```
# 🔄 Update the Application
1. Modify source code (for example, I have updated title in index.html)
2. Build new Docker image with a new version:

```
docker build -t samarth502/task6c:v2 .
docker push samarth502/task6c:v2
```
3. Update Kubernetes deployment image:


```
kubectl set image deployment/calculator-deployment calculator=samarth502/task6p:v2
```
4. Verify update:
```
kubectl rollout status deployment calculator-deployment
```
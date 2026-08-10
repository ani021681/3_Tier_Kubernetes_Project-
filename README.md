# ☸️ 3-Tier Web Application on Kubernetes

A 3-tier web application deployed on Kubernetes using **Minikube, Docker, and kubectl**. The project demonstrates a Frontend, Backend API, and MongoDB Database tier with Kubernetes Deployments, Services, ConfigMaps, Secrets, and persistent storage.

## 🏗️ Architecture

```text
User
  |
  v
Frontend
(Nginx / NodePort)
  |
  v
Backend API
(ClusterIP)
  |
  v
MongoDB
(ClusterIP + PV/PVC)
```

## 🛠️ Technologies

- Kubernetes
- Minikube
- Docker
- kubectl
- Nginx
- Node.js
- MongoDB

## ☸️ Kubernetes Components

- Pods
- Deployments
- Services
- ConfigMaps
- Secrets
- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)
- ReplicaSets

## 🚀 Deployment

### 1. Start Minikube

```bash
minikube start --driver=docker
kubectl get nodes
```

### 2. Deploy Database

```bash
kubectl apply -f kubernetes/database/
kubectl get deployment,pod,svc -l app=mongo
```

### 3. Deploy Backend

```bash
kubectl apply -f kubernetes/backend/
kubectl get deployment,pod,svc -l app=backend
```

### 4. Deploy Frontend

```bash
kubectl apply -f kubernetes/frontend/
kubectl get deployment,pod,svc -l app=frontend
```

### 5. Access Application

```bash
minikube service frontend-service --url
```

Open the displayed URL in a browser.

## 📈 Scaling & Self-Healing

Scale the backend:

```bash
kubectl scale deployment backend-deployment --replicas=4
kubectl get pods -l app=backend
```

Test self-healing:

```bash
kubectl get pods -l app=backend
kubectl delete pod <BACKEND_POD_NAME>
kubectl get pods -l app=backend
```

Kubernetes should create a replacement Pod to maintain the desired replica count.

## 📂 Project Structure

```text
3-Tier-Kubernetes-Application/
├── README.md
├── kubernetes/
│   ├── database/
│   ├── backend/
│   └── frontend/
└── documentation/
    └── 3-Tier-Kubernetes-Project-Guide.pdf
```

## 📌 Key Learning

- Deploying a multi-tier application on Kubernetes
- Kubernetes Pods, Deployments, and Services
- ConfigMaps and Secrets
- Persistent storage using PV/PVC
- Internal service communication
- Pod self-healing
- Application scaling

## 👨‍💻 Author

**Aniruddh Jadhav**

GitHub: https://github.com/ani021681  
LinkedIn: https://linkedin.com/in/aniruddh-jadhav-0327b4302

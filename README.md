# 🧭 Microservices Full Stack App (Minikube + Docker + Kubernetes)

This project is a full-stack microservices application featuring:

- 🔐 **User Authentication** (Login, Signup, Forgot Password)
- 🌐 **Frontend** built with React
- ⚙️ **Backend API** built with Node.js + Express
- 🗃️ **MongoDB** for data storage
- 📦 **Dockerized** services
- ☸️ **Kubernetes Deployment** on Minikube (with 3 replicas per service)

---

## 🧰 Tech Stack

- **Frontend:** React
- **Backend:** Node.js + Express
- **Database:** MongoDB
- **Auth:** Bcrypt-based (no JWT)
- **Containerization:** Docker
- **Orchestration:** Kubernetes (Minikube)

---

## 🗂️ Project Structure
```bash
Microservices-app/
├── backend/ # Backend service
├── frontend/ # Frontend React app
├── k8s/ # Kubernetes YAML files
├── docker-compose.yml # (For local development only)
└── README.md
```

---

## Run the App on Minikube (Production Setup)

#### 1. Start Minikube

```bash
minikube start
```

#### 2. Connect to Minikube's Docker Daemon
``` bash
Invoke-Expression -Command (minikube docker-env | Out-String)   // Powershell
FOR /f "tokens=*" %i IN ('minikube docker-env') DO @%i          // CMD (WINDOWS)
```

####  3. Build Docker Images Inside Minikube
```bash
docker build -t backend ./backend
docker build -t frontend ./frontend
```

#### 4. Apply Kubernetes Configurations
``` bash
kubectl apply -f k8s/
```

#### 5. Check Pod Status
``` bash
kubectl get pods OR kubectl get pods -A
```

#### 6. Access the Frontend in Browser
```bash
minikube service frontend-service
```

#### Without MiniKube:
```bash
docker-compose up --build
```
App will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

### Clean-Up:
```bash
kubectl delete -f k8s/
minikube stop
```


# 🚀 Kubernetes Fullstack App

This project demonstrates a fullstack application deployed on **Kubernetes**, including:
- React frontend (served using Nginx)
- Node.js backend (REST API)
- PostgreSQL database
- Kubernetes Ingress
- ConfigMap and Secrets for secure configuration

---

## 🧱 Project Architecture

```plaintext
User --> Ingress --> Frontend (Nginx) --> Backend (Node.js) --> PostgreSQL (with PVC)


## 📁 Project Structure

```
k8s-fullstack-app/
├── frontend/
│   ├── Dockerfile
│   └── k8s/
├── backend/
│   ├── Dockerfile
│   └── k8s/
├── database/
│   └── k8s/
├── config/
│   ├── configmap.yaml
│   └── secret.yaml
├── ingress/
│   └── ingress.yaml
├── images/
│   └── A_diagram_depicts_the_architecture_of_a_full-stack.png
└── README.md
```

---

## 🛠️ Technologies Used

- Kubernetes (Minikube / k3s / kind / cloud)
- Docker
- React + Nginx
- Node.js (Express)
- PostgreSQL (13)
- YAML (K8s manifests)
- ConfigMap / Secret / PVC / Ingress

---

## 🧪 Setup Instructions

### 📦 1. Build and Push Docker Images

Make sure you're logged into DockerHub:

```bash
docker login
```

### Frontend:
```bash
cd frontend/
docker build -t frontend:latest .
docker tag frontend:latest minamorcos187/frontend:latest
docker push minamorcos187/frontend:latest
```

### Backend:
```bash
cd backend/
docker build -t backend:latest .
docker tag backend:latest minamorcos187/backend:latest
docker push minamorcos187/backend:latest
```

---

### ⚙️ 2. Apply Kubernetes Manifests

Apply all manifests in correct order:

```bash
kubectl apply -f config/
kubectl apply -f database/k8s/
kubectl apply -f backend/k8s/
kubectl apply -f frontend/k8s/
kubectl apply -f ingress/
```

---

### 🧩 3. Update Your Hosts File

Edit your local `/etc/hosts` file and add this line:

```
127.0.0.1   app.local
```

> This allows you to access the app in your browser via `http://app.local`.

---

## 🔐 Configuration Details

### ConfigMap (`config/configmap.yaml`)
Stores environment variables like app port.

### Secret (`config/secret.yaml`)
Stores database username/password securely.

### PVC (`database/k8s/pvc.yaml`)
Persistent storage for PostgreSQL.

---

## ✅ Expected Output

After deployment, you should be able to:
- Open the frontend at `http://app.local`
- Interact with the backend API (e.g., create or list items)
- Data should be stored in PostgreSQL persistently

---

## 🧰 Useful Commands

```bash
kubectl get pods
kubectl get services
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

---

## 🧠 Troubleshooting

- ❌ Frontend doesn't load? → Check `kubectl get ingress`, verify hosts and IPs.
- ❌ API errors? → Check backend logs with `kubectl logs`.
- ❌ Database not connecting? → Check Secret values and Service names.

---

## 📬 Author

**Mina Morcos** – [DockerHub: minamorcos187](https://hub.docker.com/u/minamorcos187)  
Feel free to fork, clone, or improve this project.

---

## 📜 License

This project is licensed under the MIT License.

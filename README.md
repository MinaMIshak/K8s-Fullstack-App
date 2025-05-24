# Kubernetes Fullstack App

This project demonstrates a fullstack application running on Kubernetes with:
- React frontend (served by Nginx)
- Node.js backend
- PostgreSQL database
- Ingress controller for routing
- ConfigMap and Secrets for configuration management

## Structure
- `frontend`: Static files served by Nginx
- `backend`: REST API connected to PostgreSQL
- `database`: PostgreSQL with persistent volume
- `ingress`: Ingress setup
- `config`: Secrets and config map

## Deploy Instructions
1. Build and push Docker images for frontend and backend.
2. Apply all Kubernetes manifests:
```
kubectl apply -f config/
kubectl apply -f database/k8s/
kubectl apply -f backend/k8s/
kubectl apply -f frontend/k8s/
kubectl apply -f ingress/
```
3. Add `app.local` to `/etc/hosts` pointing to your cluster IP.
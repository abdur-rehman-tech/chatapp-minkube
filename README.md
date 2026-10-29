# 💬 Real-Time Chat App on Kubernetes (Minikube)

![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=white) ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)

A full-stack real-time chat app (React + Node.js + MongoDB) **containerized and deployed on Kubernetes** with Minikube, including persistent storage and Ingress.

> Application code is based on [iemafzalhassan/full-stack_chatApp](https://github.com/iemafzalhassan/full-stack_chatApp). My work here is the Kubernetes deployment.

## ☸️ Kubernetes architecture (`k8s/`)

```
            Ingress (chat-tws.com)
           /                      \
  frontend Service           backend Service
        │                          │
 frontend Deployment       backend Deployment ──► MongoDB Service
                                                    │
                                          MongoDB Deployment
                                                    │
                                            PVC (5Gi) → PV
```

| File | Resource |
|---|---|
| `frontend-deployment.yml` / `frontend-service.yml` | React frontend |
| `backend-deployment.yml` / `backend-service.yml` | Node.js API |
| `mongodb-deployment.yml` / `mongodb-service.yml` | MongoDB |
| `mongodb-pv.yml` / `mongodb-pvc.yml` | 5Gi persistent storage |
| `ingress.yml` | Host-based routing |
| `secert.yml` | App secrets |

## 🚀 Deploy on Minikube

```bash
minikube start
minikube addons enable ingress
kubectl apply -f k8s/
kubectl get pods,svc,ingress

# map the host locally
echo "$(minikube ip) chat-tws.com" | sudo tee -a /etc/hosts
```

## 🐳 Run with Docker Compose

```bash
docker compose up -d
```

---

## 👤 Author

**Abdur Rehman** · DevSecOps Engineer · Founder of [ARTechOps](https://artechops.com)

[LinkedIn](https://www.linkedin.com/in/muhamad-abdur-rehman-81777b366/) · [GitHub](https://github.com/abdur-rehman-tech) · [artechops.com](https://artechops.com)

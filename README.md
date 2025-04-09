# 🚀 Kubernetes Host-Based Routing with NGINX Ingress & GoDaddy DNS

This guide demonstrates how to deploy two applications (`nginx` and `httpd`) on a Kubernetes cluster using host-based routing with NGINX Ingress. DNS is configured via GoDaddy.

---

## 🌐 Domain Setup

- **Domain:** `praveens.online`
- **Subdomains:**
  - `www.praveens.online` → Routes to `nginx` app
  - `httpd.praveens.online` → Routes to `httpd` app

---

## 🧰 Prerequisites

- Kubernetes Cluster (EKS, Minikube, etc.)
- `kubectl` installed and configured
- Domain purchased and managed in GoDaddy
- Two deployed services: `nginx` and `httpd`

---

## 🛠️ Setup Steps

### 1️⃣ Install NGINX Ingress Controller

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.6/deploy/static/provider/cloud/deploy.yaml

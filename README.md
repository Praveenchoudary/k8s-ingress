# 🚀 Kubernetes Host-Based Routing with NGINX Ingress & GoDaddy DNS

This guide walks you through deploying two applications (`nginx` and `httpd`) on Kubernetes using **host-based routing** via NGINX Ingress. It also includes DNS setup via **GoDaddy** to route external traffic to your apps.

---

## 🌐 Domain Setup

- **Domain Name:** `praveens.online`
- **Subdomains Used:**
  - `www.praveens.online` → Routes to `nginx`
  - `httpd.praveens.online` → Routes to `httpd`

---

## 🧰 Prerequisites

- A Kubernetes cluster (Minikube, EKS, etc.)
- `kubectl` configured
- Domain purchased on GoDaddy
- Two containerized applications: `nginx` and `httpd`

---

## 🛠️ Setup Instructions

### 1️⃣ Install NGINX Ingress Controller

Apply the official manifest:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.6/deploy/static/provider/cloud/deploy.yaml


`✅ Check the status of the ingress controller:

kubectl get pods -n ingress-nginx

🌐 Get the External IP of the ingress controller:

kubectl get svc -n ingress-nginx

    Note the EXTERNAL-IP of the ingress-nginx-controller service (type: LoadBalancer).
    You’ll use this IP in GoDaddy DNS settings.

2️⃣ Configure A Records in GoDaddy DNS
Follow these steps:

    Go to https://godaddy.com and log in.

    Under My Products, select your domain: praveens.online.

    Click DNS to manage records.

    Click Add Record and enter:

Host	Type	Points to (Ingress EXTERNAL-IP)	TTL
@	A	<Ingress EXTERNAL-IP>	600
httpd	A	<Ingress EXTERNAL-IP>	600

    @ points to the root domain (www.praveens.online)

    httpd creates the subdomain (httpd.praveens.online)

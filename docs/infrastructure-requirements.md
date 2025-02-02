# Infrastructure Requirements for Development Environment

## 📌 Overview
This document outlines the minimum and recommended system requirements for running the development infrastructure of the SaaS platform using Docker containers on a **Linux-based environment**.

## 🖥️ System Requirements
### **Minimum Requirements**
- **Operating System:** Ubuntu 22.04+ / Debian 11+ / Fedora 37+
- **CPU:** 4 vCPUs
- **RAM:** 8GB
- **Disk Space:** 50GB free storage
- **Networking:** Internet access for pulling container images
- **Additional:** User must have `sudo` privileges for Docker setup

### **Recommended Requirements**
- **Operating System:** Ubuntu 24.04+ / Debian 12+ / Fedora 38+
- **CPU:** 8 vCPUs or higher
- **RAM:** 16GB or higher (especially if running multiple services concurrently)
- **Disk Space:** 100GB+ free storage (to accommodate database and logs growth)
- **Networking:** Stable broadband connection
- **Additional:** SSD storage for better performance

## 🛠️ Required Software
### **Mandatory Software**
- **Docker Engine (latest stable version)**
- **Docker Compose**
- **Git (latest stable version)**
- **Java JDK 21+ (if developing Java microservices)**
- **Node.js 18+ (if developing frontend or API services in JavaScript/TypeScript)**

### **Optional Tools**
- **Portainer** (UI for managing Docker containers)
- **Lazydocker** (Terminal-based Docker UI)
- **DBeaver** (Database management tool for PostgreSQL, MongoDB, etc.)
- **Postman** (API testing tool)

## 📦 Containers & Services
The following services are included in the `docker-compose.yml` for local development:

| Service     | Description                                | Ports |
|------------|--------------------------------|-------|
| PostgreSQL | Main relational database       | 5432  |
| Redis      | Caching service                | 6379  |
| MongoDB    | NoSQL document database       | 27017 |
| RabbitMQ   | Message broker                 | 5672 (AMQP), 15672 (UI) |
| Keycloak   | Identity & Access Management  | 8080  |

## 🚀 Setup & Installation
### **1️⃣ Install Required Software**
```bash
sudo apt update && sudo apt install -y docker.io docker-compose git
```
Ensure Docker is running:
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

### **2️⃣ Clone the Repository**
```bash
git clone https://github.com/YOUR-REPO/saas-platform.git
cd saas-platform/infra
```

### **3️⃣ Start Infrastructure Services**
```bash
docker compose up -d
```

### **4️⃣ Verify Running Containers**
```bash
docker ps
```

## 🔍 Troubleshooting
- If Docker commands fail due to permissions:
```bash
sudo usermod -aG docker $USER
newgrp docker
```
- If any service fails to start, check logs:
```bash
docker logs <container_name>
```

## 📌 Notes
- This setup is for **local development only**.
- For production, consider **Kubernetes (K8s) or cloud-managed services**.
- Ensure **firewall rules** allow required ports if accessing services externally.

---
**Author:** DevOps Team  
**Last Updated:** February 2025


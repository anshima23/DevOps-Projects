# 🚀 Cloud-Native Food-Tech Stack: End-to-End DevSecOps Pipeline

This project demonstrates a high-scale, **Cloud-Native Food-Tech Application** (Zomato Clone) deployed on **Kubernetes** using a robust **DevSecOps** framework. It automates everything from code quality analysis to security vulnerability scanning and multi-stage deployment.

---

## 🏗️ Architecture Overview
The pipeline ensures that every code commit undergoes rigorous quality and security checks before reaching the production environment.

* **Frontend:** React.js (Node 16 based)
* **CI/CD:** Jenkins (Pipeline-as-Code)
* **Security (Shift-Left):** SonarQube, OWASP Dependency-Check, Trivy, and Docker Scout.
* **Orchestration:** Kubernetes (EKS/Self-managed)
* **Monitoring:** Prometheus Node Exporter integration.

---

## 🛠️ Tech Stack & Integration

| Category | Tools | Purpose |
| :--- | :--- | :--- |
| **CI/CD** | Jenkins | Pipeline Orchestration |
| **SAST** | SonarQube | Code Quality & Static Analysis |
| **SCA** | OWASP & Trivy | File System & Dependency Vulnerability |
| **Container** | Docker | Application Containerization |
| **Image Security**| Docker Scout | Real-time Image CVE Analysis |
| **Orchestration** | Kubernetes | High Availability & Scaling |
| **Monitoring** | Prometheus | Infrastructure Health Metrics |
| **Notification** | Email-ext | Automated Build Reports |

---

## 📂 Repository Structure

```text
Cloud-Native-Food-Tech-Stack/
├── Kubernetes/             # Declarative K8s Manifests
│   ├── deployment.yaml      # App Deployment (2 Replicas)
│   ├── service.yaml         # Internal Cluster Service
│   └── node-service.yaml    # NodePort Service for Node Exporter
├── src/                     # React.js Source Files
│   ├── components/          # Modular UI Components
│   └── data.js              # Application Mock Data (Cuisines, Chains)
├── Dockerfile               # Multi-stage Docker Build Blueprint
├── jenkinsfile              # Comprehensive DevSecOps Pipeline
└── package.json             # Node.js Dependencies & Scripts


#🛡️ DevSecOps Pipeline Stages

Code Analysis: Automated scans via SonarQube to ensure the code meets industry standards.

Security Gate: OWASP Dependency-Check identifies vulnerable libraries in the package.json.

Vulnerability Scanning: Trivy performs a deep scan of the filesystem and the final Docker image.

Image Analysis: Docker Scout provides a quickview of CVEs and offers remediation recommendations.

Automated Deployment:
Staging: Deploying as a Docker container for testing.
Production: Orchestrating pods on Kubernetes with 2 replicas for load balancing.

Post-Build: Automated Email notifications with trivy.txt vulnerability reports attached.

#🚀 Getting Started

Prerequisites

Jenkins with Docker, SonarQube, and OWASP plugins.
Kubernetes Cluster (Minikube/EKS/K3s).
Docker Hub account for image registry.

Local Setup

Clone the Repo:
Bash
git clone https://github.com/anshima23/DevOps-Projects.git
cd Cloud-Native-Food-Tech-Stack

Build & Run with Docker:
Bash
docker build -t food-tech-app .
docker run -p 3000:3000 food-tech-app

Apply K8s Manifests:
Bash
kubectl apply -f Kubernetes/deployment.yaml
kubectl apply -f Kubernetes/service.yaml


#📊 Monitoring Strategy
The project integrates Prometheus Node Exporter via node-service.yaml on port 9100. This allows the DevOps team to monitor hardware and OS metrics of the K8s nodes in real-time.

#🤝 ConnectivityIf you found this project helpful, let's connect!LinkedIn: [Your Profile Link Here]Portfolio: [Your Portfolio Link Here]
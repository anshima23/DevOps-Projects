# 🚀 Cloud-Native Food-Tech Stack: End-to-End DevSecOps Pipeline

This project demonstrates a high-scale, **Cloud-Native Food-Tech Application** (Zomato Clone) deployed on **Kubernetes** using a robust **DevSecOps** framework. It automates everything from code quality analysis to security vulnerability scanning and multi-stage deployment.

---

# 📂 Repository Structure

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

```

## 🏗️ Architecture Overview
The pipeline ensures that every code commit undergoes rigorous quality and security checks before reaching the production environment.

* **Frontend:** React.js (Node 16 based)
* **CI/CD:** Jenkins (Pipeline-as-Code)
* **Security (Shift-Left):** SonarQube, OWASP Dependency-Check, Trivy, and Docker Scout.
* **Orchestration:** Kubernetes (EKS/Self-managed)
* **Monitoring:** Prometheus Node Exporter integration.

---

## 🗺️ Architecture & Pipeline Flow

```text
       +-----------+       +----------------+       +-------------------+
       | Developer | ----> |  GitHub Repo   | ----> |   Jenkins Server  |
       | (Pushes)  |       | (Source Code)  |       |   (On AWS EC2)    |
       +-----------+       +----------------+       +---------+---------+
                                                              |
                                                              v
       +------------------------------------------------------+---------------------------------------+
       |                                Jenkins Pipeline Stages                                       |
       +------------+------------+------------+------------+------------+------------+------------+
       |  SonarQube | OWASP Scan | NPM Build  | Trivy Scan | Docker     | Docker     | K8s        |
       |  (SAST)    | (SCA)      | & Install  | (FS Scan)  | Build/Push | Scout Scan | Deploy     |
       +------------+------------+------------+------------+------------+------------+------------+
                                                              |
                                                              v
       +-----------------------+                    +---------+---------+
       |   Prometheus Metrics  | <----------------- | Kubernetes Cluster|
       |   (Node Exporter)     |                    | (Self-Managed/EKS)|
       +-----------------------+                    +-------------------+

```

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


## 🛡️ DevSecOps Pipeline Stages

* **Code Analysis:** Automated scans via **SonarQube** to ensure the code meets industry standards.
* **Security Gate:** **OWASP Dependency-Check** identifies vulnerable libraries in the `package.json`.
* **Vulnerability Scanning:** **Trivy** performs a deep scan of the filesystem and the final Docker image.
* **Image Analysis:** **Docker Scout** provides a quickview of CVEs and offers remediation recommendations.
* **Automated Deployment:**
    * **Staging:** Deploying as a Docker container for immediate testing.
    * **Production:** Orchestrating pods on **Kubernetes** with 2 replicas for high availability and load balancing.
* **Post-Build:** Automated Email notifications with `trivy.txt` vulnerability reports attached for transparency.

---

## 🚀 Getting Started

### **Prerequisites**
* Jenkins installed with Docker, SonarQube, and OWASP plugins.
* Access to a Kubernetes Cluster (Minikube, EKS, or K3s).
* Docker Hub account for image hosting.

### **Local Setup**

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/anshima23/DevOps-Projects.git](https://github.com/anshima23/DevOps-Projects.git)
   cd Cloud-Native-Food-Tech-Stack
   ```


2. **Build & Run with Docker:**
    ```bash
    docker build -t food-tech-app .
    docker run -p 3000:3000 food-tech-app
    ```

3. **Apply K8s Manifests:**
   ```bash
   kubectl apply -f Kubernetes/deployment.yaml
   kubectl apply -f Kubernetes/service.yaml
   ```

  --- 

 ## 🛡️ DevSecOps Approach: Shift-Left Security
In this project, security is not an afterthought but integrated at every stage:
* **Pre-Build:** Trivy scans the file system for vulnerabilities in dependencies.
* **During Build:** OWASP Dependency-Check analyzes the `package.json` for known CVEs.
* **Post-Build:** Docker Scout performs real-time analysis on the container image before deployment to production.

---

## 🌐 Port Configuration & Access

Kubernetes cluster ke andar networking aur access points ko samajhne ke liye niche di gayi table ka use karein:

| Service | Port | Access Type | Purpose |
| :--- | :--- | :--- | :--- |
| **Application (Frontend)** | 3000 | Container Port | Main Web UI |
| **Node Exporter** | 9100 | NodePort / Monitoring | Infrastructure Metrics |
| **SonarQube** | 9000 | External Tool | Static Code Analysis |
| **Jenkins** | 8080 | CI Engine | Pipeline Orchestration |

---

## 📊 Monitoring Strategy
The project integrates Prometheus Node Exporter via node-service.yaml on port 9100. This allows the DevOps team to monitor hardware and OS metrics of the K8s nodes in real-time.

---

## 🤝 Connectivity
If you found this project helpful, let's connect!LinkedIn: [Your Profile Link Here]Portfolio: [Your Portfolio Link Here]
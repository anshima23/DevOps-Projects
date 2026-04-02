### 🚀 Cloud-Native E-Commerce Microservices: End-to-End DevSecOps on AWS EKS
This project represents a high-scale E-Commerce Microservices Application deployed on Amazon EKS. It features a fully automated CI/CD Pipeline using Jenkins, infrastructure management via Terraform (IaC), and secure container hosting on Amazon ECR.

---

## 📂 Repository Structure
```Plaintext
Microservices-E-Commerce-eks-project/
├── ecr-terraform/           # Infrastructure for Container Registry
│   ├── backend.tf           # Remote State configuration for ECR
│   ├── ecr-jenkinfile       # Pipeline to automate ECR provisioning
│   └── ecr-repo-main.tf     # ECR Repository definitions
├── eks-terraform/           # Core Kubernetes Cluster Infrastructure
│   ├── backend.tf           # Remote State configuration for EKS
│   ├── eks-jenkinsfile      # Pipeline for EKS lifecycle management
│   ├── main.tf              # EKS Cluster, Node Groups & IAM Roles
│   └── variable.tf          # Parameterized cluster configurations
├── jenkinsfiles/            # Service-specific CI/CD Pipelines
│   ├── adservice.jenkinsfile
│   ├── cartservice.jenkinsfile
│   └── [Other microservices jenkinsfiles...]
├── kubernetes-files/        # K8s Manifests (Deployments & Services)
│   ├── adservice.yaml
│   ├── frontend.yaml
│   └── [Other 10+ microservice manifests...]
├── s3-buckets/              # Persistent Storage & State Management
│   ├── main.tf              # S3 Bucket provisioning
│   ├── output.tf            # Bucket ARNs and Names
│   └── variables.tf         # Storage configurations
├── src/                     # Polyglot Application Source Code
│   ├── adservice/
│   ├── frontend/
│   └── [10+ Microservices logic...]
├── terraform_main_ec2/      # Infrastructure for Management Server
│   ├── main.tf              # Provisioning the Jenkins/Jumphost EC2
│   ├── variables.tf         # Instance & Network variables
│   └── output.tf            # Public IP & Instance Metadata
├── .editorconfig            # Code style consistency
└── .gitignore               # Excluded files
```

## 🏗️ Architecture Highlights

1. **Management-Centric Deployment**
The terraform_main_ec2 provisions a secure Jumphost/Jenkins Server. This instance acts as the central control plane for executing Terraform scripts and managing the Kubernetes cluster via kubectl.

2. **Automated Container Registry (ECR)**
The ecr-terraform module automates the creation of private repositories for each microservice, ensuring secure and low-latency image pulls within the AWS ecosystem.

3. **Polyglot CI/CD Pipeline**
With dedicated jenkinsfiles for each service, the project implements a Pipeline-as-Code strategy. It handles:

* **Building Docker images from the src/ directory.**
* **Pushing images to Amazon ECR.**
* **Rolling updates to the EKS Cluster using manifests in kubernetes-files/.**

---

## 🛠️ Tech Stack & Integration

| Category | Tools | Purpose |
| :--- | :--- | :--- |
| **IaC** | **Terraform** | Multi-service Cloud Provisioning & State Management |
| **Orchestration** | **Kubernetes (EKS)** | Container Scheduling, Scaling, and Management |
| **CI/CD** | **Jenkins** | Automated Build & Deployment Pipelines |
| **Registries** | **Amazon ECR** | Private Docker Image Hosting |
| **Compute** | **AWS EC2** | Dedicated Management/Jumphost Server |
| **Storage** | **Amazon S3** | Remote Terraform State & Persistent Data |

---

## 🛡️ Security Implementation

**Identity Integration:**  Configured IAM OIDC Provider to allow Kubernetes ServiceAccounts to interact with AWS S3 and ECR securely.

**State Management:**  Used S3 Backends in Terraform (backend.tf) to ensure infrastructure stat2e is locked and persistent.

**Network Security:**  Only the Frontend is exposed via an AWS Load Balancer, while internal services are secured using ClusterIP.

---

## 🚀 Execution Guide

1. Provision Management Server:
  ```Bash
  cd terraform_main_ec2 && terraform apply
  ```

2. Setup ECR & S3:
  ```Bash 
  cd ecr-terraform && terraform apply
  cd s3-buckets && terraform apply
  ```
3. Deploy EKS Cluster:
  ```Bash
  cd eks-terraform && terraform apply
  ```

4. CI/CD Pipeline:  Configure Jenkins to use the files in the jenkinsfiles/ directory to automate the src/ builds.

## 🤝 Let's Connect

If you have any questions about this architecture or want to discuss DevSecOps, feel free to reach out!

* **LinkedIn:** https://linkedin.com/in/your-profile
* **Portfolio:** https://yourportfolio.com
* **Email:** mailto:your.email@example.com
# Blue-Green Deployment on Amazon EKS using Jenkins CI/CD

## Project Overview

This project demonstrates the implementation of a complete **Blue-Green Deployment Strategy** on **Amazon EKS (EKS)** using a fully automated **CI/CD Pipeline** built with Jenkins.

The primary objective of this project was to automate the software delivery lifecycle from source code checkout to production deployment while ensuring:

- Zero Downtime Deployments
- High Availability
- Faster Release Cycles
- Improved Application Reliability
- Automated Security & Quality Checks

The project integrates multiple DevOps tools and AWS services including Jenkins, SonarQube, Nexus Repository, Docker, Trivy, Terraform, Kubernetes, and Amazon EKS.

---

# Architecture Diagram

<img width="1254" height="1254" alt="Blue-Green_Dep_architecture" src="https://github.com/user-attachments/assets/28c3249e-07c4-470c-b7d9-19e3868bc6a5" />


---

# Blue-Green Deployment Strategy

This project implements a Blue-Green Deployment model to achieve zero downtime deployments.

## Blue Environment

- Current Production Environment
- Serves Live User Traffic
- Stable Application Version

## Green Environment

- Newly Deployed Application Version
- Used for Validation & Testing
- Receives Traffic After Verification

## Deployment Process

1. Current production traffic is served by the Blue Environment.
2. New application version is deployed to the Green Environment.
3. Validation and health checks are performed.
4. Kubernetes Service selector is updated.
5. Traffic is switched from Blue to Green.
6. Users experience zero downtime.
7. If any issue occurs, traffic can instantly be redirected back to Blue.

# Tools & Technologies Used

| Category | Tools |
|-----------|--------|
| Cloud Platform | AWS |
| CI/CD | Jenkins |
| Source Control | Git, GitHub |
| Build Tool | Maven |
| Code Quality | SonarQube |
| Artifact Repository | Nexus Repository |
| Containerization | Docker |
| Container Registry | Docker Hub |
| Security Scanning | Trivy |
| Container Orchestration | Kubernetes |
| Infrastructure as Code | Terraform |
| Cluster Management | kubectl, AWS CLI |

---

---

# Project Implementation

## Step 1: Infrastructure Provisioning

The project began by provisioning the required AWS infrastructure for hosting the CI/CD ecosystem and Kubernetes cluster.

### Resources Created

The following AWS resources were provisioned and configured:

- VPC
- Public & Private Subnets
- Route Tables
- Internet Gateway
- Security Groups
- IAM Roles & Policies
- Amazon EKS Cluster
- Managed Node Groups
- AWS Load Balancer
- EBS Volumes

<img width="1920" height="973" alt="Instances" src="https://github.com/user-attachments/assets/20c95b03-6116-42a2-8e0c-fdbe49baf610" />

<img width="1920" height="973" alt="SGs" src="https://github.com/user-attachments/assets/7ac4115b-7f78-40af-9d3a-579cba9a978b" />

<img width="1920" height="973" alt="Clustter_info" src="https://github.com/user-attachments/assets/65a2b15d-4f97-4656-825d-cfe6135b5e44" />


---

## Step 2: Launching EC2 Instances

Four dedicated EC2 instances were launched to separate responsibilities and simulate a production-like DevOps environment.

### Instances Created

| Instance | Purpose |
|-----------|----------|
| Jenkins | CI/CD Automation |
| SonarQube | Code Quality Analysis |
| Nexus | Artifact Repository |
| Management Server | Terraform, kubectl & AWS CLI |


---

## Step 3: Installing and Configuring DevOps Tools

The Jenkins server was configured with all required tools for building, scanning, and deploying applications.

### Installed Tools

- Jenkins
- Java 21
- Maven
- Docker
- Trivy
- kubectl
- AWS CLI

---

## Step 4: Provisioning Amazon EKS Using Terraform

Terraform was used to provision the Kubernetes infrastructure on AWS.

### Activities Performed

- EKS Cluster Creation
- Node Group Creation
- IAM Role Configuration
- Networking Configuration

<img width="1915" height="1075" alt="terraform_apply_command" src="https://github.com/user-attachments/assets/c9502387-b360-412d-b175-5eb9218f8411" />

---

## Step 5: Configuring Jenkins Pipeline

A Declarative Jenkins Pipeline was created to automate the entire software delivery lifecycle.

### Pipeline Stages

- Git Checkout
- Compile
- Test
- Trivy FS Scan
- SonarQube Analysis
- Quality Gate Validation
- Package
- Nexus Upload
- Docker Build
- Docker Image Scan
- Docker Push
- EKS Deployment


---

## Step 6: Static Code Analysis using SonarQube

SonarQube was integrated into the pipeline to enforce code quality and security standards.

### Screenshot

![SonarQube Dashboard](images/sonarqube-dashboard.png)

---

## Step 7: Artifact Management using Nexus Repository

Build artifacts were automatically published to Nexus Repository.

### Screenshot

![Nexus Repository](images/nexus-dashboard.png)

---

## Step 8: Docker Image Creation and Registry Integration

The application was containerized using Docker and pushed to Docker Hub.

### Screenshot

![Docker Hub Repository](images/dockerhub-repository.png)

---

## Step 9: Kubernetes Deployment on Amazon EKS

Application workloads were deployed to Amazon EKS using Kubernetes manifests.

### Resources Created

- Deployments
- Services
- Service Accounts
- Secrets

### Screenshot

![EKS Cluster](images/eks-cluster.png)

---

## Step 10: Deploying Blue Environment

The Blue environment represented the currently active production version.

### Screenshot

![Blue Deployment](images/blue-deployment.png)

---

## Step 11: Deploying Green Environment

The Green environment hosted the new application version for validation and testing.

### Screenshot

![Green Deployment](images/green-deployment.png)

---

## Step 12: Traffic Switching using Blue-Green Deployment

Traffic was shifted from the Blue environment to the Green environment by updating Kubernetes Service selectors.

This ensured:

- Zero Downtime
- Safe Deployments
- Instant Rollback Capability

### Screenshot

![Traffic Switching](images/traffic-switching.png)

---

## Step 13: Deployment Verification

The deployment was verified by checking:

- Pods
- Services
- Endpoints
- Load Balancer
- Application Accessibility

### Screenshot

![Kubernetes Pods](images/kubernetes-pods.png)

### Screenshot

![Kubernetes Service](images/kubernetes-service.png)

### Screenshot

![AWS Load Balancer](images/load-balancer.png)

---

## Step 14: Application Validation

The application was successfully accessed through the AWS Load Balancer endpoint, confirming successful deployment.

### Screenshot

![Application Login Page](images/application-login.png)

---



```text
GitHub
   │
   ▼
Git Checkout
   │
   ▼
Compile
   │
   ▼
Unit Test
   │
   ▼
Trivy File System Scan
   │
   ▼
SonarQube Analysis
   │
   ▼
Quality Gate Validation
   │
   ▼
Package Build
   │
   ▼
Publish Artifact to Nexus
   │
   ▼
Docker Build
   │
   ▼
Trivy Image Scan
   │
   ▼
Docker Push
   │
   ▼
Deploy to Amazon EKS
   │
   ▼
Blue-Green Deployment
   │
   ▼
Traffic Switching
   │
   ▼
Deployment Verification
```

---


### Benefits

- Zero Downtime Releases
- Instant Rollback
- Safer Deployments
- Reduced Production Risk

---

# Security & Quality Implementation

## SonarQube

Implemented:

- Static Code Analysis
- Vulnerability Detection
- Code Quality Validation
- Quality Gate Enforcement

## Trivy

Implemented:

### File System Scan

Scans:

- Source Code
- Dependencies
- Configuration Files

### Docker Image Scan

Scans:

- Container Images
- OS Packages
- Libraries
- Known CVEs

## Kubernetes Security

Implemented:

- Service Account Authentication
- RBAC Authorization
- Token-Based Cluster Access

---

# Challenges Faced & Troubleshooting

During implementation several real-world DevOps challenges were encountered and resolved.

## Jenkins Startup Failure

### Issue

Jenkins service failed to start.

### Root Cause

Latest Jenkins version required Java 21 but Java 17 was installed.

### Resolution

- Installed OpenJDK 21
- Updated Jenkins runtime
- Restarted Jenkins successfully

---

## SonarQube Quality Gate Timeout

### Issue

Pipeline execution stopped during Quality Gate validation.

### Root Cause

SonarQube webhook was not configured.

### Resolution

- Configured SonarQube Webhook
- Integrated Jenkins and SonarQube
- Verified webhook communication

---

## Docker Hub Push Failure

### Issue

Docker push returned authorization errors.

### Root Cause

Docker image repository belonged to a different user.

### Resolution

- Created personal Docker Hub repository
- Updated IMAGE_NAME variable
- Successfully pushed images

---

## Kubernetes Authentication Failure

### Issue

Deployment stages failed during Kubernetes resource creation.

### Root Cause

Incorrect Kubernetes Service Account Token.

### Resolution

- Generated new Service Account Token
- Updated Jenkins Credentials
- Verified cluster access

---

## EKS Connectivity Issues

### Issue

kubectl commands failed due to authentication errors.

### Root Cause

Incorrect cluster credentials.

### Resolution

- Reconfigured kubeconfig
- Updated EKS access permissions
- Validated cluster connectivity

---

## Storage Exhaustion on Jenkins Server

### Issue

Pipeline execution failed due to low disk space.

### Root Cause

Docker images, build artifacts, and temporary files consumed available storage.

### Resolution

- Removed unused Docker images
- Cleaned Jenkins workspace
- Freed disk space

---

## Load Balancer Access Issue

### Issue

Application appeared deployed but was inaccessible from browser.

### Root Cause

Application redirected traffic to login endpoint.

### Resolution

- Verified Kubernetes Services
- Verified Endpoints
- Verified Load Balancer Configuration
- Successfully accessed application through login page

---

## Installation & Configuration

#### Installed Components

- Jenkins
- OpenJDK 21
- Maven
- Docker
- Trivy
- kubectl
- AWS CLI

#### Installation Commands

##### Update Packages

```bash
sudo apt update && sudo apt upgrade -y
```

##### Install Java 21

```bash
sudo apt install openjdk-21-jdk -y
java -version
```

##### Install Jenkins

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y

sudo systemctl enable jenkins
sudo systemctl start jenkins
```

##### Retrieve Jenkins Initial Password

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

##### Install Maven

```bash
sudo apt install maven -y
mvn -version
```

##### Install Docker

```bash
sudo apt install docker.io -y

sudo systemctl enable docker
sudo systemctl start docker

sudo usermod -aG docker ubuntu
newgrp docker
```

##### Install Trivy

```bash
sudo apt install wget apt-transport-https gnupg lsb-release -y

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | \
gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null

echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] \
https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | \
sudo tee /etc/apt/sources.list.d/trivy.list

sudo apt update
sudo apt install trivy -y
```

##### Install AWS CLI

```bash
sudo snap install aws-cli --classic
```

##### Install kubectl

```bash
sudo snap install kubectl --classic
```

##### Verify Installations

```bash
java -version
jenkins --version
mvn -version
docker --version
trivy --version
kubectl version --client
aws --version
```

# Final Outcome

Successfully implemented:

-  Automated Jenkins CI/CD Pipeline
-  SonarQube Code Analysis
-  Nexus Artifact Management
-  Trivy Security Scanning
-  Docker Build & Push Automation
-  Amazon EKS Deployment
-  Blue-Green Deployment Strategy
-  Zero Downtime Traffic Switching
-  AWS Load Balancer Integration
-  End-to-End Deployment Automation


# Future Enhancements

- GitHub Webhook Automation
- Prometheus Monitoring
- Grafana Dashboards
- Automated Rollback Mechanism
- ArgoCD GitOps Deployment
- Multi-Environment Deployments

---

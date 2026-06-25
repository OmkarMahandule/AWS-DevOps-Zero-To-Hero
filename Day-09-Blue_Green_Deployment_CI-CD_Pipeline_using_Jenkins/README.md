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

<img width="525" height="636" alt="CI-CD" src="https://github.com/user-attachments/assets/be203d98-90b4-43cb-b557-2ee9048b3362" />


---

## Step 6: Code Analysis using SonarQube

SonarQube was integrated into the pipeline to enforce code quality and security standards.


<img width="1920" height="1080" alt="SonarQube_test_passed" src="https://github.com/user-attachments/assets/e30d36d3-94c4-41a0-a6f4-0e4f61228745" />

<img width="1920" height="1080" alt="SonarQube_BG-Tests" src="https://github.com/user-attachments/assets/d7c9a03d-2531-4370-8613-73acef02e344" />

---

## Step 7: Artifact Management using Nexus Repository

Build artifacts were automatically published to Nexus Repository.


<img width="1920" height="1080" alt="Nexus_snapshots_details" src="https://github.com/user-attachments/assets/eefcbfd5-1301-4f6c-a7a9-df8aa9771c7a" />

<img width="1920" height="1080" alt="Nexux_Malware_Risk_Analysis" src="https://github.com/user-attachments/assets/e838b1ec-9923-4e56-bf7b-4b6a50cd8090" />


---

## Step 8: Docker Image Creation and Registry Integration

The application was containerized using Docker and pushed to Docker Hub.

<img width="1920" height="1080" alt="Docker_bankapp_repo" src="https://github.com/user-attachments/assets/471fd5d6-f0b8-4d31-8b14-023b528bea0e" />

---

## Step 9: Kubernetes Deployment on Amazon EKS

Application workloads were deployed to Amazon EKS using Kubernetes manifests.

### Resources Created

- Deployments
- Services
- Service Accounts
- Secrets

---

## Step 10: Deploying Blue Environment

The Blue environment represented the currently active production version.


<img width="1915" height="1075" alt="Build_with_parameter-blue" src="https://github.com/user-attachments/assets/8f27a980-bf7d-45f4-81ed-60ea9d81117e" />

<img width="1920" height="1080" alt="Blue_Env" src="https://github.com/user-attachments/assets/e7107d84-a21c-402b-a490-8a524f5e18c5" />

<img width="1920" height="1080" alt="Build_07_Console_output" src="https://github.com/user-attachments/assets/4f8651ca-db8c-4c35-83bf-d760ce609aa4" />

<img width="1920" height="1080" alt="Blue_env_CLI" src="https://github.com/user-attachments/assets/88c513a1-b77b-425c-9e0b-2aa0dac0f4e2" />

---

## Step 11: Deploying Green Environment

The Green environment hosted the new application version for validation and testing.


<img width="1920" height="1080" alt="Green_Env_parameter" src="https://github.com/user-attachments/assets/befd1b19-f02d-4f16-aa83-5af9effcf238" />

<img width="1920" height="1080" alt="Build_08_Console_output" src="https://github.com/user-attachments/assets/2b5c2c92-7bf4-4a70-a433-a045517e0acd" />

<img width="1920" height="1080" alt="Blue-Green_Env_CLI" src="https://github.com/user-attachments/assets/5c1e3ef9-da56-463e-812f-abdc38c3acd4" />


---

## Step 12: Traffic Switching using Blue-Green Deployment

Traffic was shifted from the Blue environment to the Green environment by updating Kubernetes Service selectors.

This ensured:

- Zero Downtime
- Safe Deployments
- Instant Rollback Capability

<img width="1920" height="1080" alt="Green_pipline_traffic_shift" src="https://github.com/user-attachments/assets/0cba3541-91bf-4238-a179-a4d4d971843c" />


---

## Step 13: Deployment Verification

The deployment was verified by checking:

- Pods
- Services
- Endpoints
- Load Balancer
- Application Accessibility

<img width="1920" height="1080" alt="Pipeline_stages_Buils_07_08" src="https://github.com/user-attachments/assets/ed132300-b30f-4636-81b5-794622bbd450" />

---

## Step 14: Application Validation

The application was successfully accessed through the AWS Load Balancer endpoint, confirming successful deployment.


<img width="1920" height="1080" alt="Blue-Green_App_UI" src="https://github.com/user-attachments/assets/3a1876eb-da23-4ff4-8ac1-e99564f45221" />

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

- Code Analysis
- Vulnerability Detection
- Code Quality Validation
- Quality Gate Enforcement

  <img width="1920" height="1080" alt="SonarQube_test_passed" src="https://github.com/user-attachments/assets/2f1fdee3-8c2b-4100-adb3-814539c4d229" />


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

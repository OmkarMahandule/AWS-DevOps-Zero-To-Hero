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
<img width="1920" height="1080" alt="Jenkins-SonarQube-report_pending" src="https://github.com/user-attachments/assets/cd1ec221-162a-4255-942f-88ac4c18758d" />


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

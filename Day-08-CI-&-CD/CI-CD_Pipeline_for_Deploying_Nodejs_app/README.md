# CI/CD Pipeline for Node.js Chat Application using AWS CodePipeline, CodeBuild & CodeDeploy

## Project Overview

This project demonstrates the implementation of a Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Node.js Chat Application using AWS managed services.

The application source code is stored in GitHub. Whenever changes are pushed to the repository, AWS CodePipeline automatically triggers the deployment workflow, which deploys the application to multiple EC2 instances using AWS CodeDeploy.

## Architecture

<img width="1536" height="1024" alt="ChatGPT Image Jun 9, 2026, 08_26_35 PM" src="https://github.com/user-attachments/assets/bfff5ddb-128f-4da9-b19e-b634bf7f04f4" />


The deployment targets multiple EC2 instances identified through instance tags.

### Deployment Strategy

* Deployed the Node.js Chat Application on **3 Amazon EC2 instances**
* Used **Instance Tagging** for deployment targeting

  * Tag Key: `Name`
  * Tag Value: `<instance_name>`
* Configured CodeDeploy Deployment Group using EC2 instance tags
* Implemented **Half-at-a-Time Deployment** strategy

  * Deploys to 2 instances at a time
  * Reduces deployment risk by updating a subset of servers first

## AWS Services Used

* Amazon EC2
* AWS IAM
* AWS CodePipeline
* AWS CodeDeploy
* AWS CodeBuild
* GitHub

## Implementation Steps

<img width="1915" height="942" alt="Steps" src="https://github.com/user-attachments/assets/62f59141-0559-403b-bab5-d911c8eb4b34" />


### 1. Create IAM Roles

Created the required IAM roles for:

* EC2 Instance
* AWS CodeDeploy Service
* AWS CodeBuild
* AWS CodePipeline

Attached the necessary policies to enable communication between AWS services.

---

### 2. Launch EC2 Instances

Created multiple Amazon EC2 instances and:

* Installed Node.js
* Installed PM2
* Installed and configured CodeDeploy Agent
* Attached IAM Instance Profile
* Assigned instance tags for deployment targeting

Example:

```text
Key   : Name
Value : instance_name
```

---
<img width="1920" height="911" alt="Instances" src="https://github.com/user-attachments/assets/c290e43f-2b6d-45a7-9d4a-3634f9938f7c" />


### 3. Configure CodeDeploy

Created a CodeDeploy Application and Deployment Group.

Deployment Group Configuration:

* Deployment Type: In-Place
* Environment Configuration: Amazon EC2 Instances
* Instance Selection: EC2 Tags
* Deployment Configuration: HalfAtATime

This allowed CodeDeploy to deploy the application to only a portion of the fleet at a time.
<img width="1920" height="911" alt="Code_dep_grp" src="https://github.com/user-attachments/assets/5782ac43-407d-41da-a9b5-fdce7efbc115" />

<img width="1920" height="911" alt="codedeploy-application-dep_grp" src="https://github.com/user-attachments/assets/6086070e-b82e-445f-ab51-0b990b993f7e" />

---

### 4. Configure CodeBuild

Created a CodeBuild project to:

* Retrieve source code from GitHub
* Prepare deployment artifacts
* Pass artifacts to the deployment stage

---

### 5. Configure CodePipeline

Created a CI/CD pipeline consisting of:
<img width="1915" height="942" alt="pipeline-overview" src="https://github.com/user-attachments/assets/85a36be2-6e3a-44b0-ab99-bef482e75e37" />

<img width="1920" height="911" alt="Pipeline" src="https://github.com/user-attachments/assets/00eaccb6-61cf-4057-a88a-25031eab1f8f" />

#### Source Stage

* GitHub Repository

#### Build Stage

* AWS CodeBuild

#### Deploy Stage

* AWS CodeDeploy

Pipeline Flow:

```text
GitHub
   ↓
CodePipeline
   ↓
CodeBuild
   ↓
CodeDeploy
   ↓
EC2 Instances
```

---

### 6. Application Deployment

The Node.js Chat Application was deployed to multiple EC2 instances through CodeDeploy lifecycle hooks.

Deployment files used:

* `appspec.yml`
* `afterinstall.sh`
* `applicationstart.sh`

Responsibilities:

#### afterinstall.sh

```bash
npm install
```

#### applicationstart.sh

```bash
pm2 start server.js
```

<img width="1920" height="891" alt="Chat app EC2-1" src="https://github.com/user-attachments/assets/c327a53a-2366-4e0d-864c-e705a34fe4ec" />

<img width="1920" height="891" alt="Chat-app-EC2-2" src="https://github.com/user-attachments/assets/c16f98d6-a878-4db6-9338-75b31421a675" />

---

### 7. Validate CI/CD Workflow

To validate the pipeline:

1. Modified the application source code.
2. Pushed changes to GitHub.
3. Verified automatic pipeline execution.
4. Confirmed successful deployment on EC2 instances.
5. Accessed the application through:

---

## Learning Outcomes

Through this project, I gained hands-on experience with:

* CI/CD Pipeline Implementation
* AWS CodePipeline
* AWS CodeBuild
* AWS CodeDeploy
* Deployment Groups & EC2 Tagging
* Blue/Green & Rolling Deployment Concepts
* Half-at-a-Time Deployment Strategy
* Node.js Application Deployment on EC2
* PM2 Process Management
* GitHub Integration with AWS Services
* Infrastructure Automation Concepts

## Future Improvements

* Implement Blue/Green Deployments
* Add Automated Testing Stage
* Deploy behind an Application Load Balancer
* Integrate CloudWatch Monitoring
* Configure Auto Scaling Group Deployments
* Add Approval Stages in CodePipeline


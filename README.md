# AWS DevOps Zero to Hero: 30-Day Learning Challenge

Welcome to my 30-day AWS DevOps journey!  

I’ve spent time learning the fundamentals snd theory behind Linux, Git, Docker, CI/CD, cloud, automation, and monitoring. Now, I’m moving to **hands-on implementation**, focused on AWS. Over the next 30 days, I’ll be building projects, exploring services, and documenting everything publicly.  

This repository will serve as my personal learning journal. I’ll include notes, scripts, mini-projects, and key takeaways — everything I do to become proficient in AWS DevOps.  

---

## Table of Contents

1. [Day 1 — Introduction to AWS](#day-1-—-introduction-to-aws)  
2. [Day 2 — IAM (Identity and Access Management)](#day-2-—-iam-identity-and-access-management)  
3. [Day 3 — EC2 Instances](#day-3-—-ec2-instances)  
4. [Day 4 — Networking with VPC](#day-4-—-networking-with-vpc)  
5. [Day 5 — Security in AWS](#day-5-—-security-in-aws)  
6. [Day 6 — Route 53](#day-6-—-route-53)  
7. [Day 7 — Secure VPC Setup with EC2](#day-7-—-secure-vpc-setup-with-ec2)  
8. [Day 8 — AWS Interview Questions](#day-8-—-aws-interview-questions)  
9. [Day 9 — S3 Storage](#day-9-—-s3-storage)  
10. [Day 10 — AWS CLI](#day-10-—-aws-cli)  
11. [Day 11 — CloudFormation](#day-11-—-cloudformation)  
12. [Day 12 — CodeCommit](#day-12-—-codecommit)  
13. [Day 13 — CodePipeline](#day-13-—-codepipeline)  
14. [Day 14 — CodeBuild](#day-14-—-codebuild)  
15. [Day 15 — CodeDeploy](#day-15-—-codedeploy)  
16. [Day 16 — CloudWatch](#day-16-—-cloudwatch)  
17. [Day 17 — Lambda](#day-17-—-lambda)  
18. [Day 18 — CloudWatch Events & EventBridge](#day-18-—-cloudwatch-events--eventbridge)  
19. [Day 19 — CloudFront](#day-19-—-cloudfront)  
20. [Day 20 — Elastic Container Registry (ECR)](#day-20-—-elastic-container-registry-ecr)  
21. [Day 21 — ECS](#day-21-—-ecs)  
22. [Day 22 — EKS](#day-22-—-eks)  
23. [Day 23 — Secrets Manager](#day-23-—-secrets-manager)  
24. [Day 24 — Terraform](#day-24-—-terraform)  
25. [Day 25 — CloudTrail & Config](#day-25-—-cloudtrail--config)  
26. [Day 26 — Elastic Load Balancer](#day-26-—-elastic-load-balancer)  
27. [Day 27 — AWS Interview Questions](#day-27-—-aws-interview-questions)  
28. [Day 28 — Cloud Migration](#day-28-—-cloud-migration)  
29. [Day 29 — Best Practices & Job Prep](#day-29-—-best-practices--job-prep)  
30. [Day 30 — Final Project with RDS](#day-30-—-final-project-with-rds)  

---

## What This Challenge Includes

- Daily learning summaries  
- Mini-projects and real-world use cases  
- Commands, configurations, and setup notes  
- AWS interview questions and practical tips  

---

## 30-Day Learning Path

### Day 1 — Introduction to AWS
Understand the difference between private and public cloud, why companies are moving to the cloud, and the benefits it offers. Explore AWS core services and set up an AWS account to navigate the Management Console.

### Day 2 — IAM (Identity and Access Management)
Create users, groups, and roles. Learn how to apply permissions correctly and follow security best practices.

### Day 3 — EC2 Instances
Launch virtual servers, connect via SSH, and understand instance types, key pairs, and security groups.  
**Project:** Deploy a simple web application (like Jenkins) on the EC2 instance and access it externally.

### Day 4 — Networking with VPC
Create and configure VPCs, subnets, and route tables to design a secure network for applications.

### Day 5 — Security in AWS
Implement Security Groups, Network ACLs, and IAM policies. Ensure proper access and protection of resources.

### Day 6 — Route 53
Manage domain names, DNS records, health checks, and routing policies.  
**Project:** Configure and manage a domain using Route 53.

### Day 7 — Secure VPC Setup with EC2
Design a VPC with public and private subnets, configure route tables, internet and NAT gateways, security groups, IAM roles, and SSH key access. Test connectivity and permissions.  
**Project:** Launch EC2 instances in both public and private subnets, set up security and IAM roles, and validate connectivity and security settings.

### Day 8 — AWS Interview Questions
Review key concepts on EC2, IAM, and VPC.

### Day 9 — S3 Storage
Create buckets, upload files, use versioning, lifecycle policies, and access controls.

### Day 10 — AWS CLI
Learn to interact with AWS services from the command line efficiently.

### Day 11 — CloudFormation
Automate resource provisioning using Infrastructure as Code (IaC).  
**Project:** Build a CloudFormation template that provisions a fully configured application stack including EC2, networking, and security components.

### Day 12 — CodeCommit
Set up a managed Git repository and configure collaboration workflows.  
**Project:** Configure a CodeCommit repository for a team project including access control.

### Day 13 — CodePipeline
Build CI/CD pipelines to automate software deployment.  
**Project:** Create a pipeline integrating source, build, and deployment stages for an application.

### Day 14 — CodeBuild
Configure build projects and automate build/testing workflows.  
**Project:** Run builds using CodeBuild and integrate with other AWS services.

### Day 15 — CodeDeploy
Automate deployments with Blue/Green strategies.  
**Project:** Deploy a sample application with zero-downtime deployment and rollback options.

### Day 16 — CloudWatch
Monitor AWS resources, create alarms, and set notifications.  
**Project:** Configure CloudWatch alarms for critical application metrics.

### Day 17 — Lambda
Create serverless functions and trigger them with events.  
**Project:** Deploy Lambda functions to automate simple workflows.

### Day 18 — CloudWatch Events & EventBridge
Build event-driven workflows connecting multiple AWS services.  
**Project:** Automate workflows using CloudWatch Events and EventBridge rules.

### Day 19 — CloudFront
Configure CDN for static website hosting via S3.  
**Project:** Serve an S3-hosted static website through CloudFront.

### Day 20 — Elastic Container Registry (ECR)
Store Docker images and integrate them into CI/CD pipelines.  
**Project:** Build a pipeline that automatically builds, pushes, and deploys Docker images to ECR.

### Day 21 — ECS
Deploy and manage containerized applications with auto-scaling.  
**Project:** Deploy a multi-container application using ECS and configure auto-scaling.

### Day 22 — EKS
Set up Kubernetes clusters and deploy apps with manifests.  
**Project:** Deploy a sample application on EKS using Kubernetes manifests.

### Day 23 — Secrets Manager
Store and rotate sensitive credentials securely.  
**Project:** Configure Secrets Manager and integrate secret retrieval into applications.

### Day 24 — Terraform
Provision AWS infrastructure with Terraform.  
**Project:** Create a VPC and deploy two applications across different availability zones with a load balancer.

### Day 25 — CloudTrail & Config
Audit AWS activity and enforce compliance rules.  
**Project:** Configure CloudTrail to log API activities and enforce compliance using AWS Config rules.

### Day 26 — Elastic Load Balancer
Distribute traffic across instances and ensure high availability.  
**Project:** Configure an Elastic Load Balancer and observe load distribution across instances.

### Day 27 — AWS Interview Questions
Review practical AWS and DevOps concepts.

### Day 28 — Cloud Migration
Learn strategies and tools for moving applications to AWS.

### Day 29 — Best Practices 
Review security, performance, and cost optimization best practices.

### Day 30 — Final Project with RDS
Bring everything together in a multi-service AWS project including databases and compute resources.

---

## How to Use This Repository

I will update this repo daily with:  

- Learning notes  
- Projects and code snippets  
- Screenshots and diagrams  
- Key lessons and insights  

Follow along if you’re learning AWS or DevOps. Feedback, suggestions, or tips are always welcome!

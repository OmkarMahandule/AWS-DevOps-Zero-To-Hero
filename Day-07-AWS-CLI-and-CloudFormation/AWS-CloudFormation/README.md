# AWS CloudFormation – Infrastructure as Code

> Part of my **AWS-DevOps-Zero-To-Hero Challenge**.
> This document covers **AWS CloudFormation concepts and hands-on implementation**, including real-world errors, debugging, and learnings.

---

## Objective
Learn how to **provision, manage, and delete AWS infrastructure using code** instead of manual console actions by using **AWS CloudFormation**.

---

## Environment Details
- OS: Ubuntu / Linux
- AWS Region: eu-north-1 (Stockholm)
- Template Format: YAML
- Resources Used: EC2, VPC components, Security Groups, IAM, Key Pair

---
## Understanding CloudFormation Basics

CloudFormation allows defining infrastructure as code using templates.

components:
- **Template** – YAML/JSON file defining resources
- **Stack** – Running instance of a template
- **Parameters** – Inputs passed at stack creation
- **Resources** – AWS services created
- **Outputs** – Useful values returned after creation
- **Events** – Detailed logs of stack operations

benefits:
- Repeatable infrastructure
- Version control
- Automatic rollback on failure
- Consistency across environments

---

## Creating the CloudFormation Template
 - Open CloudFormation-Templete File

## Issues Faced & Learnings

| Issue | Root Cause | Learning |
|------|-----------|----------|
| AMI not found | Region mismatch | AMIs are region-specific |
| Key pair error | Key not created | Pre-create required resources |
| Unsupported config | Instance type not available | Check region limits |
| Stack rollback | Invalid parameters | CloudFormation validates early |

---

## Best Practices Learned
- Avoid hardcoding region-specific values
- Use parameters for flexibility
- Read **Events tab** before guessing
- Clean up stacks after testing
- Prefer IaC over manual creation

---

# AWS CloudFormation – Infrastructure as Code (Hands-on)

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

## Step 1: Understanding CloudFormation Basics

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

## Step 2: Creating the CloudFormation Template

Actions performed:
- Created a YAML template
- Defined parameters for flexibility
- Added EC2 instance resource
- Used intrinsic functions (`!Ref`, `!Sub`)

Example parameter definition:
    
    Parameters:
      KeyPairName:
        Type: AWS::EC2::KeyPair::KeyName
        Description: Existing EC2 Key Pair in eu-north-1

Learning:
- Parameters make templates reusable
- Values are passed during stack creation (not hardcoded)

---

## Step 3: Stack Creation via AWS Console

Actions performed:
- Opened CloudFormation console
- Clicked **Create stack**
- Uploaded template file
- Entered parameter values
- Submitted stack for creation

<img width="1912" height="941" alt="Screenshot from 2026-02-04 11-38-20" src="https://github.com/user-attachments/assets/631980b6-4203-4060-b908-d864b2cc653d" />

---

## Step 4: Stack Failure – AMI Not Found

Error encountered:
- EC2 instance creation failed
- AMI ID did not exist in eu-north-1

Learning:
- AMIs are **region-specific**
- Hardcoding AMIs is a bad practice
- Each region requires a valid AMI ID
---

---

## Step 5: Fixing Errors and Recreating Stack

Actions performed:
- Updated template values
- Ensured key pair existed
- Verified instance type support
- Recreated stack from scratch

Stack states observed:
- CREATE_IN_PROGRESS
- CREATE_COMPLETE

<img width="1912" height="947" alt="Screenshot from 2026-02-04 12-34-44" src="https://github.com/user-attachments/assets/5afc6e6b-c87e-4d99-99d3-dd6d07cc9296" />

---

## Step 6: Stack Deletion (Cleanup)

Actions performed:
- Deleted CloudFormation stack after testing
- Verified all resources were removed automatically

Learning:
- Stack deletion cleans all managed resources
- Prevents unnecessary AWS costs
- IaC encourages clean infrastructure lifecycle

---

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

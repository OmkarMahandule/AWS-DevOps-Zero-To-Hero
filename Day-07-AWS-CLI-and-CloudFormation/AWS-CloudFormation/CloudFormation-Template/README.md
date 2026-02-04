# Day 7 – AWS CloudFormation (EC2 Application Stack)

This document demonstrates hands-on experience with **AWS CloudFormation** by provisioning a complete **EC2-based application stack** using **Infrastructure as Code (IaC)**.

---

## Stack Overview

The CloudFormation template provisions the following resources:

- Custom VPC
- Public Subnet
- Internet Gateway
- Route Table with Internet Route
- Security Group (SSH + HTTP)
- EC2 Instance
- Apache Web Server (installed automatically using UserData)

---

## Prerequisites

Before creating the stack:

- AWS account is active
- Region is set to **Europe (Stockholm) – eu-north-1**
- EC2 Key Pair exists in the same region

---

## Step 0: Create EC2 Key Pair
**Region:** eu-north-1 (Stockholm)

1. Go to **EC2 → Key Pairs**
2. Click **Create key pair**
3. Enter key pair name
4. Key type: **RSA**
5. File format: **.pem**
6. Download and store the key securely
   
<img width="1918" height="611" alt="Screenshot from 2026-02-04 17-01-20" src="https://github.com/user-attachments/assets/fbd2e40a-de14-4767-8366-70a3e49c70ed" />

---

## Step 1: Open CloudFormation

1. Open **AWS Management Console**
2. Search for **CloudFormation**
3. Click **Create stack**
4. Select: with new resources (standard)

---

## Step 2: Upload Template

1. Select **Upload a template file**
2. Upload `template.yaml`
3. Click **Next**

   <img width="1916" height="915" alt="Screenshot from 2026-02-04 17-04-11" src="https://github.com/user-attachments/assets/84a4fa49-f333-41eb-91e7-db8244ba34fe" />


---

## Step 3: Configure Stack Details

### Stack Name: omkar-ec2-app-stack or (your-stack-name)

### Parameters
| Parameter | Value |
|---------|-------|
| KeyPairName | omkar-keypair |

Click **Next**

<img width="1916" height="915" alt="Screenshot from 2026-02-04 17-06-54" src="https://github.com/user-attachments/assets/bd15db54-61e0-4a2b-a629-58da0f582208" />

---

## Step 4: Stack Options

- Leave all options as default
- Click **Next**

---

## Step 5: Review and Create Stack

1. Review configuratio
2. Click **Create stack**

---

## Step 6: Monitor Stack Creation

Open the **Events** tab and observe resource creation:

### Networking
- VPC created
- Internet Gateway created
- IGW attached to VPC
- Public Subnet created
- Route Table created
- Default route (0.0.0.0/0)
- Subnet associated with Route Table

### Security
- Security Group created
  - SSH (22)
  - HTTP (80)

### Compute
- EC2 instance launched
- Ubuntu 22.04 AMI resolved dynamically via SSM
- Apache installed using UserData

Final stack status:
CREATE_COMPLETE


<img width="1916" height="912" alt="Screenshot from 2026-02-04 17-10-26-1" src="https://github.com/user-attachments/assets/0deace65-341e-45ef-bad8-75db4882bfca" />

---

## Step 7: Verify EC2 Instance

1. Go to **EC2 → Instances**
2. Confirm instance state is **Running**
3. Note the **Public IPv4 address**

<img width="1916" height="912" alt="Screenshot from 2026-02-04 17-12-00" src="https://github.com/user-attachments/assets/c5381639-f84e-433d-967a-4f387072487f" />


---

## Step 8: Verify Apache Web Server

- Open browser and visit:
   http://<EC2-Public-IP>

- Expected output:
  Apache2 Ubuntu Default Page  

This confirms:
- Internet Gateway works
- Route Table is correct
- Security Group allows HTTP
- Apache installed automatically

<img width="1913" height="1026" alt="Screenshot from 2026-02-04 12-36-41" src="https://github.com/user-attachments/assets/ba35fd9f-38de-465e-a6f5-b86efe134328" />


---

## Key CloudFormation Concepts Demonstrated

- Infrastructure as Code (IaC)
- Parameterized templates
- Resource dependency management
- VPC and subnet design
- Security group configuration
- Dynamic AMI resolution using SSM
- Automated provisioning using UserData
- Stack lifecycle management

---

---

## Conclusion

This CloudFormation implementation demonstrates the ability to design, provision, verify, and clean up AWS infrastructure using Infrastructure as Code best practices.


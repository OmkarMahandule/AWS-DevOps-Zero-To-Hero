# Day 04 — AWS Networking with VPC

## Objective
To design, configure, and troubleshoot AWS networking by creating a secure VPC using subnets, route tables, gateways, and security controls, based on real-world scenarios.

---

## What is a VPC?
A Virtual Private Cloud (VPC) is a logically isolated network in AWS that gives full control over IP addressing, routing, and network security.

<img width="862" height="528" alt="image" src="https://github.com/user-attachments/assets/df496f34-0a2e-4ece-88a9-effbce0c7c5c" />


---

## AWS Networking Components

### 1️ VPC
- Acts as a private network inside AWS
- Defined using CIDR blocks (example: `10.0.0.0/16`)
- Foundation for all AWS resources

---

### 2️ Subnets
Subnets divide a VPC into smaller networks.

**Types**
- **Public Subnet** – has internet access
- **Private Subnet** – no direct internet access

**Example**
- Public Subnet: `10.0.1.0/24`
- Private Subnet: `10.0.2.0/24`

---

### 3️ Internet Gateway (IGW)
- Enables communication between VPC and the internet
- Must be attached to the VPC

---

### 4️ Route Tables
Control how traffic flows inside the VPC.

**Public Route Table**
- Destination: 0.0.0.0/0
- Target: Internet Gateway

**Private Route Table**
- No internet route
- Used for internal traffic only

---

### 5️ Security Groups
- Instance-level firewall
- Stateful (return traffic automatically allowed)

**Common Rules**
- SSH (22) – restricted to personal IP
- HTTP (80)
- HTTPS (443)

---

### 6️ Network ACLs (NACLs)
- Subnet-level security
- Stateless
- Optional additional security layer

---

## Hands-On Steps Performed
1. Created a custom VPC with CIDR `10.0.0.0/16`
   
   <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/ac979e9f-cc29-421d-9c5d-6b13bd4a482b" />

2. Created public and private subnets
   
   <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/a5c7988a-6557-4ae7-a841-17d4c681101b" />

3. Attached an Internet Gateway to the VPC

   <img width="800" height="601" alt="image" src="https://github.com/user-attachments/assets/c82a0e4f-da06-4122-b0f4-aed2f9f5f658" />

4. Created and configured route tables

   <img width="800" height="601" alt="image" src="https://github.com/user-attachments/assets/94dbec10-3977-44c1-b391-b9312c2cf461" />

5. Associated public route table with public subnet
6. Launched EC2 instance in public subnet

    <img width="800" height="601" alt="image" src="https://github.com/user-attachments/assets/84bbfebf-de95-4ad7-85ed-2feeb6d2bad7" />

7. Verified internet and SSH connectivity

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/9852365d-1da0-41b4-9002-06d8e0e4a2e4" />

---

## Real-World Problems Encountered & Solutions

### Problem 1: EC2 instance had no internet access
**Issue**
- EC2 instance could not access the internet or install packages.

**Root Cause**
- Internet Gateway was not attached to the VPC
- Route table did not have a default route

**Solution**
- Attached Internet Gateway to the VPC
- Added `0.0.0.0/0` route pointing to IGW
- Associated route table with the public subnet

---

### Problem 2: SSH connection timed out
**Issue**
- Unable to SSH into EC2 instance.

**Root Cause**
- Port 22 not allowed in Security Group
- Incorrect source IP address

**Solution**
- Inbound Rule:
- Type: SSH
- Port: 22
- Source: My IP

  ## Key Learnings
- Proper VPC design prevents security risks
- Understanding traffic flow simplifies troubleshooting
- Public and private subnet separation is critical
- AWS networking is simple once fundamentals are clear




# Day 5 — AWS Route 53 🌐

## Overview
On Day 6 of my **30-Day DevOps Learning Challenge**, I worked on understanding and setting up **AWS Route 53**, AWS’s scalable DNS and domain management service.

This lab focused on learning how DNS works in real cloud environments and how traffic is routed to AWS resources.

---

## What I Learned
- Basics of DNS and domain name resolution
- What AWS Route 53 is and where it fits in cloud architecture
- Hosted Zones (Public vs Private)
- DNS record types:
  - A Record
  - CNAME
  - ALIAS
- How Route 53 maps a domain to AWS resources
- Importance of network configuration before DNS (Security Groups)

---

## Prerequisites
- AWS Account
- EC2 instance running with a **Public IPv4**
- HTTP (Port 80) allowed in the Security Group
- Apache web server running on EC2

---

## Project: Route 53 + EC2 Integration

### Step 1: Prepare EC2
- Launched an EC2 instance
- Installed Apache web server
- Verified Apache accessibility using the EC2 Public IP

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/c5d4507c-761c-4352-a5ad-1a0ad218829c" />


### Step 2: Create a Hosted Zone
- Created a **Public Hosted Zone** in Route 53
- Observed default NS and SOA records

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/6cf03672-71dd-40b0-8fa3-6e02ca2ad4e2" />


### Step 3: Configure DNS Records
- Created an **A Record**
- Mapped the domain name to the EC2 Public IPv4 address

  <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/bb495869-4b1f-4d82-ae7c-0412ed7584c5" />


  ### step 4: Testing- Install a Web Server on EC2
  - Apache2

    <img width="800" height="608" alt="image" src="https://github.com/user-attachments/assets/a9d90911-1b1e-4a98-a4fb-7caf41cd9801" />




---

## Challenges Faced & Fixes

### Issue: Apache page not loading
**Cause:** HTTP (Port 80) was blocked in the Security Group  
**Fix:** Added an inbound rule allowing HTTP from `0.0.0.0/0`

This highlighted the importance of networking fundamentals before DNS configuration.

---

## Key Takeaways
- DNS works only when the underlying service is reachable
- Security Groups act as the first line of defense
- Route 53 is independent of compute but tightly linked to networking
- Small misconfigurations can completely block access

---

## Status
1. EC2 configured  
2. Apache running  
3. DNS records created  

 Ready to explore advanced routing and health checks next

---


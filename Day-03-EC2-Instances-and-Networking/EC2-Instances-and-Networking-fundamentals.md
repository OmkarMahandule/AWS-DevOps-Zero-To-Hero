# Day 3 – EC2 & Networking Fundamentals

Focus 👉 Launching EC2 instances, understanding networking, and practicing real-world AWS setups for DevOps.

---

## Starting State

Checked the AWS account and networking setup before launching instances:

- No EC2 instances running  
- Default VPC present, but no custom subnets or security groups  
- No key pairs created for SSH access  

---

## EC2 Instance Launch

**Steps performed:**

- Selected **Amazon Linux 2 AMI**  
- Instance type: `t2.micro` (free-tier)  
- Configured **IAM role** for S3 access  
- Key pair generated: `devops-keypair`  
- Security group created:
  - SSH (22) from my IP only  
  - HTTP (80) open for testing web server
 
    <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/bdd5a50c-8ddf-4875-942d-60095f935f63" />


**Takeaway:** Proper IAM roles and key pairs are essential for secure EC2 access.

---

## Networking Setup

**VPC / Subnet Configuration:**

- Used default VPC for simplicity  
- Verified public subnet availability  
- Assigned Elastic IP to EC2 instance for consistent access  

**Security Groups:**

- SSH restricted to trusted IPs  
- HTTP opened temporarily for testing a web server  

**Observations:**  
- Restricting access at the security group level prevents unauthorized access  
- Public vs private subnet understanding is critical for multi-tier architecture

---

## Connecting to EC2

**SSH Connection Test:**

```bash
ssh -i devops-keypair.pem ec2-user@<Elastic-IP>
```

<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/2da8b9fb-fa4e-4378-b617-73d2415abdb6" />



**Validation:**  
- Able to login successfully  
- Installed `httpd` and confirmed Apache server running  

**Guideline:** Always validate connectivity and role permissions after instance launch.

---

## Common Errors & Troubleshooting

1. **SSH Permission Denied**  
   - Cause: Incorrect key permissions  
   - Fix: `chmod 400 devops-keypair.pem`  

2. **Unable to Access Web Server**  
   - Cause: Security group HTTP port not open  
   - Fix: Add inbound rule for port 80
  
   <img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/80970fc5-fa13-475a-9246-a307bf3560e1" />


3. **EC2 Cannot Access S3 Bucket**  
   - Cause: IAM role not attached or incorrect policy  
   - Fix: Attach proper IAM role with `AmazonS3ReadOnlyAccess`  

---

## Observations & Notes

- Launching EC2 with correct IAM role saves manual credential management  
- Security groups are the first line of defense; always restrict access  
- Elastic IPs are useful for predictable connectivity during testing  

---

Day 3 complete — EC2 instances launched, networking understood, and initial web server validated.

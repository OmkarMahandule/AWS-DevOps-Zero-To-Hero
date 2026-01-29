
# AWS CLI Setup — Day 01

This document covers the installation and configuration of AWS CLI.

---

## 1. Install AWS CLI

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
## 2. Configure AWS CLI
Set up your AWS credentials:

```bash
aws configure
```
 Provide filowing when prompted:

AWS Access Key ID: <YOUR_ACCESS_KEY>

AWS Secret Access Key: <YOUR_SECRET_KEY>

Default region name: e.g., us-east-1

Default output format: json

## 3. Verify Configuration

Check if your CLI is correctly configured:
```bash
aws sts get-caller-identity
```
You should see output similar to:

```bash

{
    "UserId": "AIDAEXAMPLEID",
    "Account": "123456789012",
    "Arn": "arn:aws:iam::123456789012:user/your-username"
}
```

## 4. Tips & Best Practices
1. Keep credentials safe: Do NOT commit your AWS keys to GitHub.

2. Use IAM users: Create a dedicated IAM user for learning projects instead of using root account.

3. Verify before starting projects: Always confirm AWS CLI works to avoid issues later.

4. Documentation is key: Write down commands you use for future reference.
















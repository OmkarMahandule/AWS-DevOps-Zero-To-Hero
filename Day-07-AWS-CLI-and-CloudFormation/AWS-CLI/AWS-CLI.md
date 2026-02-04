# Day 7 – AWS CLI (Complete Hands-on)

> Part of my ** AWS-DevOps-Zero-To-Hero Challenge** 
---

## Objective
Learn to interact with AWS services efficiently using the **AWS Command Line Interface (CLI)** and perform real infrastructure operations without relying on the AWS Console.

---

## Environment Details
- OS: Ubuntu / Linux
- AWS Region: eu-north-1 (Stockholm)
- AWS CLI Version: v2
- Access Type: IAM User (Programmatic Access)


---

## Step 1: Install AWS CLI

Install AWS CLI:

    sudo apt update
    sudo apt install awscli -y

Verify installation:

    aws --version

<img width="1622" height="395" alt="image" src="https://github.com/user-attachments/assets/d42f2925-cb54-4ad2-b45e-891488e18238" />


---

## Step 2: IAM User Setup

Actions performed:
- Created IAM user for AWS CLI usage
- Enabled programmatic access
- Attached required IAM policies

IAM policies attached:
- AmazonS3FullAccess
- AmazonEC2FullAccess
- CloudWatchReadOnlyAccess
- IAMReadOnlyAccess

<img width="1918" height="957" alt="image" src="https://github.com/user-attachments/assets/55dbba2c-e49f-4378-ac46-0585b97224ca" />

---

## Step 3: Configure AWS CLI

Configure the AWS CLI:

    aws configure

Values entered:
- Access Key ID
- Secret Access Key
- Default region name: eu-north-1
- Default output format: json

Verify configured identity:

    aws sts get-caller-identity

<img width="1917" height="831" alt="image" src="https://github.com/user-attachments/assets/a3f413d4-45fc-43dc-9ec5-68852cecbb56" />

---

## Step 4: S3 Operations Using AWS CLI

### Create S3 Bucket

    aws s3 mb s3://omkar-aws-cli-demo-bucket --region eu-north-1

---

### Upload File to S3

    echo "AWS CLI S3 upload test" > test.txt
    aws s3 cp test.txt s3://omkar-aws-cli-demo-bucket/

Verify upload:

    aws s3 ls s3://omkar-aws-cli-demo-bucket/

---

### Download File from S3

    aws s3 cp s3://omkar-aws-cli-demo-bucket/test.txt .

---

### Delete S3 Bucket (Cleanup)

    aws s3 rm s3://omkar-aws-cli-demo-bucket --recursive
    aws s3 rb s3://omkar-aws-cli-demo-bucket
    
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4267efc3-f927-417a-96ed-a080fa987e9a" />


---

## 🔹 Step 5: EC2 Management via AWS CLI

### Launch EC2 Instance

    aws ec2 run-instances \
      --image-id ami-xxxxxxxx \
      --instance-type t3.micro \
      --key-name omkar-keypair \
      --count 1 \
      --region eu-north-1

---

### List EC2 Instances

    aws ec2 describe-instances --region eu-north-1
---

### Stop EC2 Instance

    aws ec2 stop-instances \
      --instance-ids i-xxxxxxxx \
      --region eu-north-1

---

---

## Step 6: IAM Operations via CLI

List IAM users:

    aws iam list-users
    
<img width="1918" height="957" alt="image" src="https://github.com/user-attachments/assets/50da059f-2786-4287-a715-9775b2b1b7a1" />

---

List IAM policies:

    aws iam list-policies --scope AWS

Screenshot to add:
- IAM policies list

  <img width="1918" height="878" alt="image" src="https://github.com/user-attachments/assets/9e631aca-e70a-4c22-add8-4679c68d49a6" />

---

## Step 7: CloudWatch Operations via CLI

List CloudWatch metrics:

    aws cloudwatch list-metrics --region eu-north-1

---

List EC2 CPU metrics:

    aws cloudwatch list-metrics \
      --namespace AWS/EC2 \
      --metric-name CPUUtilization \
      --region eu-north-1

<img width="1918" height="427" alt="image" src="https://github.com/user-attachments/assets/04ea048d-6b2d-4ced-801f-6f1b5d854cd3" />


---

## Issues Faced & Learnings

| Issue | Learning |
|------|----------|
| Region mismatch | AWS CLI is fully region-specific |
| Access denied errors | IAM policies must be correct |
| AMI not found | AMIs vary by region |
| Cleanup mistakes | Always delete resources |

---

## Best Practices Learned
- Always verify AWS region before running commands
- Never use root account for CLI access
- Clean up AWS resources after testing
- Prefer CLI for repeatable operations
- Read AWS error messages carefully

---

## Key keaways

> “The AWS Console shows you resources.  
> The AWS CLI gives you control.”

- AWS CLI is essential for DevOps engineers
- Enables automation and scripting
- Strong foundation for CI/CD and IaC tools

---

## Next Topic
AWS CloudFormation – Infrastructure as Code

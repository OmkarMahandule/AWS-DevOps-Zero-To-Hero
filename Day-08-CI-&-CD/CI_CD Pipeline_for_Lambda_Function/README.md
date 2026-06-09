# AWS Lambda CI/CD Pipeline using CodePipeline & CodeBuild

## Project Overview

In this project, I built a simple CI/CD pipeline that automatically deploys code changes from GitHub to an AWS Lambda function.

The primary goal was to understand how AWS CodePipeline and CodeBuild work together to automate deployments without manually updating the Lambda function every time the code changes.

---

## Architecture

```text
GitHub Repository
        ↓
AWS CodePipeline
        ↓
AWS CodeBuild
        ↓
AWS Lambda

```
<img width="917" height="510" alt="image" src="https://github.com/user-attachments/assets/536918fc-dc7a-4c23-8f1b-2ecca8ebccab" />


Whenever code is pushed to GitHub, the pipeline automatically triggers, builds the deployment package, and updates the Lambda function.

---

# Implementation Steps

## Step 1: Create a Lambda Function

Created an AWS Lambda function named:

```text
Hello_world
```

Since the focus of this project was understanding the CI/CD workflow, I used a simple Python Lambda function.

---

## Step 2: Create a GitHub Repository

Created a GitHub repository containing the project files.

### Repository Structure

```text
lambda-cicd/
│
├── lambda_function.py
├── buildspec.yml
└── README.md
```

### Files Used

#### lambda_function.py

Contains the Lambda function code.

#### buildspec.yml

Contains the instructions executed by AWS CodeBuild.


<img width="1907" height="952" alt="Github repo" src="https://github.com/user-attachments/assets/2e205bf2-6af1-4dac-a546-f03606a095ef" />

---

## Step 3: Create an S3 Bucket

Created an S3 bucket to store build artifacts generated during the pipeline execution.

### Purpose

* Store deployment packages
* Store pipeline artifacts
* Enable communication between pipeline stages

<img width="1916" height="955" alt="S3 bucket" src="https://github.com/user-attachments/assets/d2dd6a20-5812-4602-9de0-988aad3f9b22" />

---

## Step 4: Create a CodeBuild Project

Created a CodeBuild project named:

```text
lambda-project01
```

### Responsibilities

* Download source code from GitHub
* Execute commands from buildspec.yml
* Create deployment package
* Update Lambda function



<img width="1916" height="955" alt="Lambda_fun Phase_details" src="https://github.com/user-attachments/assets/09ce0251-9b92-4d1b-9396-e685afdeddfa" />

---

## Step 5: Configure buildspec.yml

Configured CodeBuild instructions inside buildspec.yml.

### Key Tasks Performed

* Install zip package
* Package Lambda code
* Deploy updated code to Lambda

<img width="1901" height="845" alt="Screenshot from 2026-06-09 01-05-01" src="https://github.com/user-attachments/assets/f6a44e40-403e-4e42-b74e-4ae0b02558f6" />

---

## Step 6: Create a CodePipeline

Created a pipeline named:

```text
lambda-pipeline01
```

### Pipeline Stages

#### Source Stage

* GitHub Repository

#### Build Stage

* AWS CodeBuild
* Project: lambda-project01

### Workflow

```text
GitHub
   ↓
CodePipeline
   ↓
CodeBuild
   ↓
Lambda Deployment
```

<img width="1916" height="955" alt="Pipeline source and build phases" src="https://github.com/user-attachments/assets/41b8cc99-86d8-4000-82a6-f3cab1a5f10e" />


---

## Step 7: Test the CI/CD Pipeline

To validate the pipeline:

1. Modified the Lambda code inside `lambda_function.py`

Before Changes: 
   <img width="1916" height="955" alt="github code before updation" src="https://github.com/user-attachments/assets/fa1c88f1-8dcd-4af5-8532-0429d73c2bac" />

After Changes:
    <img width="1916" height="955" alt="github code after updation" src="https://github.com/user-attachments/assets/4f41598c-7c07-4572-93e1-c275f592a065" />

3. Committed the changes
4. Pushed the changes to GitHub
5. Pipeline triggered automatically
6. CodeBuild executed successfully
7. Lambda function was updated automatically
   
Beefore Updation:
    <img width="1916" height="955" alt="lambda fun code before updation" src="https://github.com/user-attachments/assets/aef56c71-8038-4ebc-b0ff-bedeaf221e47" />

After updation;
    <img width="1916" height="955" alt="lambda code after updation" src="https://github.com/user-attachments/assets/53b90b12-2151-4228-840d-7f4026ce0766" />

---

## Challenges Faced & Troubleshooting

### Issue 1: Build Failure

Error:

```text
zip: command not found
```

### Root Cause

The zip package was not installed in the CodeBuild environment.

### Solution

```bash
yum install -y zip
```

Added the command in the install phase.

<img width="1916" height="955" alt="Pipeline exe details" src="https://github.com/user-attachments/assets/2e858ba2-8853-4b6e-8b48-b3cb7b8cfd5d" />

---

### Issue 2: Lambda Deployment Failure

Error:

```text
ResourceNotFoundException
```

### Root Cause

Lambda function name mismatch.

Incorrect:

```text
hello_world
```

Correct:

```text
Hello_world
```

AWS Lambda function names are case-sensitive.

---

# Outcome

- Created an end-to-end CI/CD pipeline for AWS Lambda

- Automated deployment from GitHub to Lambda

- Learned how CodePipeline and CodeBuild interact

- Gained hands-on experience troubleshooting build and deployment issues

- Improved understanding of buildspec.yml and AWS deployment workflows

---

## Skills Practiced

* AWS Lambda
* AWS CodePipeline
* AWS CodeBuild
* Amazon S3
* Git & GitHub
* CI/CD Fundamentals
* Build Automation
* Troubleshooting & Debugging

---

### Conclusion

Every code change pushed to GitHub automatically triggers the pipeline and deploys the updated code to the Lambda function, eliminating the need for manual deployments.

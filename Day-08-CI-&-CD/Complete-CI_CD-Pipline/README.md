# AWS CI/CD Pipeline for Static Website Deployment

## Overview

This project demonstrates an end-to-end CI/CD pipeline on AWS for automatically deploying a static website hosted on Amazon S3.

The pipeline integrates GitHub, AWS CodePipeline, AWS CodeBuild, and Amazon S3 to automate the process of fetching source code, building the application, and deploying the latest version of the website.

## Architecture

<img width="993" height="629" alt="ChatGPT Image Jun 7, 2026, 08_29_47 PM" src="https://github.com/user-attachments/assets/26dad42c-c91f-441e-8156-544cc9f8c02c" />


## Services Used

* Amazon S3
* AWS CodePipeline
* AWS CodeBuild
* GitHub
* AWS IAM
* AWS CodeStar Connections

## Resources Created

### S3 Buckets

#### app-artifacts

Used by CodePipeline to store build and deployment artifacts.

#### app-destination

Used to host the static website and store deployment files.

<img width="1920" height="951" alt="app-destination bucket" src="https://github.com/user-attachments/assets/7b94ca09-4d58-4479-9b19-725751199885" />


## Workflow

### Step 1: Create S3 Buckets

Created two S3 buckets:

* app-artifacts
* app-destination

<img width="1918" height="945" alt="S3 buckets for website" src="https://github.com/user-attachments/assets/d83dd1de-f8f9-4c54-a4b9-c7a51cef7118" />

### Step 2: Create GitHub Repository

* Created a simple static website.
* Added project files to GitHub.
* Configured GitHub as the source repository.

<img width="1920" height="1071" alt="github repo" src="https://github.com/user-attachments/assets/b3522b49-9d57-4c16-80a7-b63ea4b4aabf" />


### Step 3: Configure GitHub Connection

* Created a GitHub connection using CodeStar Connections.
* Authorized AWS to access the repository.
* Connected GitHub with AWS services securely.

<img width="1920" height="945" alt="github connection " src="https://github.com/user-attachments/assets/e806b9b9-2c26-4727-9350-810505d8bde6" />


### Step 4: Create CodeBuild Project

Configured AWS CodeBuild to:

* Pull source code from the pipeline.
* Process build instructions.
* Generate deployment artifacts.

<img width="1918" height="945" alt="Screenshot from 2026-06-07 19-22-18" src="https://github.com/user-attachments/assets/fd7e0af9-1fbf-4087-9601-41a3281b29bd" />


### Step 5: Create CodePipeline

Configured a three-stage pipeline:

#### Source Stage

* GitHub Repository

#### Build Stage

* AWS CodeBuild

  <img width="1905" height="940" alt="app-codbuild" src="https://github.com/user-attachments/assets/c147bf92-c678-4361-b32e-422729070a8c" />


#### Deploy Stage

* Amazon S3


### Step 6: Deploy Website

Pipeline execution flow:

1. Code pushed to GitHub.
2. CodePipeline detects changes.
3. Source code is fetched.
4. CodeBuild processes the application.
5. Deployment artifacts are generated.
6. Files are deployed to the S3 bucket.

First Time Deployment (Before changes):

<img width="1901" height="1020" alt="wesite v0 0" src="https://github.com/user-attachments/assets/d6391d77-bf5f-47c6-ba6c-0edf8ff7346a" />


After Changes has been made:
Whenever code is pushed to GitHub, a webhook triggers CodePipeline. 
The pipeline fetches the latest source code, passes it to CodeBuild to generate build artifacts, and then automatically deploys the updated website to an S3 bucket hosting the static site.

<img width="1920" height="945" alt="Pipeline01" src="https://github.com/user-attachments/assets/a0bbdc3b-172c-44b1-a2fe-44bf41205c4e" />


<img width="1908" height="1005" alt="website v0 2" src="https://github.com/user-attachments/assets/7a0d75ae-e407-48b8-9c91-9b72dff84cb5" />


### Step 7: Verify Website

Successfully accessed the deployed static website through Amazon S3 hosting.


## Challenges Faced

### S3 Object Ownership and ACL Configuration

While configuring deployment, the pipeline encountered issues related to S3 Object Ownership settings and ACL restrictions. The issue was resolved by reviewing bucket permissions and deployment configuration.

### GitHub Trigger Configuration

Troubleshooting was required to understand automatic pipeline execution and GitHub integration.

## Key Learnings

* CI/CD fundamentals
* AWS CodePipeline
* AWS CodeBuild
* GitHub integration with AWS
* S3 static website hosting
* Artifact management
* IAM permissions
* S3 Object Ownership and ACLs
* Automated deployment workflows

## Outcome

Successfully built and deployed a static website using an automated CI/CD pipeline on AWS. The project provided hands-on experience with source control integration, build automation, artifact management, and deployment automation.


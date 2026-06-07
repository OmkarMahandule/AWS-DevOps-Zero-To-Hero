
# Day 8 - AWS CodeCommit

## Overview

Today, I explored AWS CodeCommit and its role in a CI/CD pipeline. AWS CodeCommit is a fully managed source control service that hosts private Git repositories in the AWS cloud.

In a typical CI/CD workflow, CodeCommit serves as the **Source Stage**, where developers store and manage application code before it moves through build, testing, and deployment stages.

---

## What is AWS CodeCommit?

AWS CodeCommit is a fully managed Git repository service that enables teams to securely store, version, and manage source code without maintaining their own Git servers.

It provides a centralized location for source code and integrates seamlessly with other AWS DevOps services.

### Features

- Fully managed Git repositories
- Secure code storage
- IAM-based access control
- Encryption at rest and in transit
- High availability and scalability
- Integration with AWS DevOps services

---

## Why Do We Need CodeCommit?

In modern software development, teams need a centralized repository to:

- Store source code
- Track changes and maintain version history
- Collaborate with team members
- Manage branches and merges
- Trigger automated CI/CD workflows

CodeCommit provides these capabilities while reducing the operational overhead of managing Git infrastructure.

---

## Role of CodeCommit in CI/CD

CodeCommit acts as the **Source Stage** of the CI/CD pipeline.

### CI/CD Flow

```text
Developer
    │
git push
    │
    ▼
CodeCommit
    │
    ▼
CodePipeline
    │
    ▼
CodeBuild
    │
    ▼
CodeDeploy
    │
    ▼
Production
```

### Workflow

1. A developer writes or modifies code locally.
2. Changes are committed using Git.
3. Code is pushed to the CodeCommit repository.
4. CodeCommit stores the latest version of the application.
5. CodePipeline detects the change.
6. The build, test, and deployment stages are triggered automatically.

---

## What Happens in the CodeCommit Stage?

### Step 1: Develop Code

The developer creates or updates application files locally.

### Step 2: Commit Changes

```bash
git add .
git commit -m "Added login feature"
```

### Step 3: Push Code

```bash
git push origin main
```

### Step 4: Store and Track Changes

CodeCommit records:

- Commit ID
- Author information
- Timestamp
- Modified files
- Branch information

  <img width="1920" height="927" alt="Screenshot from 2026-06-06 20-09-21" src="https://github.com/user-attachments/assets/16cdd8fa-52bf-4208-826c-3f19388184dc" />


### Step 5: Trigger the Pipeline

A successful push can trigger the next stages of the CI/CD pipeline, such as build, testing, and deployment.

---

## Common Git Commands Used with CodeCommit

### Clone Repository

```bash
git clone <repository-url>
```

### Check Status

```bash
git status
```

### Add Files

```bash
git add .
```

### Commit Changes

```bash
git commit -m "message"
```

### Push Changes

```bash
git push origin main
```

### Pull Latest Changes

```bash
git pull origin main
```

### Create a Branch

```bash
git checkout -b feature-branch
```

### Merge a Branch

```bash
git merge feature-branch
```

---

## Benefits of Using CodeCommit

- Fully managed Git repositories
- No Git server maintenance
- Fine-grained access control using IAM
- Secure and encrypted storage
- Easy integration with AWS CI/CD services
- Supports collaborative development workflows



---

## Key Takeaways

- AWS CodeCommit is a fully managed Git repository service.
- It serves as the Source Stage in an AWS CI/CD pipeline.
- Developers interact with CodeCommit using standard Git commands.
- CodeCommit integrates with CodePipeline, CodeBuild, and CodeDeploy.
- A code push to CodeCommit can automatically trigger the software delivery process.

---

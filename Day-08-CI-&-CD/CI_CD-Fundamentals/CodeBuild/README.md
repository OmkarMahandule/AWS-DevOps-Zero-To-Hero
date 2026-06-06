---

# AWS CodeBuild

## Overview

AWS CodeBuild is a fully managed, continuous integration build service that compiles source code, runs tests, and produces deployment-ready artifacts.

In a CI/CD pipeline, CodeBuild is responsible for transforming source code into a deployable application while ensuring that the code passes the required validation and testing processes.

---

## Why Do We Need CodeBuild?

Before an application can be deployed, it must be:

- Compiled (if required)
- Tested for quality and functionality
- Packaged into deployable artifacts
- Validated against project requirements

CodeBuild automates these tasks and ensures consistency across builds.

---

## Role of CodeBuild in CI/CD

CodeBuild serves as the **Build Stage** of the CI/CD pipeline.

```text
Developer
    │
git push
    │
    ▼
CodeCommit
(Source)
    │
    ▼
CodePipeline
(Orchestration)
    │
    ▼
CodeBuild
(Build & Test)
    │
    ▼
CodeDeploy
(Deployment)
    │
    ▼
Production
```

---

## What Happens Inside CodeBuild?

### Step 1: Source Code Retrieval

CodeBuild receives the latest source code from the Source Stage.

### Step 2: Environment Provisioning

AWS creates a temporary build environment based on the configuration provided.

<img width="1920" height="927" alt="Screenshot from 2026-06-06 21-54-47" src="https://github.com/user-attachments/assets/3d38e247-7218-47a8-8e0f-0b41d5d1ec14" />


### Step 3: Build Execution

The application is compiled or prepared for deployment.

<img width="1920" height="927" alt="Screenshot from 2026-06-06 21-56-35" src="https://github.com/user-attachments/assets/93ead841-80ec-4053-97cb-8e6070240883" />


Examples:

- Java → Generate JAR/WAR files
- Node.js → Install dependencies and build application
- Python → Package application files
- Docker → Build container images

### Step 4: Testing

Automated tests are executed.

Examples:

- Unit Testing
- Integration Testing
- Code Quality Checks

### Step 5: Artifact Generation

The build output is packaged into deployable artifacts.

Examples:

- JAR files
- WAR files
- ZIP packages
- Docker Images

### Step 6: Pass Artifacts to Next Stage

The generated artifacts are forwarded to CodeDeploy or another deployment service.

---

## Build Specification File

CodeBuild uses a `buildspec.yml` file to define build instructions.

### Example

```yaml
version: 0.2

phases:
  install:
    commands:
      - echo Installing dependencies

  build:
    commands:
      - echo Building application

  post_build:
    commands:
      - echo Build completed

artifacts:
  files:
    - '**/*'
```

The buildspec file tells CodeBuild what actions to perform during each stage of the build process.

<img width="1920" height="927" alt="image" src="https://github.com/user-attachments/assets/016625c0-d075-4291-9925-fa41a71db7a6" />


---

## Common Build Phases

### Install

Install required dependencies and tools.

### Pre-Build

Run setup tasks before the build starts.

### Build

Compile source code and create application packages.

### Post-Build

Execute final tasks after the build completes.

### Artifacts

Store files that will be used in later stages.

---

## Benefits of Using CodeBuild

- Fully managed build service
- No build server maintenance
- Automatic scaling
- Pay only for build time used
- Supports multiple programming languages
- Seamless integration with AWS services

---

## Key Takeaways

- CodeBuild is AWS's fully managed build service.
- It serves as the Build Stage in a CI/CD pipeline.
- It compiles code, runs tests, and creates deployable artifacts.
- It uses a `buildspec.yml` file to define build instructions.
- It integrates seamlessly with CodePipeline and CodeDeploy.
- It helps automate Continuous Integration processes.

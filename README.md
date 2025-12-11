# AWS CI/CD Pipeline — demo_cicd_ec2_AWS

This document describes the complete CI/CD pipeline implemented using **AWS CodePipeline**, **CodeBuild**, **ECR**, **EC2**, and **SSM RunCommand** for automated Docker deployments.

---

# 🚀 Architecture Overview

GitHub → CodePipeline → CodeBuild (Build) → ECR
↓
CodeBuild (Deploy)
↓
SSM RunCommand → EC2 → Docker

yaml
Copy code

Application runs at:

http://<EC2-PUBLIC-IP>:8080

yaml

---

# 🧩 AWS Services Used

- AWS CodePipeline — pipeline orchestrator  
- AWS CodeBuild — build and deploy stages  
- Amazon ECR — Docker image registry  
- Amazon EC2 — application runtime  
- AWS SSM RunCommand — remote command execution  
- IAM — permissions for services  

---

# 🔁 CI/CD Flow

### 1️⃣ CodePipeline Source  
Pulls code from GitHub via a CodeStar Connection.

### 2️⃣ Build Stage (CodeBuild)
- Build Docker image  
- Tag image as first 8 chars of commit SHA  
- Push to ECR  

### 3️⃣ Deploy Stage (CodeBuild)
- Trigger SSM RunCommand  
- EC2 executes deploy script  
- Pulls new image → Restarts container  

---

# 📂 File Structure (AWS-related)

buildspec-build.yml
buildspec-deploy.yml
scripts/
└── deploy_docker.sh

<img width="1437" height="494" alt="image" src="https://github.com/user-attachments/assets/a1c21df4-4b21-4531-b377-77b3dde932d1" />



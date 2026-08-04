<div align="center">

# 🚀 DevOps CI/CD Pipeline using Jenkins, Docker, SonarQube & AWS

### Automated CI/CD Pipeline with GitHub • Jenkins • SonarQube • Docker • Amazon ECR • AWS EC2

![GitHub](https://img.shields.io/badge/GitHub-Version%20Control-black?style=for-the-badge&logo=github)
![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-red?style=for-the-badge&logo=jenkins)
![Docker](https://img.shields.io/badge/Docker-Containers-blue?style=for-the-badge&logo=docker)
![SonarQube](https://img.shields.io/badge/SonarQube-Code%20Quality-4E9BCD?style=for-the-badge&logo=sonarqube)
![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)

</div>

---

# 📖 Project Overview

This project demonstrates an end-to-end DevOps CI/CD pipeline that automatically builds, analyzes, containerizes, and deploys an application using industry-standard DevOps tools.

The pipeline is automatically triggered whenever code is pushed to GitHub.

---

# 🏗 Architecture

```
                    GitHub Repository
                           │
                     Push Source Code
                           │
                           ▼
                  GitHub Webhook Trigger
                           │
                           ▼
                      Jenkins Pipeline
                           │
          ┌────────────────┼────────────────┐
          │                                 │
          ▼                                 ▼
   Checkout Source                 Verify Project Files
                           │
                           ▼
                    SonarQube Analysis
                           │
                           ▼
                 Build Docker Image
                           │
                           ▼
                  Login to Amazon ECR
                           │
                           ▼
                 Tag Docker Image
                           │
                           ▼
                Push Image to Amazon ECR
                           │
                           ▼
                  Verify Image in ECR
                           │
                           ▼
                  Deploy to AWS EC2
                           │
                           ▼
                 🌐 Live Application
```

---

# 🚀 Pipeline Workflow

✔ GitHub Source Code

⬇

✔ GitHub Webhook

⬇

✔ Jenkins Pipeline

⬇

✔ SonarQube Code Analysis

⬇

✔ Docker Image Build

⬇

✔ Amazon ECR Push

⬇

✔ AWS EC2 Deployment

---

# ⚙ Jenkins Pipeline Stages

- Checkout Source Code
- Verify Files
- SonarQube Scan
- Build Docker Image
- Login to Amazon ECR
- Tag Docker Image
- Push Docker Image
- Verify Image in ECR
- Deploy Application
- Post Build Actions

---

# 🛠 Tech Stack

| Category | Technologies |
|-----------|-------------|
| Version Control | Git, GitHub |
| CI/CD | Jenkins |
| Code Quality | SonarQube |
| Containerization | Docker |
| Container Registry | Amazon ECR |
| Cloud | AWS EC2 |
| Operating System | Linux |
| Scripting | Shell Script |
| Frontend | HTML, CSS |

---

# 📂 Project Structure

```
devops-portfolio/

│── Dockerfile
│── Jenkinsfile
│── sonar-project.properties
│── index.html
│── README.md
```

---

# 🔐 Jenkins Credentials

The following credentials are securely configured inside Jenkins.

- SonarQube Token
- AWS Access Key
- AWS Secret Access Key

---

# 📦 Docker

Build Image

```bash
docker build -t devops-portfolio .
```

Run Container

```bash
docker run -d -p 80:80 devops-portfolio
```

---

# ☁ Amazon ECR

Login

```bash
aws ecr get-login-password --region YOUR_REGION \
| docker login --username AWS --password-stdin YOUR_ECR_URL
```

Tag Image

```bash
docker tag devops-portfolio:latest YOUR_ECR_URL/devops-portfolio:latest
```

Push Image

```bash
docker push YOUR_ECR_URL/devops-portfolio:latest
```

---

# 🚀 Deployment

The application is deployed on an AWS EC2 instance after a successful pipeline execution.

Deployment Flow

```
GitHub
   │
   ▼
Jenkins
   │
   ▼
SonarQube
   │
   ▼
Docker
   │
   ▼
Amazon ECR
   │
   ▼
AWS EC2
```

---

# 📷 Project Screenshots

## 1️⃣ Application

```
images/application.png
```

---

## 2️⃣ Jenkins Pipeline

```
images/jenkins-pipeline.png
```

---

## 3️⃣ SonarQube Dashboard

```
images/sonarqube-dashboard.png
```

---

## 4️⃣ AWS EC2

```
images/aws-ec2.png
```

---

## 5️⃣ GitHub Repository

```
images/github.png
```

---

# ✨ Features

- Automated CI/CD Pipeline
- GitHub Webhook Integration
- Static Code Analysis
- Docker Image Creation
- Push Image to Amazon ECR
- Secure Jenkins Credentials
- AWS EC2 Deployment
- Continuous Integration
- Continuous Delivery

---

# 📈 Skills Demonstrated

- DevOps
- CI/CD
- Jenkins Pipelines
- Docker
- SonarQube
- AWS EC2
- Amazon ECR
- GitHub
- Linux
- Shell Scripting

---

# 👩‍💻 Author

**Divya Yelewar**

DevOps Engineer | AWS | Docker | Jenkins | Python | Linux

GitHub:
https://github.com/divyayelewar

LinkedIn:
(Add your LinkedIn Profile)

---

⭐ If you like this project, don't forget to star the repository!

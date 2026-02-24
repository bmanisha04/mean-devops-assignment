MEAN Stack CI/CD Deployment using Jenkins, Docker & Azure 
Project Overview
This project demonstrates a complete CI/CD pipeline for deploying a MEAN (MongoDB, Express, Angular, Node.js) application using modern DevOps practices.
The implementation includes:
CI/CD automation using Jenkins
Containerization using Docker
Image registry using Docker Hub
Cloud deployment on Microsoft Azure Virtual Machine
Reverse proxy configuration using Nginx
The pipeline automatically builds Docker images, pushes them to Docker Hub, and deploys the updated application to an Azure VM.

 Architecture
Developer → GitHub Push → Jenkins Pipeline →
Build Docker Images → Push to Docker Hub →
Azure VM pulls latest images → Docker Compose deploys containers →
Nginx Reverse Proxy → Application accessible via Port 80

 Prerequisites
Azure Virtual Machine (Ubuntu 22.04)
Docker & Docker Compose installed
Jenkins installed and configured
Docker Hub account
GitHub repository containing MEAN application source code

Step-by-Step Setup & Deployment
1️⃣ Azure VM Setup
An Ubuntu Virtual Machine was created on Microsoft Azure.
Docker and Docker Compose were installed on the VM to enable containerized deployment.
Required ports opened:
22 (SSH)
80 (HTTP)
8080 (Jenkins)
2️⃣ Jenkins Installation & Configuration
Jenkins was installed on the Azure VM.
After installation:
Required plugins were installed (Git, Pipeline, Docker Pipeline, Credentials Binding).
Docker Hub credentials were configured securely inside Jenkins.
SSH credentials were configured for deployment access.
A Pipeline job was created to automate:
Source code checkout
Docker image build
Image push to Docker Hub
Deployment on Azure VM
3️⃣ Dockerization
The application was containerized using Docker:
Backend Dockerfile created for Node.js + Express service.
Frontend Dockerfile created for Angular build served via Nginx.
MongoDB deployed as a container.
Docker Compose was used on the VM to orchestrate:
Frontend container
Backend container
MongoDB container
4️⃣ CI/CD Workflow
The Jenkins pipeline performs the following stages:
Pull latest code from GitHub
Build frontend and backend Docker images
Push images to Docker Hub
Pull latest images on Azure VM
Restart containers automatically
This ensures zero manual deployment effort after code changes.
5️⃣ Nginx Reverse Proxy
Nginx was configured on the Azure VM as a reverse proxy.
It routes incoming traffic from port 80 to the frontend container, making the application accessible without specifying a port number.
Application Access URL:
http://20.193.144.86

📸 Screenshots
## 📸 CI/CD Pipeline Execution
![Jenkins Pipeline](screenshots/jenkins-success.png)

## 🐳 Docker Image Build & Push
![DockerHub Frontend](screenshots/dockerhub-frontend.png)
![DockerHub Backend](screenshots/dockerhub-backend.png)

## 🚀 Application Deployment
![Docker PS](screenshots/docker-ps.png)

## 🌐 Working Application UI
![App Running](screenshots/app-running.png)

## 🔁 Nginx Configuration
![Nginx Config](screenshots/nginx-config.png)

🎯 Output

✔ Automatic build triggered on GitHub push
✔ Docker images successfully pushed to Docker Hub
✔ Containers deployed on Azure VM
✔ Application accessible via port 80
✔ Reverse proxy successfully configured

📌 Conclusion

This project demonstrates a complete end-to-end DevOps workflow including:

CI/CD automation

Containerized deployment

Cloud infrastructure setup

Reverse proxy configuration

Production-style deployment strategy

The infrastructure is kept active for live demonstration as required.

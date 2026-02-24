# MEAN Stack CI/CD Deployment using Jenkins, Docker & Azure

## Project Overview

This project shows deployment of a MEAN (MongoDB, Express, Angular, Node.js) application using a CI/CD pipeline.

The build and deployment process is automated using Jenkins and Docker, and the application is hosted on an Azure Virtual Machine.

Technologies used:
- Jenkins (CI/CD)
- Docker (containerization)
- Docker Hub (image registry)
- Microsoft Azure VM (cloud hosting)
- Nginx (reverse proxy)

---

## CI/CD Workflow

On every push to GitHub:

1. Jenkins pulls the latest source code  
2. Docker images for frontend and backend are built  
3. Images are pushed to Docker Hub  
4. Azure VM pulls updated images  
5. Containers are restarted using Docker Compose  

The deployment process runs automatically without manual steps.

---

## Azure Setup

- Ubuntu Virtual Machine created on Azure  
- Docker and Docker Compose installed  
- Jenkins installed and configured  
- Required ports opened: 22, 80, 8080  

---

## Application Containers

The application runs using three containers:

- Frontend (Angular)
- Backend (Node.js + Express)
- MongoDB

Docker Compose is used to manage and run all services together.

---

## Reverse Proxy Configuration

Nginx is configured as a reverse proxy.

Incoming traffic on port 80 is forwarded to the frontend container, allowing access without specifying a port number.

Application URL:

http://20.193.144.86

---

## Screenshots

### Jenkins Build Success
![Jenkins](screenshots/jenkins-success.png)

### Docker Hub Images
![Frontend](screenshots/dockerhub-frontend.png)
![Backend](screenshots/dockerhub-backend.png)

### Running Containers
![Docker PS](screenshots/docker-ps.png)

### Application UI
![App Running](screenshots/app-running.png)

### Nginx Configuration
![Nginx](screenshots/nginx-config.png)

---

## Result

- Automated build and deployment  
- Docker images pushed successfully  
- Containers running on Azure VM  
- Application accessible via port 80  
- Reverse proxy working correctly  

# Automated Deployment of Dockerized Application on AWS EC2 using GitHub Actions and Nginx

## Project Overview
This project demonstrates an end-to-end CI/CD pipeline for automatically deploying a Dockerized portfolio website on an AWS EC2 instance using GitHub Actions and Nginx Reverse Proxy.

Whenever code is pushed to the GitHub repository, GitHub Actions automatically:

1. Builds the Docker image.
2. Pushes the image to Docker Hub.
3. Connects to AWS EC2 through SSH.
4. Pulls the latest Docker image.
5. Deploys the container automatically.

---

## Architecture

Developer → GitHub Repository → GitHub Actions → Docker Hub → AWS EC2 → Docker Container → Nginx Reverse Proxy → Users

---

## Technologies Used

- AWS EC2 (Ubuntu)
- Docker
- Docker Hub
- GitHub Actions
- Nginx
- Linux (Ubuntu)
- SSH

---

## Project Structure

```bash
Portfolio-Website/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── Dockerfile
├── index.html
├── style.css
├── images/
└── README.md
```

---

## CI/CD Workflow

### Continuous Integration (CI)

- Source code is pushed to GitHub.
- GitHub Actions automatically triggers.
- Docker image is built.
- Image is pushed to Docker Hub.

### Continuous Deployment (CD)

- GitHub Actions connects to EC2 using SSH.
- Latest Docker image is pulled.
- Existing container is stopped and removed.
- New container is deployed automatically.

---

## GitHub Secrets Used

| Secret Name | Description |
|-------------|-------------|
| DOCKER_USERNAME | Docker Hub Username |
| DOCKER_PASSWORD | Docker Hub Password/Access Token |
| VM_HOST | AWS EC2 Public IP Address |
| VM_USER | Ubuntu User |
| VM_SSH_KEY | Private SSH Key |

---

## Docker Commands Used

### Build Docker Image

```bash
docker build -t jeeva0312/portfolio-website:latest .
```

### Push Docker Image

```bash
docker push jeeva0312/portfolio-website:latest
```

### Run Container

```bash
docker run -d --name app -p 8080:80 jeeva0312/portfolio-website:latest
```

---

## Nginx Reverse Proxy Configuration

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://localhost:8080;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

### Role of Nginx

- Acts as a Reverse Proxy.
- Routes traffic from Port 80 to Docker Container Port 8080.
- Improves security and professional deployment architecture.

---

## Deployment Steps

### Step 1
Launch Ubuntu EC2 Instance.

### Step 2
Install Docker and Nginx.

### Step 3
Create Docker Image.

### Step 4
Push Image to Docker Hub.

### Step 5
Configure GitHub Actions.

### Step 6
Configure SSH Authentication.

### Step 7
Push Code to GitHub.

### Step 8
Automatic Deployment to AWS EC2.

---

## Expected Output

- Automatic Docker Image Build
- Automatic Deployment to AWS EC2
- Containerized Portfolio Website
- Production-Style Hosting using Nginx
- End-to-End CI/CD Pipeline

---

## Learning Outcomes

- Docker Containerization
- GitHub Actions CI/CD
- AWS EC2 Deployment
- SSH-based Deployment
- Nginx Reverse Proxy Configuration
- DevOps Automation Concepts

---

## Author

**G K Jeeva**

GitHub: https://github.com/gkjeeva12
Docker Hub: https://hub.docker.com/u/jeeva0312

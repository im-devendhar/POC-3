

# POC-3

## 🚀 Project Deployment Guide on AWS EC2

This guide explains how to deploy your project using **Git**, **Jenkins**, and **Docker** on an AWS EC2 instance.

---

## 🛠️ Prerequisites

- AWS EC2 instance (Ubuntu is recommended)
- SSH access to the EC2 instance
- Internet connectivity

---

## 📦 Installation Steps

### 1. Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
```

### 2. Install Git
```bash
sudo apt install git -y
```

### 3. Install Java (required for Jenkins)
```bash
sudo apt install openjdk-17-jdk -y

```

### 4. Install Jenkins
```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### 5. Install Docker
```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
newgrp docker


- `Dockerfile`: Defines how to build the Docker image.
- `Jenkinsfile`: Contains CI/CD pipeline instructions.

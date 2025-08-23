

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
### 3. Install Docker
```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu
newgrp docker
```

## 🚀 Jenkins and Java Installation Guide (Ubuntu 24.04 Noble)

This guide walks you through installing **OpenJDK 17** and **Jenkins** on Ubuntu 24.04, including fixing GPG key issues and enabling the Jenkins service.

---

### 🔧 Step 1: Install Java (OpenJDK 17)

Jenkins requires Java to run. Install OpenJDK 17:

```bash
sudo apt update
sudo apt install openjdk-17-jre -y
java --version
```

---

### 🔐 Step 2: Add Jenkins Repository and GPG Key

Fix the GPG key issue and add the Jenkins repository:

```bash
# Download the updated Jenkins GPG key
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

# Add Jenkins repository
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | \
  sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
```

---

### 📦 Step 3: Install Jenkins

```bash
sudo apt update
sudo apt install jenkins -y
```

---

### ▶️ Step 4: Start and Enable Jenkins Service

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins

Add Jenkins user to the Docker group

sudo usermod -aG docker jenkins


Restart Jenkins service

sudo systemctl restart jenkins


Restart Docker service (optional but recommended)

sudo systemctl restart docker


Verify Jenkins user can run Docker

sudo su - jenkins
docker ps
```

---

### 🌐 Step 5: Access Jenkins Web Interface

Open your browser and go to:

```
http://<your-server-ip>:8080
```

To retrieve the initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
# Jenkins Setup for This Project

To build and deploy this project using Jenkins, make sure you have the following plugins installed:

### ✅ Required Plugins

1. **Pipeline Plugin** – Allows Jenkins to read and run the `Jenkinsfile`.
2. **Git Plugin** – For pulling this repository into Jenkins.
3. **Docker Pipeline Plugin** – Enables `docker.build()` and `docker.run()` steps in the pipeline.
4. **Credentials Binding Plugin** – For securely storing DockerHub or GitHub credentials if pushing images.




- `Dockerfile`: Defines how to build the Docker image.
- `Jenkinsfile`: Contains CI/CD pipeline instructions.

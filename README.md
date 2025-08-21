# POC-3

🚀 Project Deployment Guide on AWS EC2
This guide explains how to deploy your project using Git, Jenkins, and Docker on an AWS EC2 instance.

🛠️ Prerequisites
AWS EC2 instance (Ubuntu is recommended)
SSH access to the EC2 instance
Internet connectivity
📦 Installation Steps
1. Update System Packages
   -- sudo apt update && sudo apt upgrade -y

2. Install Git
   -- sudo apt install git -y

3. Install Java (required for Jenkins)
   -- sudo apt install openjdk-11-jdk -y

4. Install Jenkins
   -- wget -q -O - https update
   -- sudo apt install jenkins -y
   -- sudo systemctl start jenkins
   -- sudo systemctl enable jenkins


6. Install Docker
   -- sudo apt install docker.io -y
   -- sudo systemctl start docker
   -- sudo systemctl enable docker
   -- sudo usermod -aG docker $USER

🔄 Deployment Flow
Code Commit: Push your code to a Git repository.
Build & Test: Jenkins pulls the code and runs the pipeline defined in Jenkinsfile.
Deploy: Jenkins uses Docker to build the image from Dockerfile and deploy the container.
📁 Project Files
Dockerfile: Defines how to build the Docker image.
Jenkinsfile: Contains CI/CD pipeline instructions.


🚀 Complete CI/CD Pipeline using Jenkins, Git, Maven, Ansible, Docker, and Tomcat

This project demonstrates a robust end-to-end CI/CD pipeline with Jenkins that automates the process of pulling source code, building it with Maven, transferring the artifact using SSH, and deploying it inside a Docker container running Tomcat.

📸 Project Overview

✅ Jenkins Build Pipeline View

A clear multistage Jenkins pipeline with the following stages:

pullmycode – Clone source from GitHub

buildmycode – Build the project using Maven

transfercodetodeploy – Send .war and Dockerfile to the deployment server

deploywartocontainer – Ansible triggers Docker container deployment



💠 Tools & Technologies Used

Tool

Purpose

Jenkins

CI/CD automation

Git

Source code version control

Maven

Java project build tool

Ansible

Configuration management and deployment

Docker

Containerization

Tomcat

Java web application server

Amazon Linux 2

Base OS for all EC2 instances

🧱 Pipeline Structure

🔹 pullmycode

Jenkins pulls the source code from a GitHub repository (https://github.com/hackwithabhi1/devpro2024.git).

🔹 buildmycode

Maven builds the code and generates a .war file inside target/ directory.

🔹 transfercodetodeploy

Jenkins uses the Publish over SSH plugin to:

Copy the webapp.war file

Copy the Dockerfile

Send both to the /opt/docker/ directory on the remote Ansible/Docker node.

🔹 deploywartocontainer

Jenkins executes an Ansible playbook create-docker-container.yml that:

Installs Docker

Builds a Docker image from the Dockerfile

Deploys the .war inside a Tomcat container

Maps container port 8080 to host port 80

🔐 Jenkins Plugin Configuration

Publish over SSH plugin configured with:

Remote host IP and SSH credentials (itadmin)

Remote path: /opt/docker

Post-build script to run Ansible playbook.

📂 Ansible Playbook Overview (create-docker-container.yml)

- name: Create Docker container for WAR deployment
  hosts: all
  become: true
  tasks:
    - name: Install and start Docker
      ...
    - name: Copy WAR and Dockerfile
      ...
    - name: Build Docker image and run container
      ...

🌐 Deployment Verification

Docker container running on port 80

WAR application deployed inside the containerized Tomcat instance

📍 Example:

# On Docker host
docker ps
docker images

🔗 Access web app:

http://<docker-node-ip>/webapp

📂 Deployment UI (Tomcat Manager & Jenkins)

🥈 Tomcat Manager showing Jenkins deployed:



✅ Final Results

Code is built and deployed in seconds.

Fully automated process using Jenkins + Ansible + Docker + Tomcat.

Clean pipeline stages with traceable logs and success indicators.

## 🔗 Sample Application

GitHub Repo (used in pipeline):  
➡️ [`CICD.git`](https://github.com/Nandani1806pandey/CICD)

DockerHub Repo:  
➡️ [`181071/registerpro`](https://hub.docker.com/repository/docker/181071/registerpro)

---
## 📸 Screenshots (Optional)

_Add screenshots of your Jenkins job, DockerHub image, Tomcat._
![Screenshot 2025-05-31 204922](https://github.com/user-attachments/assets/a5e01cd4-2eb8-406b-8ef0-fb52965d7a2c)
![Screenshot 2025-05-30 172952](https://github.com/user-attachments/assets/392d6603-3db4-4086-90a1-87551093c695)
![Screenshot 2025-05-30 101418](https://github.com/user-attachments/assets/5d4fa22b-8c59-496b-b83e-113df3dff63a)

---


📁 Folder Structure

📆 devpro2024
 ├️ 📜 Dockerfile
 ├️ 📁 webapp
 ┃ └️ 📜 webapp.war
 ├️ 📜 create-docker-container.yml
 └️ 📄 README.md

🙌 Author

Nandani PandeyDevOps & Cloud Enthusiast  | CI/CD | Docker | Kubernetes | AWS  
📧 [Email](nandani1806pandey@gmail.com)  
🔗 [LinkedIn](www.linkedin.com/in/nandani-pandey-485a58328)

---



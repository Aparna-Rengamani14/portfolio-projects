Dockerized vProfile Application Deployment using Vagrant
This repository demonstrates end-to-end deployment of the vProfile multi-tier application using Vagrant + VirtualBox and Docker Compose.
The goal of this project is to showcase how a complete application stack can be provisioned automatically on a local VM and deployed using containerization.
This project is ideal for:
	• DevOps beginners
	• Interview demonstrations
	• Understanding Infrastructure + Application automation together

🏗️ Architecture Overview
The vProfile application follows a multi-tier architecture:
	• Web Tier – Frontend web server (Nginx/Apache)
	• App Tier – Java application running on Tomcat
	• DB Tier – MySQL database
	• Cache Tier – Memcached
	• Messaging Tier – RabbitMQ
All components run as separate Docker containers, orchestrated using Docker Compose, inside a Vagrant-managed Ubuntu VM.
Browser
   ↓
Web Container (vproweb :80)
   ↓
App Container (vproapp :8080)
   ↓
---------------------------------
| MySQL | Memcached | RabbitMQ |
---------------------------------


🧰 Tools & Technologies Used
	• Vagrant – VM lifecycle management
	• VirtualBox – VM provider
	• Ubuntu 20.04 (Focal) – Guest OS
	• Docker Engine – Container runtime
	• Docker Compose – Multi-container orchestration
	• MySQL – Database
	• Memcached – Caching
	• RabbitMQ – Message broker
	• Tomcat – Application server

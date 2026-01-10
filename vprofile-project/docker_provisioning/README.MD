# Dockerized vProfile Application Deployment using Vagrant

This repository demonstrates **end-to-end deployment** of the **vProfile multi-tier application** using **Vagrant + VirtualBox** and **Docker Compose**.

The goal of this project is to showcase how a **complete application stack** can be provisioned automatically on a local VM and deployed using **containerization**.
 

---

## Architecture Overview

The vProfile application follows a **multi-tier architecture**:

- **Web Tier** – Frontend web server (Nginx / Apache)  
- **App Tier** – Java application running on Tomcat  
- **DB Tier** – MySQL database  
- **Cache Tier** – Memcached  
- **Messaging Tier** – RabbitMQ  

All components run as **separate Docker containers**, orchestrated using **Docker Compose**, inside a **Vagrant-managed Ubuntu VM**.

### Request Flow
Browser -> Web Container (vproweb :80) -> App Container (vproapp :8080) -> | MySQL | Memcached | RabbitMQ |



## Tools & Technologies Used

- **Vagrant** – VM lifecycle management  
- **VirtualBox** – VM provider  
- **Ubuntu 20.04 (Focal)** – Guest OS  
- **Docker Engine** – Container runtime  
- **Docker Compose** – Multi-container orchestration  
- **MySQL** – Database  
- **Memcached** – Caching  
- **RabbitMQ** – Message broker  
- **Tomcat** – Application server  

## Deployment Flow

1. Vagrant creates an Ubuntu VM  
2. VM is provisioned with Docker & Docker Compose  
3. Docker Compose pulls required images  
4. All application services start automatically  
5. Application becomes accessible from the host browser  

---

## Vagrant Configuration Summary

The `Vagrantfile` performs the following:

- Uses `ubuntu/focal64` base box  
- Allocates **2 GB RAM** to the VM  
- Configures networking:
  - **Private Network:** `192.168.56.82`
  - **Public (Bridged) Network**
- Installs Docker components:
  - Docker Engine  
  - Docker CLI  
  - Containerd  
  - Docker Buildx  
  - Docker Compose  

Provisioning is done using an **inline shell provisioner**, making the setup fully automated.

---

## Docker Compose Services Explained

### MySQL Database – `vprodb`
- Image: `vprocontainers/vprofiledb`
- Port: `3306`
- Persistent storage using named volume `vprodbdata`
- Root password configured via environment variables

### Cache – `vprocache01`
- Image: `memcached`
- Port: `11211`
- Acts as a caching layer for MySQL to improve performance and reduce database load

### Message Queue – `vpromq01`
- Image: `rabbitmq`
- Port: `15672` (Management UI)
- Used for asynchronous messaging between application components

### Application Server – `vproapp`
- Image: `vprocontainers/vprofileapp`
- Runs Java application on Tomcat
- Port: `8080`
- Uses named volume `vproappdata` for application files

### Web Server – `vproweb`
- Image: `vprocontainers/vprofileweb`
- Port: `80`
- Acts as frontend and reverse proxy for the application

---

## Volumes Used

| Volume Name   | Used By | Purpose |
|--------------|--------|---------|
| vprodbdata   | MySQL  | Database persistence |
| vproappdata  | App    | Application data |

---

## How to Run This Project

### Prerequisites
- Vagrant installed  
- VirtualBox installed  

### Step 1: Clone the Repository
```bash
git clone <your-repo-url>
cd <repo-directory>
```

### Key Learning Outcomes:

- Infrastructure provisioning with Vagrant
- Automated VM setup using shell provisioning
- Docker containerization of multi-tier applications
- Docker Compose networking & volumes
- Real-world DevOps deployment workflow





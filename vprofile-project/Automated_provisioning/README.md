## Multi-Tier Application using Vagrant

This project provisions a multi-tier application environment using Vagrant.
It includes separate virtual machines for web, application, database,
cache, and messaging layers. It uses hostmanager for hostname resolution, VirtualBox as the provider, private networking for inter-VM communication, 
and shell provisioning for automatic service setup during vagrant up.


## Prerequisites
- Vagrant
- VirtualBox
- Git
- Minimum 8 GB RAM recommended


## Architecture
- Web Server: Nginx
- Application Server: Tomcat
- Database: MySQL
- Cache: Memcached
- Message Broker: RabbitMQ


## Component Overview
- **Nginx**
  Acts as a load balancer and entry point to the application.
  Routes incoming requests to the Tomcat application server.
  
- **Apache Tomcat**
  Java web application server where the application is deployed.
  Handles business logic and user requests.

- **MySQL**
  Stores persistent application data such as user login credentials.

- **Memcached**
  Acts as an in-memory cache for MySQL query results to reduce database load and improve response time.

- **RabbitMQ**
  Message broker included to simulate inter-service communication
  and increase system complexity.


## Application workflow

1. The user opens a browser and enters the IP address of the load balancer.
   In this project, a DNS-based URL is not used; instead, the application
   is accessed directly via the load balancer IP address.

2. Nginx is used as the load balancer in this setup.
   It receives incoming HTTP requests and forwards them to the backend
   application server based on the configured routing rules.

3. Apache Tomcat acts as the application server.
   It hosts the Java-based web application where the core business logic
   resides. If the application needs external storage, NFS storage can be used.

4. User authentication and login details are stored in a MySQL database.
   Tomcat communicates with the MySQL server to validate user credentials.

5. Memcached is used as a database cache.
   - When a login request is received for the first time, Tomcat fetches
     the data from the MySQL database and stores it in Memcached.
   - For subsequent requests with the same data, Tomcat retrieves the
     information directly from Memcached, reducing database load and
     improving performance.

6. RabbitMQ is included as a messaging service.
   In this project, it serves as a dummy component to increase architectural
   complexity and demonstrate how a message broker can be integrated to
   enable asynchronous communication between applications.


## Project Structure
.
├── Vagrantfile
├── mysql.sh
├── memcache.sh
├── rabbitmq.sh
├── tomcat.sh
├── nginx.sh
├── architecture ├── architecture.png
└── application.properties


## Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/project-name.git
   cd project-name
2. Start the environment
   ```bash
   vagrant up
4. SSH into a VM
   ```bash
   vagrant ssh db01
6. For Destroying the setup
   ```bash
   vagrant destroy -f


## VM Details

<img width="858" height="231" alt="image" src="https://github.com/user-attachments/assets/2ebdd5e2-6e0a-4c68-bde7-28199a9d9369" />

<br>
</br>

## DevOps Concepts Covered
1. Infrastructure as Code
2. Reverse proxy
3. Automated provisioning
4. Multi-tier architecture

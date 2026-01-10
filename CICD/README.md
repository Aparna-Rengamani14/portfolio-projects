## CI/CD Pipeline for Java(Maven) Application using Jenkins

This project demonstrates a **fully automated CI/CD pipeline** built using **Jenkins** for a Java (Maven) application.  
The pipeline covers **build, testing, code quality analysis, artifact management, containerization, and notifications**.

This project is designed to showcase **real-world DevOps practices** 

---

##  Project Overview

The pipeline automates the following workflow:

1. Fetches source code from Git
2. Builds the Java application using Maven
3. Runs unit and integration tests
4. Performs static code analysis (Checkstyle & SonarQube)
5. Enforces SonarQube quality gates
6. Publishes versioned artifacts to Nexus Repository
7. Builds and pushes Docker images (if Dockerfile exists)
8. Sends success/failure notifications
9. Cleans Jenkins workspace

---

## Tools & Technologies Used

| Category | Tools |
|-------|------|
| CI/CD | Jenkins |
| Build Tool | Maven |
| Code Quality | Checkstyle, SonarQube |
| Artifact Repository | Nexus Repository Manager |
| Containerization | Docker |
| Notifications | Email |
| Version Control | Git |

---

## Repository Structure

```text
.
├── Jenkinsfile          # Declarative Jenkins CI/CD pipeline
├── Dockerfile           # Docker image definition (optional)
├── pom.xml              # Maven project configuration
├── src/                 # Application source code
└── README.md            # Project documentation

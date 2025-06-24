
## README for EC2BuildServerSetup

```markdown
# EC2 Build Server Setup for Spring Boot Docker Builds

This repository contains the configuration for an AWS EC2 build server running Docker, Maven, and Java 17. It supports the build and containerization of a Spring Boot application for Kubernetes deployment, forming a critical part of a real-world DevOps pipeline.

## Project Overview
- **Purpose**: Facilitates the build and containerization of a Spring Boot app using an EC2 server.
- **Integration**: Works with the [Spring Boot app repo](https://github.com/VinodKumarDhanavath/SpringBootKubernetesApp) for application development and deployment.
- **Environment**: AWS EC2 instance with pre-installed Docker, Maven, and Java 17.
- **Outcome**: Pushes Docker images (`vinod1089/spring-boot-app:latest` and `fix3.4.5`) to Docker Hub for deployment on Google Kubernetes Engine (GKE).

## Key Files
- Configuration scripts or setup instructions for Docker, Maven, and Java 17 (if applicable).
- [Add specific files if available, e.g., EC2 setup scripts, Docker configs]

## Setup Instructions
1. **Prerequisites**:
   - AWS EC2 instance with Docker, Maven, and Java 17.
   - Docker Hub account and credentials.
2. **Launch EC2 Instance**:
   - Use an AMI with Docker, Maven, and Java 17 pre-installed.
   - Configure security groups for SSH (port 22).
3. **Set Up Build Environment**:
   - SSH into the EC2 instance:
     ```bash
     ssh -i <key.pem> ec2-user@<EC2-IP>
     ```
   - Clone the Spring Boot app repo:
     ```bash
     git clone https://github.com/VinodKumarDhanavath/SpringBootKubernetesApp
     ```
   - Install dependencies if needed: But all these are available in the repo.
     ```bash
     sudo yum install docker maven java-17-openjdk
     ```
4. **Build and Push Docker Images**:
   - Build the app:
     ```bash
     mvn clean package
     ```
   - Build and push images:
     ```bash
     docker build -t vinod1089/spring-boot-app:latest .
     docker login
     docker push vinod1089/spring-boot-app:latest
     ```
     Repeat for `fix3.4.5`.
5. **Deploy**:
   - Use the pushed images for GKE deployment (see app repo).

## Achievements
- Streamlined the build and containerization process on EC2, supporting a secure DevOps pipeline.
- Enabled the creation of secure Docker images for Kubernetes deployment.
- Integrated with Snyk for vulnerability scanning (see app repo).

## Related Repository
- [Spring Boot App](https://github.com/VinodKumarDhanavath/SpringBootKubernetesApp): Application code and Kubernetes configuration.

## Learn More
Check out my [project report]([https://drive.google.com/drive/folders/1x491xO3BcEop-Yp4IcHtM4xdf7mY9b22?usp=sharing]) for detailed documentation, screenshots (e.g., Snyk results, `kubectl` outputs), and visualizations.

**Author**: Vinod Kumar Dhanavath  
**Portfolio**: [Insert portfolio link, if applicable]  
**LinkedIn**: [Insert LinkedIn profile link, if desired]

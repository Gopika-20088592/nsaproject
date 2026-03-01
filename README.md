**Automated Container Deployment and Administration in the Cloud**

**Project Overview**
This project demonstrates how cloud infrastructure and application deployment can be fully automated using modern DevOps tools.
The main goal of this project is to automatically create a cloud server, configure it, deploy a web application inside a Docker container, and update the application automatically whenever new code is pushed to GitHub.
Instead of manually setting up servers and installing software step-by-step, everything in this project is done using automation scripts.

**Student Details**

**Student Name:** Gopika Kattikoloth Manoharan

**Student ID:** 20088592

**Course:** MSc Information Systems with Computing

**Module:** Network Systems and Administration (B9IS121)

**Instructor:** Kingsley Ibomo

**Technologies Used**

The project combines multiple DevOps tools working together:

•	AWS EC2 – Cloud server hosting

•	Terraform – Infrastructure provisioning

•	Ansible – Server configuration

•	Docker – Application containerization

•	GitHub Actions – CI/CD pipeline automation

**Project Architecture**

**1.	Terraform Layer**
o	Creates AWS infrastructure

o	Launches EC2 instance

o	Configures security groups

**3.	Ansible Layer**
o	Connects to EC2 using SSH

o	Installs Docker

o	Configures system environment

o	Deploys application files

**5.	Docker Layer**
o	Builds container image

o	Runs web application inside container

**7.	CI/CD Layer (GitHub Actions)**
o	Automatically validates code

o	Builds application

o	Deploys updates after every push

**Repository Structure**

nsaproject/

├──. github/workflows/

 └── main.yml   - Controls CI/CD pipeline automation

├── ansible/

  ├── inventory   - Fetch EC2 host details
  
  └── playbook.yml    - Server configuration

├── app/

  ├── Dockerfile    - Web containerisation 
  
  └── index.html    - Sample web application

├── terraform/

│   ├── main.tf    - Details of Infrastructure resources

│   ├── variables.tf     - Variables

│   ├── output.tf        - Outputs

│   └── .terraform.lock.hcl – automatically created by Terraform

│

└── .gitignore – Keep sensitive Terraform state file safe

**Automation Workflow**

**Step 1 — Infrastructure Creation (Terraform)**

Terraform automatically:

•	Connects to AWS

•	Creates a security group

•	Allows SSH (22) and HTTP (80)

•	Launches an Amazon Linux EC2 instance

**Command Used:**

terraform init

terraform apply

**Step 2 — Server Configuration (Ansible)**

Ansible prepares the server by:

•	Installing Docker

•	Starting Docker service

•	Enabling Docker on boot

•	Creating application directory

•	Deploying application files

**Run using:**

ansible-playbook -i inventory playbook.yml

**Step 3 — Docker Deployment**

Docker builds and runs the application:

•	Uses nginx:latest image

•	Copies custom webpage

•	Exposes port 80

The application becomes accessible through the EC2 public IP.

**Step 4 — CI/CD Pipeline (GitHub Actions)**

Whenever code is pushed to the main branch:

1.	Terraform configuration is validated
3.	Ansible syntax is checked
4.	Dockerfile existence is verified
5.	Pipeline connects to EC2 using SSH
6.	Latest code is pulled
7.	Docker image rebuilds automatically
8.	Old container is replaced with new version
This ensures continuous deployment without manual work.

**How to Access the Application**

1.	Deploy infrastructure using Terraform.
2.	Run Ansible playbook.
3.	Open browser and enter: **http://44.200.243.162**
   
You will see the deployed web application.

**Security Configuration**

•	Port 22 → SSH access

•	Port 80 → Web application access

•	Outbound traffic allowed for updates and downloads

Sensitive files such as Terraform state and private keys are excluded using .gitignore.

**Challenges Faced**

Some challenges during development included:

•	SSH connection issues due to security group rules

•	Docker permission errors

•	YAML syntax mistakes in automation scripts

•	Managing Terraform state securely

These problems helped improve understanding of cloud networking and automation workflows.

**What I learned:**

1. How Infrastructure as Code works
2. Automating server configuration
3. Containerizing applications using Docker
4. Implementing CI/CD pipelines
5. Integrating multiple DevOps tools together

**Future Improvements**

1. Adding HTTPS with SSL certificates
2. Restricting SSH access to specific IP ranges
3. Using Load Balancer and Auto Scaling
4. Using AWS IAM roles for stronger security

**Conclusion**
This project successfully demonstrates a fully automated cloud deployment system. By combining Terraform, Ansible, Docker, and GitHub Actions, the entire process from infrastructure creation to application deployment — runs automatically.
Automation reduces manual errors, improves consistency, and reflects real-world DevOps practices used in modern IT environments.

GitHub Repository

Project Repository:
https://github.com/Gopika-20088592/nsaproject

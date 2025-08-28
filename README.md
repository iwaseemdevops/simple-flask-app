# Automated CI/CD Pipeline for a Dockerized Flask App on AWS

## 📖 Overview
This project demonstrates a complete, automated **CI/CD (Continuous Integration & Continuous Deployment) pipeline** built using Jenkins, Docker, and Terraform on AWS. The pipeline automatically builds, security-scans, and deploys a containerized Python Flask application upon every code commit to the main branch, embodying core DevOps and DevSecOps principles.

## 🖼️ Architecture Diagram
![Architecture Diagram](https://github.com/YOUR_USERNAME/simple-flask-app/raw/main/images/architecture-diagram.png) *(You will create this)*

**Flow:**
1.  **Developer** pushes code to GitHub.
2.  **Jenkins** server detects the change via webhook.
3.  **Jenkins pipeline** executes:
    *   **Stage 1:** Checks out the source code.
    *   **Stage 2:** Builds a new Docker image.
    *   **Stage 3:** Scans the image for critical vulnerabilities using Trivy.
    *   **Stage 4:** If scan passes, deploys the new container; if it fails, the pipeline stops.
4.  The updated application is live on the AWS EC2 instance.

## 🛠️ Technologies Used

| Category | Tools |
| :--- | :--- |
| **Infrastructure as Code** | Terraform |
| **Cloud Provider** | AWS (EC2, VPC, IAM, Security Groups) |
| **CI/CD Server** | Jenkins |
| **Containerization** | Docker |
| **Security** | Trivy |
| **Source Control** | Git, GitHub |
| **Programming** | Python, Flask |

## 🚀 Features
- **Full Automation:** End-to-end automation from code commit to production deployment.
- **Infrastructure as Code:** Entire AWS infrastructure is defined and version-controlled in Terraform.
- **Security "Shifted Left":** Automated security scanning (SAST) is integrated into the pipeline, failing builds on critical vulnerabilities.
- **Containerization:** Application is consistently packaged using Docker, ensuring it runs identically in all environments.

## 📸 Screenshots

| Description | Screenshot |
| :--- | :--- |
| **Successful Jenkins Pipeline Run** | ![Pipeline](https://github.com/YOUR_USERNAME/simple-flask-app/raw/main/images/pipeline-success.png) |
| **Trivy Security Scan Results** | ![Trivy](https://github.com/YOUR_USERNAME/simple-flask-app/raw/main/images/trivy-scan.png) |
| **Live Application** | ![Live App](https://github.com/YOUR_USERNAME/simple-flask-app/raw/main/images/live-app.png) |

## 🏁 Getting Started / How to Run

### Prerequisites
- AWS Account
- Terraform installed locally
- Git

### Deployment Instructions
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/YOUR_USERNAME/simple-flask-app.git
    cd simple-flask-app
    ```
2.  **Provision Infrastructure:**
    ```bash
    cd terraform/
    terraform init
    terraform apply -auto-approve
    ```
3.  **Access Jenkins:** Navigate to `http://<EC2_PUBLIC_IP>:8080` and complete the setup using the admin password retrieved via `sudo cat /var/lib/jenkins/secrets/initialAdminPassword` on the server.
4.  **Create the Jenkins Pipeline Job:** Create a new Pipeline job in Jenkins, point it to this GitHub repository, and run it.

### Destroy Infrastructure
To avoid AWS charges, destroy all resources after testing:
```bash
terraform destroy -auto-approve

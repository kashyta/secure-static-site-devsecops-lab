#  Secure Static Site DevSecOps Lab

This project demonstrates a cloud-native DevSecOps pipeline for deploying a secure static website on AWS using Terraform. It integrates automated security scanning tools and GitHub Actions to ensure infrastructure and code remain secure throughout the development lifecycle.

---

##  Infrastructure Overview

- **AWS EC2**: Used for manual testing and tool installation
- **AWS S3**: Hosts the static website
- **IAM Roles**: Configured for least privilege access
- **Terraform**: Manages infrastructure as code

---

## DevSecOps Pipeline

Security tools are integrated via GitHub Actions to run on every push and pull request:

| Tool      | Purpose                                  |
|-----------|------------------------------------------|
| Trivy     | Scans filesystem and IaC for vulnerabilities and misconfigurations |
| Semgrep   | Performs static code analysis to catch insecure patterns |
| GitLeaks  | Detects hardcoded secrets and credentials |

Scan reports are saved in the `scans/` folder with timestamps and uploaded as GitHub Action artifacts.

---

##  Folder Structure

secure-static-site-devsecops-lab/ 
├── scans/ # Timestamped scan reports 
├── infrastructure/ # Terraform modules 
    ├── ec2-instance/ 
    ├── s3-static-site/ 
    ├── iam-roles/
├── website
    └── index.html
    └── error.html
├── .github/ 
   └── workflows/ 
     └── devsecops.yml # GitHub Actions pipeline 
├── install-tools.sh # Manual tool installer (optional) 
├── .gitignore # Excludes Terraform state and secrets 
├── SECURITY.md # Explains how each tool protects the project 
├── README.md # You're reading it! 



---

## Setup Instructions

1. Clone the repo:
   ```bash
   git clone https://github.com/your-username/secure-static-site-devsecops-lab.git
   cd secure-static-site-devsecops-lab

2. Initialize Terraform:

    terraform init
    terraform apply

3. Push code to GitHub to trigger scans:

    git add .
    git commit -m "Initial commit"
    git push origin main

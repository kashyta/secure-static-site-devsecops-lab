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

Scan reports are saved with timestamps and uploaded as GitHub Action artifacts.

---

##  Folder Structure

```text
secure-static-site-devsecops-lab/
├── website                 # HTML pages and images for static website 
├── infrastructure/         # Terraform modules
│   ├── ec2-instance/       # EC2 setup for manual testing
│   ├── s3-static-site/     # S3 bucket hosting static site
│   ├── iam-roles/          # IAM roles and policies
├── .github/
│   └── workflows/
│       └── devsecops.yml   # GitHub Actions pipeline
├── install-tools.sh        # Optional script for manual tool installation
├── .gitignore              # Excludes Terraform state, secrets, and large files
├── SECURITY.md             # Explains how each tool protects the project
├── README.md               # Project overview and setup instructions
```

---

##  Setup Instructions

1. Clone the repo:
   ```bash
   git clone https://github.com/your-username/secure-static-site-devsecops-lab.git
   cd secure-static-site-devsecops-lab

2. Initialize Terraform:
    ```bash
    terraform init
    terraform apply

3. Push code to GitHub to trigger scans:
    ```bash
    git add .
    git commit -m "Initial commit"
    git push origin main

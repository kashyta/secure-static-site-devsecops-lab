# Security Overview

This project integrates automated security scanning tools to ensure infrastructure-as-code (IaC), application logic, and version control remain secure and compliant. The following tools are used in our GitHub Actions workflow:

---

## Trivy – Vulnerability Scanner

**Purpose:**  
Trivy scans the filesystem, containers, and IaC (Terraform, Dockerfiles, etc.) for known vulnerabilities (CVEs), misconfigurations, and exposed secrets.

**How It Protects:**
- Detects OS and library vulnerabilities in dependencies
- Flags insecure configurations in Terraform files
- Identifies exposed secrets and sensitive keys
- Helps maintain compliance with security benchmarks (e.g., CIS)

**Scan Type:**  
Filesystem scan (`trivy fs .`) triggered on every push and pull request.

---

## Semgrep – Static Code Analysis

**Purpose:**  
Semgrep performs lightweight static analysis to catch insecure coding patterns, logic flaws, and enforce custom security rules.

**How It Protects:**
- Detects hardcoded credentials, unsafe function calls, and insecure regex
- Enforces secure coding practices across languages
- Supports custom rules tailored to your environment
- Integrates with CI/CD for early detection

**Scan Type:**  
Source code scan (`semgrep scan .`) triggered on every push and pull request.

---

## GitLeaks – Secret Detection

**Purpose:**  
GitLeaks scans your repository for hardcoded secrets, API keys, tokens, and credentials before they reach production.

**How It Protects:**
- Identifies secrets in committed code, config files, and history
- Prevents credential leaks to public or shared repositories
- Supports custom regex rules for organization-specific secrets

**Scan Type:**  
Repository scan (`gitleaks detect --source .`) triggered on every push and pull request.

---

## Continuous Monitoring

All scans are automated via GitHub Actions and run on:
- Every push to `main`
- Every pull request
- Scheduled weekly scans (optional)

Scan results are visible in the GitHub Actions tab and can be exported for audit purposes.

---




# 🔐 Secure CI/CD Pipeline with SAST, Secret Scanning & Kill Switch

A security-first DevSecOps pipeline built with Jenkins, integrating 
three layers of security scanning across every build.

## 🛠️ Tech Stack
Jenkins | Docker | SonarQube | Trivy | Gitleaks | Python (Flask) | Git | GitHub

## 🔄 Pipeline Flow
GitHub → Gitleaks → SonarQube → Docker Build → Trivy Scan → Deploy

## 📁 Repo Contains
- `app.py` — Flask web application
- `Dockerfile` — containerizes the Flask app
- `requirements.txt` — Python dependencies

## 🔍 What This Pipeline Does
- **Gitleaks** — scans for hardcoded secrets on every build
- **SonarQube** — static code analysis (SAST) via Jenkins token integration
- **Trivy** — scans Docker image for CVEs before deployment
- **Kill Switch** — pipeline auto-aborts if HIGH/CRITICAL CVEs detected
- **RBAC** — Jenkins hardened, anonymous access disabled

## ⚠️ Real Vulnerability Encountered
During a build, Trivy flagged a CRITICAL CVE in the base image.
Investigated the CVE, upgraded base image and dependencies,
re-ran pipeline — clean scan, successful deployment.

## 📌 Note
Pipeline script lives in Jenkins directly.
This repo contains the application code and Docker configuration.

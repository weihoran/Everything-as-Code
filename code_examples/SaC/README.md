# Security as Code (SaC): Codified Checkov Vulnerability Scanning

## Overview
This project provides a  **Security as Code (SaC)** script using **Checkov** to scan **Terraform** scripts provisioning a Kubernetes cluster.
The `checkov_scan.yml` workflow scans Terraform for vulnerabilities (e.g., public endpoints) and fails on high-severity issues, ensuring security before policy checks and deployment. It runs as part of a single pipeline run, triggered by a `push` to `main` or a `pull_request`.

### Purpose
- Scans Terraform IaC for security vulnerabilities using Checkov.
- Integrates with the pipeline’s validation, policy checks, and deployment.
- Enforces security-as-code for EKS provisioning.
- Aligns with NIST SP 800-53 controls via OSCAL.



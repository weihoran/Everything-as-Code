
# Example As-Code Artifacts that demonstrate the implementation of the EaC Conceptual Model

## Overview
This project demonstrates the provisioning of a Kubernetes cluster and configuration of nodes with the Datadog host agent using a **DevSecOps pipeline**. It integrates **Infrastructure as Code (IaC)**, **Configuration as Code (CaC)**, **Security as Code (SaC)**, **Policy as Code (PaC)**, **Compliance as Code (CoaC)**, and **Pipeline as Code (PiaC)** to ensure a secure, compliant deployment. The pipeline executes as a single run, validating, scanning, enforcing policies, and deploying artifacts, with NIST SP 800-53 compliance documented via OSCAL.

Each artifact type is organized in a dedicated subfolder with its own README for detailed usage. This top-level README provides an overview and references those guides.

### Purpose
- Provisions and configures an EKS cluster using Terraform and Ansible.
- Enforces security with Checkov and Rego policies.
- Documents compliance with OSCAL.
- Automates the process via a GitHub Actions pipeline.

## Project Structure
- **IaC/**: Terraform scripts for EKS provisioning. See `IaC/README.md`.
- **CaC/**: Ansible playbooks for Datadog node configuration. See `CaC/README.md`.
- **SaC/**: Checkov workflow for Terraform vulnerability scanning. See `SaC/README.md`.
- **PaC/**: Rego policies for configuration validation. See `PaC/README.md`.
- **CoaC/**: OSCAL Component Definition for compliance. See `CoaC/README.md`.
- **PiaC/**: GitHub Actions workflows for the pipeline. See `PiaC/README.md`.

## Prerequisites
- GitHub repository with subfolders and secrets (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `DATADOG_API_KEY`).
- Tools: Terraform, Ansible, Checkov, Ansible-lint, Conftest, Trestle (installed by workflows).

## Setup
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd eks-pipeline
   ```
2. Ensure subfolders (`IaC`, `CaC`, `SaC`, `PaC`, `CoaC`, `PiaC`) contain artifacts as described in their READMEs.
3. Configure GitHub Secrets in `Settings > Secrets and variables > Actions`.
4. Push changes to trigger the pipeline:
   ```bash
   git push origin main
   ```

## Usage
- **Trigger**: Push to `main` or open a pull request.
- **Pipeline Run**: Executes sequentially:
  1. Validates IaC/CaC (PiaC).
  2. Scans Terraform with Checkov (SaC).
  3. Enforces Rego policies and Ansible-lint (PaC, CaC).
  4. Deploys EKS and Datadog (IaC, CaC, PiaC).
- **Results**: View in `Actions` tab. Fix issues per subfolder READMEs.
- **Compliance**: Validate OSCAL in `CoaC` for NIST SP 800-53 reporting.

## Integration
The pipeline integrates artifacts in a single run:
- **IaC**: Terraform provisions EKS, validated and scanned.
- **CaC**: Ansible configures nodes, linted and policy-checked.
- **SaC**: Checkov scans Terraform for vulnerabilities.
- **PaC**: Rego policies enforce compliance.
- **CoaC**: OSCAL documents NIST SP 800-53 controls.
- **PiaC**: Workflows orchestrate the process.

See subfolder READMEs for details:
- `IaC/README.md`: Terraform setup.
- `CaC/README.md`: Ansible configuration.
- `SaC/README.md`: Checkov scanning.
- `PaC/README.md`: Rego policies.
- `CoaC/README.md`: OSCAL compliance.
- `PiaC/README.md`: Pipeline execution.

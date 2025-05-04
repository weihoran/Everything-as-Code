# Rego Policy Project for Terraform and Ansible Validation

## Overview
This project provides a set of **PaC** scripts, written for **Open Policy Agent (OPA)**, to validate **IaC** and **CaC** scripts used in provisioning a Kubernetes cluster (e.g., AWS EKS) and configuring worker nodes (e.g., installing the Datadog host agent). The policies enforce security, compliance, and best practices, ensuring the infrastructure and node configurations are secure and reliable.

The policies are designed to integrate with a workflow where:
- **Terraform** provisions an EKS cluster, node groups, and outputs node IPs for Ansible.
- **Ansible** configures EKS nodes by installing the Datadog host agent for OS-level monitoring.
- **Rego** validates both Terraform plans and Ansible playbooks to catch misconfigurations before deployment.

This project is ideal for cloud-native environments requiring policy-as-code to enforce standards like CIS AWS Benchmarks or internal security policies.

## Project Structure
The project contains six Rego policy files, each targeting specific aspects of Terraform or Ansible configurations:

1. **`deny_public_eks_endpoint.rego`**: Ensures EKS clusters disable public endpoint access for security.
2. **`deny_node_group_no_keypair.rego`**: Requires EKS node groups to use a secure SSH key pair for node access.
3. **`deny_non_sensitive_outputs.rego`**: Ensures Terraform outputs containing node IPs are marked as sensitive.
4. **`deny_hardcoded_api_key.rego`**: Prevents hard-coded Datadog API keys in Ansible `vars.yml`.
5. **`deny_non_idempotent_shell.rego`**: Ensures Ansible shell tasks (e.g., Datadog installation) are idempotent.
6. **`deny_non_private_ips.rego`**: Validates that Ansible’s dynamic inventory only includes private IPs for EKS nodes.

## Prerequisites
To use these Rego policies, you need:
1. **Open Policy Agent (OPA)** or **Conftest**:
   - Install OPA: `curl -L -o opa https://openpolicyagent.org/downloads/v0.68.0/opa_linux_amd64 && chmod 755 opa`
   - Install Conftest: `curl -L https://github.com/open-policy-agent/conftest/releases/download/v0.42.0/conftest_0.42.0_Linux_x86_64.tar.gz | tar xz`
2. **Terraform**:
   - Installed and configured to provision an EKS cluster.
   - Generate a JSON plan: `terraform plan -out=tfplan && terraform show -json tfplan > tfplan.json`
3. **Ansible**:
   - Installed and configured with playbooks for node configuration (e.g., Datadog host agent installation).
   - Example playbook files: `playbook.yml`, `vars.yml`, `inventory.yml`.
4. **Input Files**:
   - **Terraform**: `tfplan.json` (Terraform plan output).
   - **Ansible**: `playbook.yml`, `vars.yml`, and inventory output (e.g., parsed `inventory.yml`).
5. **CI/CD (Optional)**:
   - Tools like GitHub Actions or GitLab CI to automate policy checks.

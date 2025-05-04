# CaC (Ansible Playbook) for Datadog Host Agent Installation on the Kubernetes Cluster provisioned with IaC

## Overview
This Ansible playbook automates the installation of the Datadog host agent on Amazon EKS worker nodes to collect OS-level metrics (e.g., CPU, memory, disk). It is designed to work with a Kubernetes cluster provisioned by Terraform, using cluster information (e.g., node IPs) as input. The playbook is idempotent, ensuring the agent is installed only if not already present.

This task is suited for Ansible because it involves **node-level configuration**, which Helm (Kubernetes-only) and Terraform (infrastructure-focused) cannot efficiently handle. The Datadog Kubernetes components (e.g., Cluster Agent) should be deployed separately via Helm.

## Files
- **`inventory.yml`**: Defines a dynamic inventory using Terraform outputs (e.g., `terraform_output.json`) to target EKS worker nodes.
- **`playbook.yml`**: Installs the Datadog host agent on EKS nodes, checking for existing installations to ensure idempotency.
- **`vars.yml`**: Stores variables, including the Datadog API key (placeholder; use Ansible Vault or a secret manager in production).
- **`README.md`**: This documentation.

## Prerequisites
1. **Ansible**: Installed on the control node (e.g., `ansible` and `ansible-core` via pip or package manager).
2. **SSH Access**: The control node must have SSH access to EKS worker nodes (ensure key pairs are configured in Terraform).
3. **Terraform Outputs**: A `terraform_output.json` file containing EKS node IPs, structured as:
   ```json
   {
     "node_ips": {
       "value": ["<ip1>", "<ip2>", "..."]
     }
   }

## CaC (Ansible Playbook) for Datadog Host Agent Configuration on Kubernetes Nodes

This Ansible playbook automates the installation of the Datadog host agent on Kubernetes worker nodes to collect OS-level metrics (e.g., CPU, memory, disk). It is designed to work with managed Kubernetes clusters like AWS EKS, IBM Kubernetes Service (IKS), or Azure AKS, using cluster information (e.g., node IPs) from Terraform outputs. The playbook is idempotent and supports different node operating systems (e.g., Amazon Linux, Ubuntu).

This task uses Ansible because it involves **node-level configuration**, which Helm (Kubernetes-only) and Terraform (infrastructure-focused) cannot efficiently handle. The Datadog Kubernetes components (e.g., Cluster Agent) should be deployed separately via Helm.

## Supported Platforms
- **AWS EKS**: Nodes typically run Amazon Linux 2/2023.
- **IBM Kubernetes Service (IKS)**: Nodes typically run Ubuntu or RHEL.
- **Azure AKS**: Nodes typically run Ubuntu or Azure Linux.

## Files
- **`inventory.yml`**: Defines a dynamic inventory using Terraform outputs (e.g., `terraform_output.json`) to target worker nodes. Supports different JSON paths for EKS, IKS, and AKS.
- **`playbook.yml`**: Installs the Datadog host agent, ensuring dependencies (e.g., `curl`) are present for Debian and RPM-based systems.
- **`vars.yml`**: Stores the Datadog API key (use Ansible Vault or a secret manager in production).
- **`README.md`**: This documentation.

## Prerequisites
1. **Ansible**: Installed on the control node (e.g., `ansible` via pip or package manager).
2. **SSH Access**: The control node must have SSH access to worker nodes. Ensure Terraform configures key pairs or cloud-specific access:
   - **EKS**: EC2 key pairs and security groups.
   - **IKS**: IBM Cloud SSH keys.
   - **AKS**: Azure VM SSH keys.
3. **Terraform Outputs**: A `terraform_output.json` file containing node IPs, structured as:
   ```json
   {
     "<key>": {
       "value": ["<ip1>", "<ip2>", "..."]
     }
   }

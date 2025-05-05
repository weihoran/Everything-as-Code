# Compliance as Code (CoaC): OSCAL Component Definition for the Kubernetes Cluster

## Overview
This project provides an **OSCAL (Open Security Controls Assessment Language)** Component Definition in JSON format  that documents the security controls implemented for an **Amazon EKS (Elastic Kubernetes Service) cluster**. The EKS cluster is the primary component, encompassing its infrastructure (provisioned via Terraform) and node configurations (managed via Ansible to install the Datadog host agent for OS-level monitoring).

The OSCAL Component Definition maps six **Rego** policies, enforced by **Open Policy Agent (OPA)** and **Conftest**, to **NIST SP 800-53 Revision 5** controls. These policies, derived from the component definition, validate the Terraform and Ansible scripts to ensure the cluster’s security and compliance. The OSCAL file serves as a machine-readable compliance artifact for audits, Governance, Risk, and Compliance (GRC) platforms, or DevSecOps pipelines.

### Purpose
The OSCAL Component Definition:
- Defines the EKS cluster as the component, covering its control plane, node groups, and node configurations.
- Documents six Rego policies as control implementations, enforcing NIST SP 800-53 controls.
- Provides traceability between the cluster’s security controls, Rego policies, and implementation details.
- Supports compliance reporting for the Kubernetes environment.

### Context
- **Terraform**: Provisions the EKS cluster, including the control plane (`aws_eks_cluster`), node groups (`aws_eks_node_group`), and outputs (e.g., node IPs).
- **Ansible**: Configures EKS worker nodes by installing the Datadog host agent.
- **Rego Policies**: Derived from the EKS cluster’s security requirements, these policies validate Terraform plans and Ansible playbooks.
- **OSCAL**: Documents the EKS cluster’s compliance with NIST SP 800-53 in a standardized format.

## Project Structure
The project contains a single OSCAL Component Definition file:

- **`OSCAL_component_definition.json`**:
  - Defines the "EKS Cluster" component.
  - Maps six Rego policies to NIST SP 800-53 controls, derived from the cluster’s security requirements:
    1. `deny_public_eks_endpoint.rego` → SC-7 (Boundary Protection)
    2. `deny_node_group_no_keypair.rego` → IA-2 (Identification and Authentication)
    3. `deny_non_sensitive_outputs.rego` → SC-8 (Secure Communication)
    4. `deny_hardcoded_api_key.rego` → CM-7 (Least Functionality)
    5. `deny_non_idempotent_shell.rego` → CM-6 (Configuration Settings)
    6. `deny_non_private_ips.rego` → SC-7 (Boundary Protection)
  - References policy files in a `policy/` directory (assumed to exist).

## Prerequisites
To use this OSCAL Component Definition, you need:
1. **OSCAL-Compatible Tools**:
   - Tools like **OSCAL CLI** (`oscalkit`), **Trestle**, or GRC platforms (e.g., Xacta) to process OSCAL JSON.
   - Install Trestle: `pip install trestle`
2. **Rego Policy Files**:
   - The six `.rego` files derived from the component definition, stored in a `policy/` directory:
     - `deny_public_eks_endpoint.rego`
     - `deny_node_group_no_keypair.rego`
     - `deny_non_sensitive_outputs.rego`
     - `deny_hardcoded_api_key.rego`
     - `deny_non_idempotent_shell.rego`
     - `deny_non_private_ips.rego`
   - These are assumed to be available (see related Rego policy project).
3. **Terraform and Ansible Setup**:
   - **Terraform**: Configured to provision an EKS cluster, generating a JSON plan (`tfplan.json`).
     ```hcl
     resource "aws_eks_cluster" "example" {
       name     = "example-cluster"
       vpc_config { endpoint_public_access = false }
     }
     resource "aws_eks_node_group" "example" {
       cluster_name    = aws_eks_cluster.example.name
       remote_access { ec2_ssh_key = "my-key-pair" }
     }
     output "node_ips" { value = [...]; sensitive = true }
     ```
   - **Ansible**: Configured to install the Datadog host agent, with playbooks (`playbook.yml`, `vars.yml`, `inventory.yml`).
     ```yaml
     - name: Install Datadog host agent
       shell: |
         DD_API_KEY={{ datadog_api_key }} bash -c "$(curl -L ...)"
       when: not datadog_stat.stat.exists
     ```
     ```yaml
     datadog_api_key: "{{ lookup('env', 'DATADOG_API_KEY') }}"
     ```
4. **OPA/Conftest**:
   - Installed to enforce Rego policies:
     ```bash
     curl -L -o opa https://openpolicyagent.org/downloads/v0.68.0/opa_linux_amd64
     chmod 755 opa
     curl -L https://github.com/open-policy-agent/conftest/releases/download/v0.42.0/conftest_0.42.0_Linux_x86_64.tar.gz | tar xz
     ```
5. **CI/CD (Optional)**:
   - Tools like GitHub Actions or GitLab CI to integrate OSCAL and policy validation.

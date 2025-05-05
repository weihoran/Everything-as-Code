
# Pipeline as Code (PiaC): Integration of IaC, CaC, PaC, and SaC

The pipeline comprises:
1. **Validate IaC and CaC (`validate_iac_cac.yml`)**: Validates Terraform and Ansible syntax.
2. **Policy and Security Checks (`policy_security_checks.yml`)**: Enforces Rego policies (PaC) and scans for vulnerabilities with Checkov and Ansible-lint (SaC).
3. **Deploy IaC and CaC (`deploy_iac_cac.yml`)**: Deploys the EKS cluster (IaC) and configures nodes (CaC).

The workflows execute in order within a single run, using dependencies (`needs`) to ensure validation precedes checks, and checks precede deployment. 

### Purpose
The pipeline:
- Executes as a single run to validate, secure, and deploy the EKS cluster and Datadog configuration.
- Integrates IaC (Terraform), CaC (Ansible), PaC (Rego), and SaC (Checkov/Ansible-lint).
- Enforces security and compliance before deployment, failing on critical issues.
- Aligns with NIST SP 800-53 controls via OSCAL for auditability.
- Automates the DevSecOps lifecycle in a single CI/CD run.


The pipeline executes as a single run, triggered by a `push` to `main` or a `pull_request`. The workflows run sequentially, enforced by `needs` dependencies, ensuring a cohesive process:

1. **Trigger**:
   - A `git push` to `main` or a pull request initiates the pipeline.
   - All workflows eligible for the event are queued.

2. **Validation (`validate_iac_cac.yml`)**:
   - **Runs First**: No dependencies, starts immediately.
   - **Actions**:
     - Validates Terraform syntax (`terraform validate`).
     - Checks Ansible playbook syntax (`ansible-playbook --syntax-check`).
   - **Outcome**: Fails if syntax errors exist, halting the pipeline.
   - **Example Failure**: Invalid Terraform resource or malformed YAML.

3. **Policy and Security Checks (`policy_security_checks.yml`)**:
   - **Runs Second**: Waits for `validate` to complete (`needs: validate`).
   - **Actions**:
     - Scans Terraform with Checkov (e.g., `CKV_AWS_38` for public endpoints).
     - Validates Ansible with Ansible-lint for best practices.
     - Generates Terraform plan (`tfplan.json`) and enforces Rego policies with Conftest (e.g., `deny_hardcoded_api_key.rego`).
     - Fails if high-severity vulnerabilities or policy violations are found.
   - **Outcome**: Fails if critical issues are detected, stopping deployment.
   - **Example Failure**: Public EKS endpoint or hard-coded API key.

4. **Deployment (`deploy_iac_cac.yml`)**:
   - **Runs Third**: Waits for `policy-security` to complete (`needs: policy-security`).
   - **Actions**:
     - Applies Terraform to provision the EKS cluster (`terraform apply`).
     - Runs Ansible to configure nodes with Datadog (`ansible-playbook`).
   - **Conditions**: Only runs on `push` to `main`, not on pull requests.
   - **Outcome**: Deploys the EKS cluster and configures nodes if all checks pass.
   - **Example Failure**: AWS credential issues or Ansible connection errors.

5. **Run Completion**:
   - **Success**: All workflows pass, and the EKS cluster is deployed with configured nodes.
   - **Failure**: Any workflow failure (e.g., syntax error, policy violation) stops the pipeline, skipping deployment.
   - **Results**: Visible in `Actions` tab, with logs for each workflow.

## Integration of As Code Artifacts
The pipeline integrates IaC, CaC, PaC, SaC, and OSCAL in a single run:
- **IaC (Terraform)**:
  - **Validation**: Syntax checked in `validate_iac_cac.yml`.
  - **Security**: Scanned by Checkov in `policy_security_checks.yml` (e.g., `CKV_AWS_38`).
  - **Policy**: Validated by Rego policies (e.g., `deny_public_eks_endpoint.rego`) in `policy_security_checks.yml`.
  - **Deployment**: Applied in `deploy_iac_cac.yml` to provision EKS.
- **CaC (Ansible)**:
  - **Validation**: Syntax checked in `validate_iac_cac.yml`.
  - **Security**: Validated by Ansible-lint and Rego (e.g., `deny_hardcoded_api_key.rego`) in `policy_security_checks.yml`.
  - **Deployment**: Executed in `deploy_iac_cac.yml` to configure nodes.
- **PaC (Rego)**:
  - **Enforcement**: Six policies validate Terraform and Ansible in `policy_security_checks.yml` using Conftest.
  - **Compliance**: Aligns with OSCAL controls (e.g., SC-7, CM-7), ensuring NIST SP 800-53 compliance.
- **SaC (Checkov/Ansible-lint)**:
  - **Scanning**: Checkov scans Terraform, Ansible-lint validates Ansible in `policy_security_checks.yml`.
  - **Enforcement**: Fails on high-severity issues, embedding security-as-code.
- **OSCAL**:
  - **Documentation**: `rego_policy_component_definition.json` documents EKS cluster controls.
  - **Traceability**: Links Rego policies to NIST controls, with Checkov as a supporting tool.
  - **Usage**: Validated post-run for compliance reporting:
    ```bash
    trestle validate -f rego_policy_component_definition.json
    ```

## Usage
1. **Trigger the Pipeline**:
   - Push to `main` or open a pull request.
   - View in `Actions` tab:
     - `Validate IaC and CaC`
     - `Policy and Security Checks`
     - `Deploy IaC and CaC` (push only)

2. **Monitor Execution**:
   - **Validation**: Ensures Terraform and Ansible are syntactically correct.
   - **Checks**: Verifies security (Checkov, Ansible-lint) and policies (Rego).
   - **Deployment**: Provisions EKS and configures nodes if all pass.
   - Check logs for each workflow.

3. **Review Results**:
   - **Validation**: Syntax errors (e.g., invalid Terraform resource).
   - **Checkov**: Vulnerabilities (e.g., `Public endpoint detected`).
   - **Ansible-lint**: Best practice warnings (e.g., `Use 'become: true'`).
   - **Conftest**: Policy violations (e.g., `Non-private IP detected`).
   - **Deployment**: Terraform and Ansible execution logs.

4. **Remediate Issues**:
   - Fix syntax errors in `main.tf` or `playbook.yml`.
   - Address Checkov failures (e.g., `endpoint_public_access = false`).
   - Resolve Ansible-lint or Rego issues (e.g., use environment variables).
   - Re-push to re-run the pipeline.

5. **Compliance with OSCAL**:
   - Use `rego_policy_component_definition.json` for NIST SP 800-53 reporting.
   - Validate OSCAL file post-run:
     ```bash
     trestle validate -f rego_policy_component_definition.json
     ```

## Applicability
- **Primary Use**: EKS cluster with Datadog node monitoring.
- **Adaptability**:
  - Supports IKS/AKS by updating Terraform and Rego policies.
  - Ansible and Ansible-lint are platform-agnostic.
  - Checkov supports other IaC frameworks.
- **Compliance**: Aligns with NIST SP 800-53 via OSCAL.

## Extending the Project
- **Custom Checkov Policies**:
  - Add policies in `custom_checks/`:
    ```yaml
    check:
      id: CUSTOM_DATADOG_API_KEY
      name: Ensure Datadog API key is not hard-coded
      severity: HIGH
      framework: ansible
      query: vars.yml contains datadog_api_key without lookup
    ```
  - Use: `checkov -d . --external-checks-dir custom_checks`
- **Alternative Tools**:
  - Use **Trivy** or **KICS** for scanning:
    ```bash
    trivy config .
    ```
  - Enhance Ansible with **KICS** or custom Rego.
- **Multi-Cloud**:
  - Adapt Terraform for IKS/AKS; update Rego policies.
- **OSCAL Enhancements**:
  - Add Checkov to OSCAL:
    ```json
    {"props": [{"name": "tool", "value": "Checkov"}]}
    ```
  - Create SSP:
    ```bash
    trestle create ssp
    ```
- **Post-Deployment**:
  - Scan nodes with **Lynis** or **OpenSCAP**.

## License
MIT License

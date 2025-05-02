# 📄 Companion File: Subdomains and Relationships in the EaC Domain Model

This document serves as a companion to the conceptual model figure, elaborating on the subdomains within each established "as-code" practice and the relationships between them. The goal is to clarify the integration logic, functional overlaps, and lifecycle sequencing embedded in the model.
![image](https://github.com/user-attachments/assets/1ff0f13f-f383-40c6-b1d3-9b3250f02883)

---

## Infrastructure as Code (IaC)

**Subdomains:**
- **Compute Resources:** VMs, containers, and autoscaling groups defined via code.
- **Network Resources:** Load balancers, firewalls, and virtual networks.
- **Storage Resources:** File systems, object storage, and volume management.
- **Serverless Resources:** Function-as-a-Service (FaaS) and container-based compute services.

**Relationships:**
- IaC **provisions the foundation** upon which Configuration as Code (CaC) builds.
- IaC **triggers validation steps** like linting and syntax checks.
- IaC artifacts are **scanned by security and policy engines** (e.g., Security as Code, Policy as Code) prior to deployment.
- IaC is constrained by **policies** defined in PaC and CoaC.

---

## Configuration as Code (CaC)

**Subdomains:**
- **OS Configurations:** Users, kernel parameters, permissions, firewall rules.
- **Middleware Configurations:** Databases, message brokers, and web servers.
- **Application-Level Configurations:** Environment variables, secrets, feature flags.
- **Orchestration Configurations:** Kubernetes, service mesh, ingress controllers.

**Relationships:**
- CaC **depends on IaC** to establish the baseline infrastructure.
- **Security and compliance scans** are applied post-configuration for validation.
- Configuration is a **target for enforcement** by both Policy as Code and Security as Code.

---

## Security as Code (SaC)

**Subdomains:**
- **Security Baseline Configurations:** IAM roles, encryption policies, secret management.
- **Vulnerability Scanning:** Static scans of IaC, OS, and containers for known risks.
- **Security Testing:** SAST and DAST during CI/CD execution.
- **Threat Detection:** Runtime anomaly detection and IDS logic.

**Relationships:**
- Security scans are **embedded in pipelines** (both app and infra).
- SaC **validates artifacts** from IaC and CaC.
- Feeds alerts into **Policy as Code constraints** or runtime block actions.
- Shares scanning results with CoaC for compliance reporting.

---

## Policy as Code (PaC)

**Subdomains:**
- **Automated Enforcement:** Validate IaC, CaC, and app manifests against rules.
- **Codified Policy Types:** 
  - *Security Policies:* E.g., “no public S3 buckets.”
  - *Compliance Policies:* E.g., “must use encrypted volumes.”
  - *Business/Internal Rules:* E.g., “tag all resources with cost center.”
  - *Infrastructure Guardrails:* Hardcoded limits for size, location, etc.

**Relationships:**
- Applies validation logic to **IaC and CaC before deployment.**
- **Shares policy definitions** with CoaC.
- **Triggers remediation actions** on failure (e.g., block provisioning).
- **Embedded in CI/CD workflows** via OPA/Gatekeeper/Conftest.

---

## Compliance as Code (CoaC)

**Subdomains:**
- **Regulatory Controls as Code:** Mappings from frameworks like NIST 800-53 or ISO 27001.
- **Compliance Scanning:** Static checks of code and runtime environments.
- **Continuous Monitoring:** Runtime state validation (e.g., dashboards).
- **Reporting and Documentation:** Audit-ready outputs in OSCAL.

**Relationships:**
- CoaC **encapsulates formal policies** and shares rules with PaC.
- **Consumes results from Security as Code scans** for evidence.
- **Validates post-provision states** (e.g., encryption enabled, ports closed).
- **Feeds documentation pipelines** for audits and assessments.

---

## Inter-Practice Relationships Summary

| Source Practice     | Target Practice       | Relationship Type                                  |
|---------------------|-----------------------|----------------------------------------------------|
| IaC                 | CaC                   | Provisions base infrastructure                     |
| IaC                 | SaC / PaC / CoaC      | Is scanned and validated pre-deployment            |
| CaC                 | SaC / PaC / CoaC      | Target for policy and security enforcement         |
| SaC                 | PaC / CoaC            | Supplies evidence and test results                 |
| PaC                 | IaC / CaC             | Validates and enforces constraints                 |
| CoaC                | PaC / SaC / IaC / CaC | Integrates policies and aggregates compliance data |
| PaC                 | CI/CD Pipelines       | Embedded in pipelines to enforce policies early    |

---

## Lifecycle Stages Mapped to the Model

| Lifecycle Stage            | Relevant Components                                      |
|----------------------------|----------------------------------------------------------|
| **Linting & Validation**   | IaC syntax, policy rules, config format (IaC, PaC, CaC)  |
| **Vulnerability Scanning** | IaC templates, container images, OS configs (SaC)        |
| **Plan & Preview**         | Policy checks, config diff, approval gates (PaC, CaC)    |
| **Provision Resources**    | IaC and CaC execution                                    |
| **Post-Provision Checks**  | Runtime validation, drift detection, CoaC scans          |

---

## Notes

- All enforcement and validation steps are integrated through **Pipeline as Code** mechanisms (e.g., Terraform pipelines, GitHub Actions).
- Some enforcement logic may span across both **build-time and runtime**, blurring boundaries between PaC, SaC, and CoaC.

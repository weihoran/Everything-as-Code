# 📘 Taxonomy of Everything as Code (EaC)

This taxonomy organizes "Everything as Code" (EaC) practices across functional domains of cloud-native software delivery, based on their roles in modern DevOps pipelines and their maturity in the industry. Practices are further classified as Established (🟥), Emerging (🟦), or Speculative (🟩) based on frequency of literature references, tooling support, and adoption levels.

---

## 🧭 Legend  
- 🟥 **Established Practices** — Commonly adopted, well-documented, and broadly supported by tools  
- 🟦 **Emerging Practices** — Increasingly adopted, partially supported, and documented in industry sources  
- 🟩 **Speculative Practices** — Low adoption and limited documentation; tracked in supplementary material

## 🏗️ Infrastructure Provisioning and Management  
*Practices focused on the declarative provisioning and post-provision configuration of foundational infrastructure components, such as compute, storage, and network resources.*

- **Infrastructure as Code** 🟥  
  Declaratively provision and manage infrastructure components like virtual machines, containers, and load balancers using code that is version-controlled and repeatable.  
  *Tools:* Terraform, Pulumi, CloudFormation, Ansible, Chef, Puppet  

- **Configuration as Code** 🟥  
  Automate the configuration of operating systems, middleware, and application settings after infrastructure provisioning. Supports dynamic and environment-specific configuration.  
  *Tools:* Ansible, Chef, Puppet, SaltStack, Helm  

- **Storage as Code** 🟦  
  Allocate and configure block, object, or file-based storage using code interfaces, enabling consistent resource setup across environments.  
  *Tools:* Ceph  

- **Network as Code** 🟦  
  Define and manage virtual networks, routing rules, and security groups declaratively using code-driven automation.  
  *Tools:* Netmiko  

- **(Infra) Pipeline as Code** 🟥  
  Automate the end-to-end lifecycle of infrastructure delivery through code-defined workflows, integrating provisioning, validation, and remediation steps.  
  *Tools:* Jenkins, GitLab CI, Terraform pipelines  

---

## ⚙️ Platform and Orchestration  
*Practices that define and manage platform-level capabilities and runtime orchestration, including service coordination, cluster setups, and environment templates.*

- **Platform as Code** 🟦  
  Codify entire application platforms, including runtimes, databases, and middleware, to standardize and replicate environments across teams or deployments.  
  *Tools:* Crossplane  

- **Environments as Code** 🟦  
  Codify and manage multi-stage environments (e.g., development, staging, production), including dependencies, secrets, and resource allocations.  
  *Tools:* Terraform, Ansible  

- **Orchestration as Code** 🟦  
  Define how services are orchestrated at runtime, including scheduling, scaling, and service discovery—often atop Kubernetes or similar systems.  
  *Tools:* Salt Project  

- **Jobs as Code** 🟩  
  Codify the definition, scheduling, and execution logic of batch jobs and background processing tasks.  
  *Tools:* Custom GitOps tools (inferred)

---

## 🧱 Application Design and Development  
*Practices aimed at codifying the structure, lifecycle, and supporting artifacts for application-level development and documentation.*

- **Architecture as Code** 🟦  
  Use code to model system architecture, including components, interfaces, and dependencies. Facilitates automated architecture validation and visualization.  
  *Tools:* Structurizr, Archi  

- **Diagrams as Code** 🟦  
  Generate visual diagrams (e.g., flowcharts, infrastructure topologies) programmatically from source code or configuration files.  
  *Tools:* Graphviz, Mermaid  

- **Docs as Code** 🟦  
  Treat software documentation as code by writing it in plaintext markup, storing it in version control, and integrating it into CI/CD pipelines.  
  *Tools:* Markdown  

- **Project as Code** 🟦  
  Automate project scaffolding, dependency setup, and boilerplate generation using reusable code templates.  
  *Tools:* Yeoman  

- **(App) Pipeline as Code** 🟥  
  Define the build, test, and deployment workflow for applications using declarative or scriptable CI/CD pipelines.  
  *Tools:* Jenkins, GitHub Actions, CircleCI, Argo CD  

---

## 🧬 Data and Database  
*Practices that codify the structure, flow, and versioning of data and database systems to ensure consistent data handling.*

- **Data as Code** 🟦  
  Version control data transformations, pipelines, and processing tasks as code to ensure repeatable and auditable data workflows.  
  *Tools:* DVC, Apache Airflow  

- **Database as Code** 🟦  
  Manage schema evolution, migrations, and database configurations through version-controlled code.  
  *Tools:* Liquibase, Bytebase, Flyway  

---

## 🔐 Security and Compliance  
*Practices embedding security and regulatory checks into automated pipelines, ensuring policy conformance and risk mitigation.*

- **Security as Code** 🟥  
  Shift security left by embedding vulnerability scans, static analysis, and threat detection into development pipelines using codified rules.  
  *Tools:* Checkov, Trivy, Snyk, SonarQube, Gauntlt  

- **Detection as Code** 🟦  
  Define detection logic (e.g., for threats, anomalies, misconfigurations) as version-controlled code integrated into monitoring pipelines.  
  *Tools:* Datadog  

- **IAM as Code** 🟦  
  Codify roles, permissions, and identity management policies to ensure consistent and auditable access control.  
  *Tools:* HashiCorp Vault  

- **Privacy as Code** 🟦  
  Automate checks for data privacy compliance, such as PII detection or GDPR adherence, using code-defined rules.  
  *Tools:* N/A  

- **Policy as Code** 🟥  
  Codify organizational, compliance, or security policies as executable rules enforced at deploy-time or runtime.  
  *Tools:* Open Policy Agent (OPA), Kyverno, Sentinel  

- **Compliance as Code** 🟥  
  Define, assess, and report on regulatory control implementations (e.g., NIST, ISO) using machine-readable artifacts.  
  *Tools:* OSCAL, Trestle, InSpec, Auditree  

---

## 📊 Observability and Analysis  
*Practices enabling proactive system health monitoring and business insights through code-driven instrumentation.*

- **Monitoring as Code** 🟦  
  Define system observability components—metrics, logs, alerts—as code to ensure repeatable and consistent monitoring setups.  
  *Tools:* Datadog, Zabbix, Nagios  

- **Dashboards as Code** 🟦  
  Generate and version visual dashboards programmatically to reflect evolving metrics and operational data.  
  *Tools:* Grafana  

- **SLO as Code** 🟦  
  Declare and monitor service-level objectives using code to enforce reliability targets across systems.  
  *Tools:* OpenSLO  

- **Analytics as Code** 🟦  
  Automate user behavior tracking, funnel analysis, and reporting logic through codified analytics configurations.  
  *Tools:* Google Analytics  

---

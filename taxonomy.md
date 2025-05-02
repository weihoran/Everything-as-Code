# Taxonomy of Everything as Code (EaC)

This taxonomy organizes "Everything as Code" (EaC) practices across functional domains of modern software delivery. Practices are classified as Established (🟥), Emerging (🟦), or Speculative (🟩), based on adoption, tool support, and presence in the literature.

---

## Infrastructure Provisioning and Management  
*Practices focused on declarative provisioning and configuration of compute, network, and storage.*

- **Infrastructure as Code** 🟥  
  Declarative provisioning and management of cloud and on-prem infrastructure components.  
  *Tools:* Terraform, Pulumi, CloudFormation, Ansible, Chef, Puppet  

- **Configuration as Code** 🟥  
  Post-provision configuration of OS, middleware, and app settings.  
  *Tools:* Ansible, Chef, Puppet, SaltStack, Helm  

- **Storage as Code** 🟦  
  Code-based provisioning and configuration of storage layers (e.g., block, object).  
  *Tools:* Ceph  

- **Network as Code** 🟦  
  Codified management of virtual and physical networking configurations.  
  *Tools:* Netmiko  

- **(Infra) Pipeline as Code** 🟥  
  Codified workflows for infrastructure deployment and validation.  
  *Tools:* Terraform CI/CD integrations  

---

## Platform and Orchestration  
*Codify orchestration of services, platform configuration, and environment management.*

- **Platform as Code** 🟦  
  Code-defined full platform environments, including runtimes, services, and control planes.  
  *Tools:* Crossplane  

- **Environments as Code** 🟦  
  Codify setup of dev/stage/prod environments including variables and secrets.  
  *Tools:* Terraform, Ansible  

- **Orchestration as Code** 🟦  
  Define service orchestration logic (e.g., deployments, rollouts, autoscaling).  
  *Tools:* Salt Project  

- **Jobs as Code** 🟩  
  Define background or scheduled task logic in reusable job configuration.  
  *Tools:* (Inferred from CI/CD and cloud schedulers)  

- **Management as Code** 🟩  
  Codify organizational or operational management workflows, such as access reviews or escalation paths.  
  *Tools:* Limited; conceptual only  

---

## Application Design and Development  
*Codify application logic, structure, and supporting development artifacts.*

- **Architecture as Code** 🟦  
  Express system architecture models in structured, versioned code.  
  *Tools:* Structurizr, Archi  

- **Diagrams as Code** 🟦  
  Use code to generate and manage diagrams like UML, infrastructure charts.  
  *Tools:* Mermaid, Graphviz  

- **Docs as Code** 🟦  
  Manage software and API documentation using dev toolchains and markdown-based pipelines.  
  *Tools:* Markdown  

- **Project as Code** 🟦  
  Automate project scaffolding and lifecycle operations through reusable templates.  
  *Tools:* Yeoman  

- **(App) Pipeline as Code** 🟥  
  Define CI/CD stages for application code builds, tests, and deployments.  
  *Tools:* GitHub Actions, GitLab CI, Jenkins, Argo CD  

- **Contracts as Code** 🟩  
  Codify service-level or business contracts (e.g., APIs, SLAs) for automated validation and enforcement.  
  *Tools:* Conceptual, some links to OpenAPI, Pact  

---

## Data and Database  
*Manage data and database schema lifecycle using code-based artifacts.*

- **Data as Code** 🟦  
  Define data processing logic, transformations, and flows as version-controlled code.  
  *Tools:* DVC, Airflow  

- **Database as Code** 🟦  
  Codify schema migrations, seed data, and deployment policies for databases.  
  *Tools:* Liquibase, Flyway, Bytebase  

---

## Security and Compliance  
*Integrate security, policy enforcement, and regulatory validation through code.*

- **Security as Code** 🟥  
  Automate static/dynamic analysis, vulnerability scanning, and threat detection via code.  
  *Tools:* Checkov, Trivy, Snyk, SonarQube  

- **Detection as Code** 🟦  
  Codify security incident detection rules integrated into monitoring platforms.  
  *Tools:* Datadog  

- **IAM as Code** 🟦  
  Define identity and access control policies declaratively.  
  *Tools:* HashiCorp Vault  

- **Privacy as Code** 🟦  
  Automate privacy compliance checks (e.g., PII detection, data anonymization).  
  *Tools:* Conceptual  

- **Policy as Code** 🟥  
  Define rules and constraints for infrastructure or application behavior.  
  *Tools:* OPA, Kyverno, Sentinel  

- **Compliance as Code** 🟥  
  Automate regulatory documentation, validation, and audit processes.  
  *Tools:* OSCAL, Trestle, InSpec, Auditree  

- **Law as Code** 🟩  
  Translate legal/regulatory texts into machine-readable, executable rules.  
  *Tools:* OSCAL (partial), others conceptual  

---

## Observability and Analysis  
*Code-driven approaches to monitoring, alerting, performance metrics, and business insights.*

- **Monitoring as Code** 🟦  
  Codify metrics, logs, and alerting rules to ensure observability consistency.  
  *Tools:* Datadog, Zabbix, Nagios  

- **Dashboards as Code** 🟦  
  Generate and manage metrics dashboards declaratively.  
  *Tools:* Grafana  

- **SLO as Code** 🟦  
  Codify service-level objectives to monitor reliability and performance guarantees.  
  *Tools:* OpenSLO  

- **Analytics as Code** 🟦  
  Define analytics tracking logic for events, funnels, and usage patterns via code.  
  *Tools:* Google Analytics  

---

## Legend  
- 🟥 **Established Practices** — Common, well-supported, and documented  
- 🟦 **Emerging Practices** — Gaining traction, partial tooling support  
- 🟩 **Speculative Practices** — Limited documentation, conceptual, tracked in supplementary material

# Reorganized “as Code” Concepts

Below is a way to reorganize these “as Code” concepts into thematic groups that highlight how they relate to one another. Each item includes its description and a reference link.

---

## 1. **Infrastructure & Deployment**

1. **Infrastructure as Code**  
   - **Description**: Managing and provisioning computer data centers through machine-readable definition files.  
   - **Link**: [InfoQ - History of Infrastructure as Code](https://www.infoq.com/presentations/history-infra-as-code/)

2. **Storage as Code**  
   - **Description**: Defining the allocation of storage in a programmatic way.  
   - **Link**: [Pure Storage - Self-Service Storage as Code](https://blog.purestorage.com/products/introducing-the-industrys-first-self-service-storage-as-code-platform/)

3. **Network as Code**  
   - **Description**: Setting up network components by defining the desired state.  
   - **Link**: [DZone - Network as Code](https://dzone.com/articles/the-mindset-required-to-treat-the-network-as-code)

4. **Configuration as Code**  
   - **Description**: Pushing all configuration changes through the CI/CD pipeline.  
   - **Link**: [Kubernetes for Developers](https://livebook.manning.com/book/kubernetes-for-developers/chapter-8/v-7)

5. **Orchestration as Code**  
   - **Description**: Standardizing how you define and run cloud-native components, often across multiple clouds.  
   - **Link**: [Kubernetes](https://kubernetes.io/)

6. **Environments as Code**  
   - **Description**: An abstraction layer over multiple IaC definitions, sequencing them in the right order.  
   - **Link**: [Compuzest - Environment as Code](https://compuzest.com/2021/09/23/from-infrastructure-as-code-to-environment-as-code/)

7. **Application as Code**  
   - **Description**: Deploying the application plus all required infrastructure and tools in one go.  
   - **Link**: [Shipa.io - Application as Code](https://shipa.io/development/from-terraform-to-gitops-to-pulumi/)

8. **Pipeline as Code**  
   - **Description**: Defining deployment pipelines in source code.  
   - **Link**: [GitLab - Pipeline as Code](https://about.gitlab.com/topics/ci-cd/pipeline-as-code/)

9. **Platform as Code**  
    - **Description**: Declarative instructions about the platform layer.  
    - **Link**: [JAXenter - Platform as Code](https://jaxenter.com/infrastructure-as-code-platform-170465.html)

---

## 2. **Observability & Workflow**

10. **Dashboards as Code**  
    - **Description**: Automating creation and updates to metrics dashboards.  
    - **Link**: [Grafana - Dashboards as Code](https://grafana.com/go/grafanaconline/2021/dashboards-as-code/)

11. **Monitoring as Code**  
    - **Description**: Managing observability (alerts, incident management) via code.  
    - **Link**: [The New Stack - Monitoring as Code](https://thenewstack.io/monitoring-as-code-what-it-is-and-why-you-need-it/)

12. **DNS as Code**  
    - **Description**: Managing DNS configurations using code for repeatability.  
    - **Link**: [DNSControl](https://dnscontrol.org/)

13. **Jobs as Code**  
    - **Description**: Automating job scheduling and definitions through code-based notation.  
    - **Link**: [Medium - Jobs as Code](https://medium.com/@jobsascode/jobs-as-code-its-origins-and-its-value-in-the-world-of-devops-4de4b1e1a17f)

14. **Workflow as Code**  
    - **Description**: Orchestrating tasks across servers in a reliable and scalable manner.  
    - **Link**: [Medium - Workflow as Code](https://medium.com/swlh/code-is-the-best-dsl-for-building-workflows-548d6824f549)

15. **Operations as Code**  
    - **Description**: Encoding sequences of tasks to be executed in a repeatable manner.  
    - **Link**: [F5 - Operations as Code](https://www.f5.com/company/blog/as-code-the-continuous-it-stack)

---

## 3. **Security & Governance**

16. **Security as Code**  
    - **Description**: Embedding security considerations into DevOps tools and pipelines.  
    - **Link**: [GitLab - Security as Code](https://about.gitlab.com/blog/2020/03/12/how-to-security-as-code/)

17. **IAM as Code**  
    - **Description**: Defining identity and access roles using code.  
    - **Link**: [Medium - IAM as Code](https://medium.com/marcus-tee-anytime/identity-and-access-management-iam-as-code-in-azure-with-terraform-f67634a1e54e)

18. **Policy as Code**  
    - **Description**: Writing high-level code that manages and enforces policies.  
    - **Link**: [HashiCorp - Policy as Code](https://docs.hashicorp.com/sentinel/concepts/policy-as-code)

19. **Detection as Code**  
    - **Description**: Systematic software-driven threat detection and response.  
    - **Link**: [Softtek - Detection as Code](https://softtek.eu/en/tech-magazine-en/cybersecurity-en/the-detection-as-code-dac-approach-to-cybersecurity/)

20. **Privacy as Code**  
    - **Description**: Automating privacy checks and validations in the CI pipeline.  
    - **Link**: [Ethyca - Privacy as Code](https://ethyca.com/privacy-as-code/)

21. **Compliance as Code**  
    - **Description**: Conducting compliance checks or threat modeling through pull requests and code-based rules.  
    - **Link**: [Omer LH - Threat Modeling as Code](https://www.omerlh.info/2019/01/19/threat-modeling-as-code/)

---


## 5. **Data & Databases**

22. **Database as Code**  
    - **Description**: Managing schema changes and DB configurations as code.  
    - **Link**: [Liquibase - Database as Code](https://www.liquibase.com/blog/database-as-code)

23. **Data as Code**  
    - **Description**: Treating data (its processing, sharing, versioning) with the same rigor as source code.  
    - **Link**: [The New Stack - Data as Code](https://thenewstack.io/the-coming-era-of-data-as-code)

---

## 6. **Documentation & Architecture**

24. **Documentation as Code**  
    - **Description**: Writing documentation using the same tools and processes as code (version control, CI).  
    - **Link**: [Write the Docs - Docs as Code](https://www.writethedocs.org/guide/docs-as-code)

25. **Diagrams as Code**  
    - **Description**: Generating diagrams automatically as part of the build or documentation process.  
    - **Link**: [Structurizr - Diagrams as Code](https://structurizr.com/help/code)

26. **Architecture as Code**  
    - **Description**: Modeling architectures in an executable, code-centric manner.  
    - **Link**: [O'Reilly - Architecture as Code](https://conferences.oreilly.com/software-architecture/sa-ca-2019/public/schedule/detail/75200.html)
---

## 7. **Business & Management**


27. **SLO as Code**  
    - **Description**: Defining reliability/performance targets in a declarative format.  
    - **Link**: [OpenSLO](https://openslo.com/)

28. **Law as Code**  
    - **Description**: Expressing regulations and statutes in code, including ambiguity handling.  
    - **Link**: [Suffolk Lit Lab - Law as Code](https://suffolklitlab.org/legal-tech-class/docs/representing-rules/representing-rules/)

29. **Analytics as Code**  
    - **Description**: Automating user behavior analytics setup and management.  
    - **Link**: [Nick McHardy - Analytics as Code](https://nickmchardy.com/2018/10/analytics-as-code.html)

30. **Management as Code**  
    - **Description**: Conceptualizing all aspects of managing teams and workflows in code.  
    - **Link**: [Medium - Management as Code](https://medium.com/dima-korolev/management-as-code-88919b00f6a8)

---

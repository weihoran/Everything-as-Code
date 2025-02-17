# Relationship Explanations

## Existing (R1–R14)

**R1: IaC → ConfigAsCode**  
"Interlinks with"  
IaC lays down the base resources that ConfigAsCode customizes.

**R2: ConfigAsCode → PolicyAsCode**  
"Validates changes"  
Configuration changes are checked against PolicyAsCode rules.

**R3: ConfigAsCode → PipelineAsCode**  
"Feeds into"  
Configurations are pulled into the pipeline for automated setup.

**R4: PipelineAsCode → SecurityAsCode**  
"Integrates with"  
Security checks run as part of the pipeline stages.

**R5: PipelineAsCode → PolicyAsCode**  
"Applies rules"  
Pipeline enforces policy requirements from PolicyAsCode.

**R6: PipelineAsCode → ComplianceAsCode**  
"Runs checks"  
CI/CD triggers compliance checks to ensure regulatory alignment.

**R7: SecurityAsCode → PolicyAsCode**  
"Depends on"  
Security scanning references policy definitions.

**R8: SecurityAsCode → ConfigAsCode**  
"Overlaps with"  
Security settings often overlap with environment configs.

**R9: PolicyAsCode → SecurityAsCode**  
"Used by"  
Security tools rely on codified policies to define best practices.

**R10: PolicyAsCode → ComplianceAsCode**  
"Underpins"  
Compliance frameworks rely on the policies to check adherence.

**R11: ComplianceAsCode → PipelineAsCode**  
"Relies on"  
Compliance checks are run via the pipeline at various stages.

**R12: ComplianceAsCode → SecurityAsCode**  
"Integrates with"  
Compliance ensures security efforts meet regulatory obligations.

**R13: MonitoringAsCode → PipelineAsCode**  
"Monitors stages"  
Monitoring collects metrics on pipeline execution.

**R14: MonitoringAsCode → SecurityAsCode**  
"Alerts on issues"  
Monitoring can trigger security alerts if anomalies occur.

---

## Newer (R15–R23)

**R15: IaC → EnvironmentsAsCode**  
"Aggregates IaC resources"  
EnvironmentsAsCode combines multiple IaC templates for end-to-end provisioning.

**R16: EnvironmentsAsCode → ConfigAsCode**  
"Uses environment-specific configs"  
Environment definitions incorporate config details.

**R17: EnvironmentsAsCode → PipelineAsCode**  
"Deployed by pipeline"  
CI/CD uses environment definitions to spin up entire setups.

**R18: IaC → PlatformAsCode**  
"Relies on infrastructure"  
PlatformAsCode builds on standard infrastructure definitions.

**R19: PlatformAsCode → PolicyAsCode**  
"Uses policy rules for governance"  
Platform definitions reference policy constraints.

**R20: IAMAsCode → SecurityAsCode**  
"Collaborates on identity checks"  
Roles/permissions feed into security scans and gating rules.

**R21: IAMAsCode → PolicyAsCode**  
"Enforces role-based rules"  
IAMAsCode implements access policies defined in PolicyAsCode.

**R22: PrivacyAsCode → PolicyAsCode**  
"Inherits data-handling policies"  
Privacy checks rely on codified data-management rules.

**R23: PrivacyAsCode → ComplianceAsCode**  
"Ensures privacy compliance"  
Privacy compliance extends general compliance frameworks.

---

## Potential (R24–R28)

**R24: MonitoringAsCode → SLOAsCode**  
"Tracks reliability/performance"  
Monitoring gathers metrics relevant to declared SLO thresholds.

**R25: PolicyAsCode → LawAsCode**  
"Encodes legal/regulatory rules"  
LawAsCode extends policy definitions with statutory frameworks.

**R26: PipelineAsCode → AnalyticsAsCode**  
"Feeds deployment data"  
Pipeline metadata (build times, usage stats) can be analyzed with AnalyticsAsCode.

**R27: DatabaseAsCode → DataAsCode**  
"Overlaps in data definitions"  
Database schemas and data transformations can share definitions or scripts.

**R28: ComplianceAsCode → LawAsCode**  
"Checks legal compliance"  
Compliance rules incorporate laws codified in LawAsCode.

---

## Newly Appended (R29–R32)

**R29: MonitoringAsCode → DashboardsAsCode**  
"Feeds metrics for dashboard creation"  
Monitoring outputs provide data that DashboardsAsCode uses to render visualizations.

**R30: DocumentationAsCode → PipelineAsCode**  
"Integrates doc generation into CI/CD"  
Documentation can be auto-generated or updated in each pipeline run.

**R31: DiagramsAsCode → DocumentationAsCode**  
"Provides generated diagrams for docs"  
Generated diagrams feed into DocumentationAsCode, ensuring updated visuals.

**R32: ArchitectureAsCode → DiagramsAsCode**  
"Generates architecture diagrams"  
Architecture models produce diagram definitions that DiagramsAsCode can render.

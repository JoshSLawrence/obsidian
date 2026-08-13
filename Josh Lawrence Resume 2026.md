# Joshua (Josh) Lawrence

|                            (301) 957-8336 · josh@joshlawrence.dev                            |
| :------------------------------------------------------------------------------------------: |
| [Website](https://joshlawrence.dev) · [LinkedIn](https://www.linkedin.com/in/joshslawrence/) |
|                          US Citizen · Remote · Seattle, Washington                           |


> Staff Platform Engineer who rescues stalled initiatives and turns them into platforms others adopt. 7+ years building cloud infrastructure across Azure, Kubernetes, AWS, and hybrid environments. Known for cross-functional influence—learning systems across business units, spotting inefficiencies, and rallying teams to solve them. Trusted advisor beyond formal scope, from engineers to executives. Technical focus: infrastructure as code, CI/CD, identity, security, FinOps, and developer experience.

| Category | Technologies |
| -------- | ------------ |
| **Cloud & Infrastructure** | Azure, AWS, Azure Arc, Azure Policy, Terraform/OpenTofu, Ansible |
| **Kubernetes & Platform** | Kubernetes, AKS, Istio, Kustomize, Kubebuilder, Karpenter, Kubecost |
| **CI/CD & Automation** | Azure DevOps, GitHub Actions, Go, PowerShell, Python, Bash |
| **Identity & Security** | Entra ID, Microsoft Graph, Defender for Cloud/XDR, CyberArk |
| **Languages & Runtimes** | Go, C#/.NET, Python, PowerShell, Bash |
| **Infrastructure** | Linux, Windows Server, VMware, Cisco UCS |

---

## Work History

### Quadax, Ohio | Sep 2022 - Present

| Role | Period |
| ---- | ------ |
| Senior Cloud Architect | Aug 2025 - Present |
| Cloud Architect | Aug 2024 - Aug 2025 |
| Senior Cloud Engineer | Jun 2024 - Aug 2024 |
| Cloud Engineer | Sep 2022 - Jun 2024 |

> Joined to take over cloud ownership from a departing director and dissolving unit. Grew from sole cloud engineer to leading platform strategy for a 40-person IT department with a majority having no prior cloud expertise.

- Replaced a fragile, contractor-built on-prem Identity Server with a new Azure AD B2C authentication platform—now the central IDP for all company applications. Built custom policies, C# Azure Functions, and federated OIDC/SAML integrations. Unlocked client SSO adoption, increasing SSO usage by over 500%.
- Leading Kubernetes/AKS platform migration for 33 applications, replacing Azure App Service patterns with portable, vendor-agnostic infrastructure. Production clusters already support Kafka, Camunda, and background workers; full application rollout in progress. Architecture delivers improved resource efficiency, in-region redundancy (previously cost-prohibitive), and faster blue/green deployments.
- Unblocked a stalled IaC initiative by designing and building a developer-friendly Terraform/OpenTofu platform on Azure Pipelines—avoiding $50K+/year in vendor costs that had paralyzed the project. Eliminated click-ops and config drift by migrating all infrastructure to state-controlled, PR-based workflows. Built Terraform module abstractions, cookiecutter templates, documentation, and AI-assisted tooling to lower the learning curve and drive adoption across 60+ developers.
- Built a Go/Kubebuilder operator for Azure DevOps build agents after a multi-day CI outage exposed fragile, manually-provisioned VM infrastructure. Containerized agents and automated pool registration, enabling instant scaling and new pool creation without manual intervention.
- Built an identity lifecycle service integrating UKG, ServiceNow, Active Directory, and Microsoft Graph—filling a gap with no out-of-the-box solution. Automated onboarding, terminations, and title changes for 800 employees, reducing provisioning time from inconsistent manual processes to guaranteed 3-hour sync.
- Delivered FinOps wins across the organization: identified bad SKUs, orphaned resources, and reservation opportunities saving thousands monthly. Served as infra SME for BI team's migration from Sisense to PowerBI/Snowflake, reducing licensing costs by $100K/year.
- Designed micro-segmented Azure networking with site-to-site VPNs; migrated workloads with zero application downtime.
- Automated DR validation process with a PowerShell CLI, replacing a manual worksheet-driven procedure. Reduced RTO from 4-5 hours to ~2 hours average; solution now owned and maintained by SysAdmin team.
- Drove observability platform consolidation, building a Dynatrace MVP to replace fragmented Application Insights instances. Updated shared logging libraries and trained teams on instrumentation patterns.
- Led a 6-engineer platform team (influence, not direct reports), establishing product ownership practices for shared systems. Defined guiding principles, quality gates enforced via CI, and documentation standards.
- Serve as security SME on weekly cybersecurity board, evaluating external pen test findings and advising remediation. Mentor a dedicated security engineering team on patterns, standards, and threat response.
- Operate as de facto on-call escalation point across the organization, joining incidents regardless of ownership. Participate in executive post-mortems, author write-ups, and implement operational changes to prevent recurrence.

### ASMGi, Ohio | Sep 2019 - Sep 2022

| Role | Period |
| ---- | ------ |
| System Administrator | Sep 2020 - Sep 2022 |
| Help Desk | Sep 2019 - Sep 2020 |

- Promoted from Help Desk to System Administrator within one year; became SME for operations with largest client (Ernst & Young).
- Built the company's first CI/CD pipeline for an EY engineering team, expanding to broader automation ownership across the MSP.
- Led Azure cloud migrations and built reusable web application security patterns with Application Gateway/WAF, creating a repeatable service offering.

---

## Education & Certificates

| Certification                                | Code   | Status | Issued         |
| -------------------------------------------- | ------ | ------ | -------------- |
| Microsoft Certified - Azure Solutions Architect Expert | AZ-305 | Active | July 2024      |
| Microsoft Certified - DevOps Engineer Expert           | AZ-400 | Active | February 2026  |
| Microsoft Certified - Azure Developer Associate        | AZ-204 | Active | October 2025   |
| Microsoft Certified - Azure Administrator Associate    | AZ-104 | Active | July 2023      |

---

## Consulting Work

### Principal Cloud Architect, The Pennsylvania State University (Retainer, Mid 2025 - Present)

- Built reusable GitHub Actions/Workflows for Azure Data Factory and Synapse promotion with OIDC-based authentication. Contributed OIDC support to Microsoft's Synapse workflow (pending merge—repo maintainer departed); contribution adopted by community users.
- Produced architecture diagrams, cost models, security reviews, DR plans, and training for DBAs, engineers, and system administrators.

### Solution Architect, Web App Express, Ltd (Retainer, 2023)

- Unblocked SSO implementation for a government contract after internal attempts failed. Advised and trained mobile developers on OIDC/OAuth patterns for iOS and Android, enabling successful feature delivery within tight budget constraints.

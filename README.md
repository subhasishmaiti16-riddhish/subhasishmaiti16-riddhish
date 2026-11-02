<div align="center">

  <h1>👋 Hi, I'm Subhasish</h1>
  
  <p align="center">
    <a href="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00C2FF&center=true&vCenter=true&width=650&height=50&lines=Senior+DevOps+%26+Cloud+Architect;DevSecOps+%26+Platform+Engineering+Lead;100%2B+Enterprise+Cloud+Migrations;Zero-Trust+Security+%26+Landing+Zones;FinOps+%26+AI-Native+Cloud+Automation">
      <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1000&color=00C2FF&center=true&vCenter=true&width=650&height=50&lines=Senior+DevOps+%26+Cloud+Architect;DevSecOps+%26+Platform+Engineering+Lead;100%2B+Enterprise+Cloud+Migrations;Zero-Trust+Security+%26+Landing+Zones;FinOps+%26+AI-Native+Cloud+Automation" alt="Typing SVG" />
    </a>
  </p>

  <p>
    <strong>Enterprise Cloud Architect • DevSecOps Practitioner • Platform Engineering • FinOps • AI Automation</strong>
  </p>

  <p>
    <img src="https://img.shields.io/badge/Total%20IT%20Experience-9.5%2B%20Years-0078D4?style=for-the-badge&logo=azure&logoColor=white" alt="IT Experience" />
    <img src="https://img.shields.io/badge/DevOps%20%26%20Cloud-5.5%2B%20Years-68217A?style=for-the-badge&logo=azuredevops&logoColor=white" alt="DevOps Experience" />
    <img src="https://img.shields.io/badge/Focus-Enterprise%20Transformation-00B294?style=for-the-badge" alt="Focus" />
  </p>

  <p>
    <a href="https://linkedin.com/in/"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin" alt="LinkedIn" /></a>
    <a href="mailto:contact@subhasish.dev"><img src="https://img.shields.io/badge/Email-Get%20in%20Touch-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Email" /></a>
    <a href="#-architecture--engineering-dna"><img src="https://img.shields.io/badge/Architecture-Enterprise%20Portfolio-FF9900?style=flat-square&logo=diagram-next&logoColor=white" alt="Portfolio" /></a>
  </p>

  <table align="center">
    <tr>
      <td align="center">🏢 <strong>100+ Workloads Migrated</strong><br/>Zero-Downtime Migration Strategy</td>
      <td align="center">🛡️ <strong>Zero-Trust Architecture</strong><br/>Shift-Left DevSecOps & Governance</td>
      <td align="center">💰 <strong>28%+ FinOps Savings</strong><br/>Rightsizing, RIs & Automated Ops</td>
      <td align="center">🤖 <strong>AI-Native Automation</strong><br/>Self-Healing & Agentic Workflows</td>
    </tr>
  </table>

</div>

---

## 📌 Executive Summary & Engineering DNA

I design resilient cloud platforms, architect enterprise landing zones, and automate delivery pipelines for mission-critical modern organizations. With **9.5+ years of total IT experience** including **5.5+ years dedicated to DevOps, Cloud Architecture, and Platform Engineering**, I bridge the strategic gap between high-level business goals and ground-level technical execution.

I don’t just build CI/CD pipelines — **I architect scalable, secure, and self-governing systems that accelerate business velocity and eliminate risk from Day 1.**

---

## 🏛️ The 10 Core Pillars of Scalability & Quality

```
+--------------------------------------------------------------------------------------------------+
|                                    10 Scalability & Quality Pillars                               |
|                                                                                                  |
|  1. Scalable      2. Robust        3. Secure        4. Reliable       5. Portable                |
|  6. Governed      7. High Avail    8. Cost-Optim    9. Backed Up      10. Compliant & Monitored  |
+--------------------------------------------------------------------------------------------------+
```

---

## 🌐 1. Enterprise Hub-and-Spoke Networking Architecture

Centralized ingress, egress, and inter-spoke traffic inspection with Zero-Trust network micro-segmentation:

```mermaid
flowchart TD
    subgraph OnPrem["🏢 On-Premises Datacenter"]
        DC["Corporate Network & Data Center"]
    end

    DC -->|ExpressRoute / S2S VPN| GW["VPN / ER GatewaySubnet"]

    subgraph Hub["☁️ Hub VNet (Central Connectivity & Security)"]
        GW
        FW["Azure Firewall Premium / NVA (Inspection & TLS)"]
        DNS["Private DNS Zones Resolver"]
        Bastion["Azure Bastion"]
    end

    GW --> FW

    FW -->|"VNet Peering + UDR (0.0.0.0/0)"| Spoke1["📦 Spoke 1: App VNet (Workloads)"]
    FW -->|"VNet Peering + UDR (0.0.0.0/0)"| Spoke2["🛠️ Spoke 2: Shared Services VNet"]

    subgraph Spoke1["📦 Spoke 1: Workload Spoke"]
        AppSubnet["App Subnet (VMSS / AKS / App Services)"]
        DBSubnet["Database Subnet (Private Endpoints)"]
        PE["Private Endpoints (Key Vault, SQL, Storage)"]
        AppSubnet --> DBSubnet
        DBSubnet --> PE
    end

    subgraph Spoke2["🛠️ Spoke 2: Shared Services"]
        Runners["Self-Hosted CI/CD Runners"]
        SecTools["Security & Observability Agents"]
    end
```

### Key Architectural Standards
* **IPAM & Non-Overlapping CIDR:** Meticulous address allocation ensuring zero overlapping subnets between on-prem and multi-region Azure VNets.
* **Forced Tunneling via UDRs:** User-Defined Routes forcing all default internet-bound (`0.0.0.0/0`) and spoke-to-spoke traffic through the Azure Firewall / NVA.
* **Zero Public IP Surface:** 100% private PaaS ingestion via **Private Endpoints** and centralized Azure Private DNS Zones.
* **Controlled Ingress/Egress:** WAF-enabled Azure Application Gateway / Front Door for Layer 7 web security; Centralized Egress with SNAT and TLS Inspection.

---

## 🏢 2. Cloud Adoption Framework (CAF) & Governance Hierarchy

A structured tenant, management group, and subscription hierarchy designed for strict blast-radius isolation and automated policy guardrails:

```mermaid
flowchart TD
    Tenant["🏢 Microsoft Entra ID Tenant"]
    Root["📂 Tenant Root Group"]

    Tenant --> Root

    Root --> MG_Platform["⚙️ Platform Management Group"]
    Root --> MG_LZ["🚀 Landing Zones (Workloads)"]
    Root --> MG_Decom["📦 Decommissioned / Sandbox"]

    MG_Platform --> Sub_Ident["🔑 Identity (Entra Domain Services, DNS)"]
    MG_Platform --> Sub_Mgmt["📊 Management (Log Analytics, Sentinel)"]
    MG_Platform --> Sub_Conn["🌐 Connectivity (Hub VNet, Firewall, VPN)"]

    MG_LZ --> MG_Corp["🔒 Corp (Internal Workloads)"]
    MG_LZ --> MG_Online["🌍 Online (Public / DMZ Workloads)"]

    MG_Corp --> Sub_Dev["🧪 Dev Subscription"]
    MG_Corp --> Sub_UAT["🔍 UAT Subscription"]
    MG_Corp --> Sub_Prod["🔥 Production Subscription"]

    MG_Decom --> Sub_Sandbox["🏖️ Sandbox Subscription"]
```

### Governance & Compliance Best Practices
- **Subscription Blast-Radius Isolation:** Workloads separated strictly by environment (`Dev`, `UAT`, `Prod`) and function (`Platform` vs `Workloads`).
- **Policy as Code (Azure Policy Initiatives):** Enforcing **CIS Azure Benchmark** and **Microsoft Cloud Security Benchmark (MCSB)** at Management Group levels with `Deny` and `AuditIfNotExists` effects.
- **Just-In-Time Privilege (PIM):** Microsoft Entra ID Privileged Identity Management with approval workflows, time-bound role activations, and multi-factor authentication.

---

## 🛡️ 3. Shift-Left DevSecOps Pipeline Architecture

Automated Infrastructure as Code (IaC) governance, security scanning, cost forecasting, and release orchestration:

```mermaid
flowchart LR
    Dev["👨‍💻 Engineer"] -->|"Git Commit"| PR["Pull Request (Trunk-Based)"]

    subgraph CI["🔄 Shift-Left Security & Validation CI"]
        PR --> Lint["Lint & Format (tflint, terraform fmt)"]
        Lint --> SecScan["Security Scanners (Checkov, tfsec, Trivy)"]
        SecScan --> Secrets["Secrets Scanning (GitLeaks)"]
        Secrets --> Cost["Cost Estimation (Infracost)"]
        Cost --> Plan["Terraform Plan & Drift Check"]
    end

    subgraph Gate["🛡️ Governance Gate"]
        Plan --> PeerReview["2+ Senior Approvals (CODEOWNERS)"]
        PeerReview --> ChangeApproval["Automated CAB / Approval Gate"]
    end

    subgraph CD["🚀 Automated Delivery CD"]
        ChangeApproval --> Apply["Terraform Apply (Blob State Lock)"]
        Apply --> Telemetry["Drift Telemetry & Observability"]
        Apply -.->|"Failure Detected"| Rollback["Automated Rollback Engine"]
    end
```

### DevSecOps Governance Highlights
- **Trunk-Based Development:** Short-lived feature branches (`feature/*`, `fix/*`) with mandatory PR reviews, branch protection, and code owner sign-offs.
- **Hardened State Storage:** Encrypted Azure Storage Accounts with blob lease locking, RBAC via Managed Identities, and private network restrictions.
- **Continuous Drift Detection:** Nightly scheduled automation pipelines running `terraform plan -detailed-exitcode` to immediately detect and remediate console drift.

---

## 🔄 4. Enterprise 100+ Workload Cloud Migration Playbook

Battle-tested framework for large-scale, zero-downtime datacenter modernization:

```mermaid
flowchart LR
    A["1. Discovery<br/>• Azure Migrate<br/>• Asset Inventory<br/>• Dependency Mapping"] --> B["2. Assessment<br/>• TCO & ROI Analysis<br/>• 7-Rs Strategy<br/>• Wave Planning"]
    B --> C["3. Landing Zone<br/>• CAF Architecture<br/>• Identity & IPAM<br/>• Connectivity Ready"]
    C --> D["4. Cutover<br/>• DB Data Sync<br/>• DNS TTL Reduction<br/>• Zero Downtime"]
    D --> E["5. Hypercare<br/>• 24x7 War Room<br/>• Performance Baseline<br/>• Telemetry Audit"]
```

### End-to-End Migration Checklist
* **Pre-Migration:** Workload discovery reports, network bandwidth sizing, VM family right-sizing, target Landing Zone certification, and rollback planning.
* **Migration Cutover Window:** Live database replication sync, maintenance window orchestration, DNS failover cutover, and smoke test sign-off.
* **Post-Migration & Hypercare:** Health telemetry audit, latency validation, end-user sanity verification, and 2-4 weeks of dedicated war room support.

---

## 🔒 5. Multi-Layered Defense-in-Depth Security Matrix

| Layer | Key Controls, Policies & Technologies |
| :--- | :--- |
| **Identity & Access** | Microsoft Entra ID, Conditional Access, Multi-Factor Authentication (MFA), Privileged Identity Management (PIM), Managed Identities (No hardcoded credentials). |
| **Network Security** | Hub-and-Spoke topology, NSGs/ASGs micro-segmentation, Azure Firewall Premium with TLS inspection, Private Endpoints, DDoS Protection Standard. |
| **Governance & Policy** | Management Group policy enforcement, CIS Azure Benchmarks, ISO 27001 compliance standards, Microsoft Defender for Cloud Secure Score. |
| **Data & Storage** | Customer Managed Keys (CMK), Azure Key Vault with automated rotation, storage SSE with double encryption, TLS 1.3 enforcement. |
| **Compute & Workloads** | Microsoft Defender for Servers, automated vulnerability scanning, golden images via Packer, Azure Update Manager baseline patching. |

---

## 💰 6. FinOps & Cloud Economics Engineering

Cloud financial governance focused on eliminating waste, driving unit economics, and maximizing ROI:

- **Waste Elimination:** Automated serverless routines discovering and purging orphaned managed disks, unassociated Public IPs, and aged VM snapshots.
- **Resource Rightsizing:** Continuous CPU/Memory percentile profiling to downscale idle instances and eliminate over-provisioning.
- **Commitment Optimization:** 1-Year / 3-Year **Reserved Instances (RI)** and **Azure Savings Plans** tailored for predictable baseline workloads.
- **Non-Prod Auto-Scheduling:** Automated stop/start schedules for Dev and Test environments outside business hours (**saves ~65% on non-prod compute**).
- **Log Ingestion Tuning:** Tailoring Azure Monitor Data Collection Rules (DCR) to filter out high-volume debug logs before reaching Log Analytics.

---

## ⚡ 7. High Availability, BCDR & Reliability Engineering

Architecting systems engineered to survive datacenter disruptions and regional disasters:

```mermaid
flowchart TD
    subgraph Primary["📍 Primary Azure Region (Active)"]
        direction TB
        LB["Azure Load Balancer / App Gateway"]
        subgraph AZ["Availability Zones (Multi-Zone)"]
            VMSS1["VMSS Zone 1"]
            VMSS2["VMSS Zone 2"]
            VMSS3["VMSS Zone 3"]
        end
        LB --> VMSS1 & VMSS2 & VMSS3
        DB_Pri[("Azure SQL / Cosmos (Primary)")]
        Storage_Pri["Zone-Redundant Storage (ZRS)"]
    end

    subgraph Secondary["📍 Secondary Paired Region (DR Standby)"]
        direction TB
        ASR["Azure Site Recovery (ASR)"]
        DB_Sec[("Geo-Replicated Database (Standby)")]
        Storage_Sec["Geo-Redundant Storage (GRS)"]
    end

    VMSS1 -.->|"Replication via ASR"| ASR
    DB_Pri -->|"Active Geo-Replication"| DB_Sec
    Storage_Pri -->|"Underlying Storage Replication"| Storage_Sec
```

### Resilience Standards
- **RTO (Recovery Time Objective):** `< 30 Minutes` for mission-critical core services.
- **RPO (Recovery Point Objective):** `< 5 Minutes` utilizing continuous asynchronous geo-replication.
- **Storage Redundancy Models:** 
  - **LRS:** 3 copies within one datacenter.
  - **ZRS:** 3 copies synchronously across 3 independent Availability Zones.
  - **GRS:** Asynchronous replication to a secondary paired geographical region.

---

## 📊 8. Enterprise Observability & SRE Operations

- **Unified Log Analytics:** Centralized Log Analytics Workspace per enterprise landing zone with centralized retention policies.
- **Azure Monitor Agent (AMA):** Granular data filtering at source via **Data Collection Rules (DCR)** to balance observability depth with log ingestion costs.
- **Intelligent Alerting:** Dynamic Metric Alerts, Health Alerts, and Log Queries routed dynamically via Action Groups to **PagerDuty**, **Slack**, and **Microsoft Teams**.

---

## 🤝 9. Technical Leadership, Governance & Vendor Management

High-impact technology delivery requires rigorous operational governance, structured vendor evaluation, and team upskilling:

```
[ RFI (Request for Information) ]
               │
[ RFP (Request for Proposal) ]
               │
[ Technical Evaluation Matrix (Architecture, Security, FinOps) ]
               │
[ Statement of Work (SOW) & Commercial Negotiation ]
               │
[ Sprint Delivery & Milestone Verification ]
               │
[ Acceptance Criteria Sign-Off & Final Transition ]
```

### Governance Methodologies
* **Statement of Work (SOW) Formulation:** Clear definition of deliverables, SLAs, acceptance criteria, milestone payments, and liability caps.
* **RACI Framework Execution:**
  * **R**esponsible: Engineers executing implementation tasks.
  * **A**ccountable: Lead Architect holding single ownership of delivery success.
  * **C**onsulted: Security, compliance, and enterprise architects providing inputs.
  * **I**nformed: Executive business sponsors and client stakeholders.
* **Mentorship & Knowledge Transfer (KT):** Driving architecture review boards, weekly engineering brown-bags, and comprehensive Architecture Decision Records (ADRs).

---

## 🧰 Tech Stack & Tooling Ecosystem

<div align="center">

| Domain | Technologies |
| :--- | :--- |
| **Cloud Platforms** | ![Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=flat-square&logo=microsoft-azure&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white) |
| **IaC & Automation** | ![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white) ![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white) ![Bicep](https://img.shields.io/badge/Azure_Bicep-0078D4?style=flat-square&logo=microsoft&logoColor=white) |
| **CI/CD & GitOps** | ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white) ![Azure DevOps](https://img.shields.io/badge/Azure_DevOps-0078D7?style=flat-square&logo=azure-devops&logoColor=white) ![GitLab](https://img.shields.io/badge/GitLab_CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white) ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white) |
| **Containers & Orch** | ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white) |
| **DevSecOps & Shift-Left** | ![Checkov](https://img.shields.io/badge/Checkov-1E88E5?style=flat-square) ![Trivy](https://img.shields.io/badge/Trivy-1772B4?style=flat-square) ![GitLeaks](https://img.shields.io/badge/GitLeaks-E53935?style=flat-square) ![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat-square&logo=sonarqube&logoColor=white) |
| **FinOps & Cost Control** | ![Infracost](https://img.shields.io/badge/Infracost-00D084?style=flat-square) ![Azure Cost Mgmt](https://img.shields.io/badge/Azure_Cost_Management-0078D4?style=flat-square) |
| **Observability** | ![Azure Monitor](https://img.shields.io/badge/Azure_Monitor-0078D4?style=flat-square) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white) |
| **Languages & Scripting** | ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white) ![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) |

</div>

---

## 📈 GitHub Stats & Activity

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=subhasishmaiti16-riddhish&show_icons=true&theme=radical&hide_border=true&count_private=true" alt="GitHub Stats" width="48%" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=subhasishmaiti16-riddhish&layout=compact&theme=radical&hide_border=true" alt="Top Languages" width="48%" />
</div>

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=subhasishmaiti16-riddhish&theme=radical&hide_border=true" alt="GitHub Streak" width="96%" />
</p>

---

## 💬 Let's Connect

I am open to discussions on **Enterprise Cloud Migrations**, **Zero-Trust DevSecOps Transformations**, **Platform Engineering Leadership**, and **AI-Driven Cloud Operations**.

<p align="center">
  <a href="https://linkedin.com/in/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:contact@subhasish.dev"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

<p align="center">
  <em>"Built for enterprise impact. Engineered for high availability. Designed for the future."</em>
</p>

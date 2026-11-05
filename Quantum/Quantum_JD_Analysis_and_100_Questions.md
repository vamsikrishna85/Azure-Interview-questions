# JD Analysis & 100 Scenario Questions

Sections 1–3: full question bank with detailed answers, troubleshooting, commands and code

Senior Azure Cloud / DevOps Engineer — Interview Preparation Pack

All incidents and scenarios in this document are **illustrative examples** for interview practice. They are not claims about your personal work history. When you use them in the interview, frame them as "In a situation like this, I would…" or adapt them honestly to your own experience.

## Table of Contents

*Click any entry to jump to that section.*

[**How to Use This Document**](#how-to-use-this-document)

[**Section 1 — Job Description Analysis**](#section-1-job-description-analysis)

> [What This Role Really Is](#what-this-role-really-is)
>
> [Topic Ranking by Interview Importance](#topic-ranking-by-interview-importance)
>
> [Most Likely Scenario Questions](#most-likely-scenario-questions)
>
> [Architecture and Design Questions to Expect](#architecture-and-design-questions-to-expect)
>
> [Hands-On Azure DevOps and Terraform Questions](#hands-on-azure-devops-and-terraform-questions)
>
> [Senior and Leadership Questions](#senior-and-leadership-questions)

[**Section 2A — Azure RBAC and Identity Management (15 Questions)**](#section-2a-azure-rbac-and-identity-management-15-questions)

> [A1. Contributor cannot assign roles](#a1-contributor-cannot-assign-roles)
>
> [A2. Expired service principal credential breaks the pipeline](#a2-expired-service-principal-credential-breaks-the-pipeline)
>
> [A3. Designing a least-privilege RBAC model](#a3-designing-a-least-privilege-rbac-model)
>
> [A4. Managed identity vs service principal](#a4-managed-identity-vs-service-principal)
>
> [A5. Creating a custom RBAC role](#a5-creating-a-custom-rbac-role)
>
> [A6. Privileged Identity Management (PIM)](#a6-privileged-identity-management-pim)
>
> [A7. Access reviews and removing stale access](#a7-access-reviews-and-removing-stale-access)
>
> [A8. Key Vault access denied](#a8-key-vault-access-denied)
>
> [A9. Azure DevOps service connection design](#a9-azure-devops-service-connection-design)
>
> [A10. Security incident: excessive permissions abused](#a10-security-incident-excessive-permissions-abused)
>
> [A11. Role assigned but user still gets access denied](#a11-role-assigned-but-user-still-gets-access-denied)
>
> [A12. Management groups and subscription design](#a12-management-groups-and-subscription-design)
>
> [A13. Users, groups and guest access](#a13-users-groups-and-guest-access)
>
> [A14. AKS RBAC and workload identity](#a14-aks-rbac-and-workload-identity)
>
> [A15. Auditing RBAC changes](#a15-auditing-rbac-changes)

[**Section 2B — Azure Monitoring and Observability (20 Questions)**](#section-2b-azure-monitoring-and-observability-20-questions)

> [B1. App Service suddenly returns HTTP 500](#b1-app-service-suddenly-returns-http-500)
>
> [B2. VM CPU consistently above 90%](#b2-vm-cpu-consistently-above-90)
>
> [B3. Application Insights stopped receiving telemetry](#b3-application-insights-stopped-receiving-telemetry)
>
> [B4. Azure Monitor architecture](#b4-azure-monitor-architecture)
>
> [B5. Centralised logging for 100+ resources](#b5-centralised-logging-for-100-resources)
>
> [B6. Designing proactive alerting](#b6-designing-proactive-alerting)
>
> [B7. Reducing alert noise](#b7-reducing-alert-noise)
>
> [B8. Action groups and notification design](#b8-action-groups-and-notification-design)
>
> [B9. Building custom monitoring dashboards](#b9-building-custom-monitoring-dashboards)
>
> [B10. Writing KQL for incident investigation](#b10-writing-kql-for-incident-investigation)
>
> [B11. Metrics vs logs vs traces](#b11-metrics-vs-logs-vs-traces)
>
> [B12. Distributed tracing across microservices](#b12-distributed-tracing-across-microservices)
>
> [B13. Application performance monitoring](#b13-application-performance-monitoring)
>
> [B14. Azure Monitor Agent and Data Collection Rules](#b14-azure-monitor-agent-and-data-collection-rules)
>
> [B15. Diagnostic settings](#b15-diagnostic-settings)
>
> [B16. Log Analytics workspace design and retention](#b16-log-analytics-workspace-design-and-retention)
>
> [B17. Container and AKS monitoring](#b17-container-and-aks-monitoring)
>
> [B18. Availability tests and synthetic monitoring](#b18-availability-tests-and-synthetic-monitoring)
>
> [B19. Log Analytics ingestion failure / data missing](#b19-log-analytics-ingestion-failure-data-missing)
>
> [B20. Leading a production incident using monitoring data](#b20-leading-a-production-incident-using-monitoring-data)

[**Section 2C — Azure Scalability and Performance (15 Questions)**](#section-2c-azure-scalability-and-performance-15-questions)

> [C1. Slow at 20,000 concurrent users](#c1-slow-at-20000-concurrent-users)
>
> [C2. AKS intermittent latency and pod restarts](#c2-aks-intermittent-latency-and-pod-restarts)
>
> [C3. App Service scaling options](#c3-app-service-scaling-options)
>
> [C4. VM Scale Sets and autoscale failure](#c4-vm-scale-sets-and-autoscale-failure)
>
> [C5. Azure Load Balancer troubleshooting](#c5-azure-load-balancer-troubleshooting)
>
> [C6. Application Gateway 502 errors](#c6-application-gateway-502-errors)
>
> [C7. Front Door for global performance and failover](#c7-front-door-for-global-performance-and-failover)
>
> [C8. High availability with Availability Zones](#c8-high-availability-with-availability-zones)
>
> [C9. Disaster recovery across regions](#c9-disaster-recovery-across-regions)
>
> [C10. Azure SQL database latency](#c10-azure-sql-database-latency)
>
> [C11. Network troubleshooting between Azure services](#c11-network-troubleshooting-between-azure-services)
>
> [C12. Caching strategy with Azure Cache for Redis](#c12-caching-strategy-with-azure-cache-for-redis)
>
> [C13. Asynchronous processing for scale (Service Bus / Functions)](#c13-asynchronous-processing-for-scale-service-bus-functions)
>
> [C14. Reducing application latency end to end](#c14-reducing-application-latency-end-to-end)
>
> [C15. Kubernetes scaling: HPA, KEDA and cluster autoscaler](#c15-kubernetes-scaling-hpa-keda-and-cluster-autoscaler)

[**Section 2D — Azure Cost Optimisation (10 Questions)**](#section-2d-azure-cost-optimisation-10-questions)

> [D1. Bill jumps from \$20,000 to \$35,000](#d1-bill-jumps-from-20000-to-35000)
>
> [D2. Azure Advisor and rightsizing VMs](#d2-azure-advisor-and-rightsizing-vms)
>
> [D3. Budgets and cost alerts](#d3-budgets-and-cost-alerts)
>
> [D4. Reserved Instances vs Savings Plans](#d4-reserved-instances-vs-savings-plans)
>
> [D5. Finding and removing unused resources](#d5-finding-and-removing-unused-resources)
>
> [D6. Storage lifecycle management](#d6-storage-lifecycle-management)
>
> [D7. AKS cost optimisation](#d7-aks-cost-optimisation)
>
> [D8. Log Analytics ingestion cost](#d8-log-analytics-ingestion-cost)
>
> [D9. Tagging and cost governance](#d9-tagging-and-cost-governance)
>
> [D10. Building a FinOps practice](#d10-building-a-finops-practice)

[**Section 2E — Azure DevOps and CI/CD (15 Questions)**](#section-2e-azure-devops-and-cicd-15-questions)

> [E1. Production deployment fails halfway](#e1-production-deployment-fails-halfway)
>
> [E2. Pipeline works in development but fails in production](#e2-pipeline-works-in-development-but-fails-in-production)
>
> [E3. Designing a multi-stage YAML pipeline](#e3-designing-a-multi-stage-yaml-pipeline)
>
> [E4. Deployment approvals and checks](#e4-deployment-approvals-and-checks)
>
> [E5. Secrets management in pipelines](#e5-secrets-management-in-pipelines)
>
> [E6. Azure Key Vault integration end to end](#e6-azure-key-vault-integration-end-to-end)
>
> [E7. Docker image builds and best practices](#e7-docker-image-builds-and-best-practices)
>
> [E8. Azure Container Registry security and authentication failures](#e8-azure-container-registry-security-and-authentication-failures)
>
> [E9. Deploying to AKS safely](#e9-deploying-to-aks-safely)
>
> [E10. Rollback strategies](#e10-rollback-strategies)
>
> [E11. Blue-green deployments](#e11-blue-green-deployments)
>
> [E12. Canary deployments](#e12-canary-deployments)
>
> [E13. CI/CD security (supply chain)](#e13-cicd-security-supply-chain)
>
> [E14. Azure Repos branching and PR strategy](#e14-azure-repos-branching-and-pr-strategy)
>
> [E15. Terraform in Azure DevOps pipelines](#e15-terraform-in-azure-devops-pipelines)

[**Section 2F — Terraform and Infrastructure as Code (10 Questions)**](#section-2f-terraform-and-infrastructure-as-code-10-questions)

> [F1. Remote backend in Azure Storage](#f1-remote-backend-in-azure-storage)
>
> [F2. Two engineers run terraform apply simultaneously](#f2-two-engineers-run-terraform-apply-simultaneously)
>
> [F3. Manually deleted resource managed by Terraform](#f3-manually-deleted-resource-managed-by-terraform)
>
> [F4. Terraform modules for multiple teams](#f4-terraform-modules-for-multiple-teams)
>
> [F5. Terraform plan and apply workflow](#f5-terraform-plan-and-apply-workflow)
>
> [F6. Terraform import](#f6-terraform-import)
>
> [F7. Infrastructure drift detection](#f7-infrastructure-drift-detection)
>
> [F8. Terraform authentication to Azure](#f8-terraform-authentication-to-azure)
>
> [F9. Troubleshooting Terraform errors](#f9-troubleshooting-terraform-errors)
>
> [F10. Bicep vs Terraform](#f10-bicep-vs-terraform)

[**Section 2G — Azure Security and Governance (10 Questions)**](#section-2g-azure-security-and-governance-10-questions)

> [G1. Azure Policy for guardrails](#g1-azure-policy-for-guardrails)
>
> [G2. Microsoft Defender for Cloud](#g2-microsoft-defender-for-cloud)
>
> [G3. Network Security Groups](#g3-network-security-groups)
>
> [G4. Private Endpoints and DNS](#g4-private-endpoints-and-dns)
>
> [G5. Managed identities as a security control](#g5-managed-identities-as-a-security-control)
>
> [G6. Key Vault security hardening](#g6-key-vault-security-hardening)
>
> [G7. Azure Firewall and hub-spoke security](#g7-azure-firewall-and-hub-spoke-security)
>
> [G8. Zero Trust on Azure](#g8-zero-trust-on-azure)
>
> [G9. Compliance requirements](#g9-compliance-requirements)
>
> [G10. Security incident response on Azure](#g10-security-incident-response-on-azure)

[**Section 2H — Leadership and Architecture (5 Questions)**](#section-2h-leadership-and-architecture-5-questions)

> [H1. Mentoring engineers](#h1-mentoring-engineers)
>
> [H2. Architecture decision-making](#h2-architecture-decision-making)
>
> [H3. Incident management leadership](#h3-incident-management-leadership)
>
> [H4. Communicating with leadership](#h4-communicating-with-leadership)
>
> [H5. Prioritising reliability, security and cost](#h5-prioritising-reliability-security-and-cost)

# How to Use This Document

This is the full question bank. Document 1 (Top 30 + Revision Plan) is the short version for tonight. Use this document to go deeper on any topic, especially the areas marked **Critical** in Section 1.

Every question uses the same structure: **Question → Scenario → Interview Answer → Technical Deep Dive → Step-by-Step Troubleshooting → Azure Portal Steps → Commands/Code → Root Cause → Prevention → Follow-Up Questions → Common Mistakes → Key Points.**

> **Honesty rule:** The scenarios are realistic examples, not your work history. In the interview, say "In a situation like this, I would…" or connect them to something you have actually done.

**Fact vs assumption:** Statements about how Azure behaves are written as facts and reflect Microsoft's current documentation as of late 2026. Where a design choice depends on the organisation, it is written as a recommendation ("I would…", "usually…"). Azure features change; if an interviewer mentions a newer feature, say you would check the current docs.

# Section 1 — Job Description Analysis

## What This Role Really Is

The JD describes a **senior platform / SRE-style engineer** who owns Azure foundations for other teams: who can access what (RBAC), how everything is observed (monitoring), how it scales, what it costs, how it is deployed (CI/CD + IaC), and how other engineers are guided. The words *design*, *implement*, *enforce*, *establish* and *advise* signal that they want someone who sets standards, not only someone who follows tickets.

The "Essential" list repeats monitoring three times (custom dashboards, centralised logging, proactive alerting). **Expect monitoring to be the deepest part of the interview.**

## Topic Ranking by Interview Importance

| **Topic**                                                        | **Priority** | **Why**                                   | **Expect deep follow-ups?**                           |
|------------------------------------------------------------------|--------------|-------------------------------------------|-------------------------------------------------------|
| Azure RBAC, Entra ID groups, service principals, least privilege | Critical     | First JD section; essential requirement   | Yes — role definitions, scopes, PIM, managed identity |
| Azure Monitor, Log Analytics, Application Insights               | Critical     | Three essential requirements              | Yes — KQL, AMA/DCR, diagnostic settings               |
| Custom dashboards and Workbooks                                  | Critical     | Explicit essential requirement            | Medium — design choices, as-code                      |
| Proactive alerting and alert noise                               | Critical     | Explicit essential requirement            | Yes — alert types, action groups, dynamic thresholds  |
| Production troubleshooting                                       | Critical     | Essential requirement; scenario questions | Yes — step-by-step reasoning                          |
| Azure DevOps YAML CI/CD                                          | Critical     | Essential requirement                     | Yes — environments, approvals, service connections    |
| Scalable architecture and performance                            | Critical     | Essential requirement                     | Yes — autoscale, caching, data tier                   |
| Cost optimisation and governance                                 | High         | JD section; essential requirement         | Medium — Cost analysis, tags, commitments             |
| Terraform (state, modules, pipelines)                            | High         | Desirable + DevOps section                | Yes — state locking, drift, import                    |
| Docker, AKS                                                      | High         | DevOps section; desirable                 | Yes — pod troubleshooting, ACR                        |
| Security best practices (Key Vault, Policy, Private Endpoints)   | High         | "Enforce security best practices"         | Medium                                                |
| Technical leadership and mentoring                               | High         | JD section; essential requirement         | Behavioural follow-ups                                |
| Bicep                                                            | Medium       | Mentioned in DevOps section               | Comparison with Terraform                             |
| Azure Functions / serverless                                     | Medium       | Desirable                                 | Hosting plans, scaling, cold start                    |
| PowerShell / Bash                                                | Medium       | Desirable                                 | Write a quick script                                  |
| UK business-hours collaboration                                  | Medium       | Essential (soft)                          | Availability, communication                           |
| Certifications (AZ-305 / AZ-400)                                 | Medium       | Desirable                                 | Mention if held or in progress                        |

## Most Likely Scenario Questions

- Contributor cannot assign roles; expired service principal; access denied after role assignment.

- App Service HTTP 500s; VM high CPU; App Insights missing data; noisy alerts.

- App slow at high user count; AKS pod restarts; App Gateway 502.

- Bill jumps from \$20k to \$35k; Log Analytics too expensive.

- Deployment fails halfway; pipeline works in dev but not prod.

- Terraform resource deleted manually; two engineers apply at once.

## Architecture and Design Questions to Expect

Centralised monitoring for 100+ resources · enterprise RBAC model · HA web app across zones/regions · AKS platform · secure CI/CD · private networking for PaaS · DR across regions · Terraform module structure for many teams.

## Hands-On Azure DevOps and Terraform Questions

Write or explain a multi-stage YAML pipeline · environments and approvals · service connections with workload identity federation · Key Vault in pipelines · template/extends · Terraform remote backend, locking, force-unlock, import blocks, drift detection, module versioning, plan-in-PR/apply-in-pipeline.

## Senior and Leadership Questions

How you set standards · mentoring · disagreeing with an architect · prioritising reliability vs security vs cost · communicating during incidents · leading a post-incident review.

# Section 2A — Azure RBAC and Identity Management (15 Questions)

## A1. Contributor cannot assign roles

**Question:** An engineer has Contributor access on a subscription but gets an authorisation error when trying to assign a role to another user. How would you troubleshoot and resolve this?

**Scenario:** A team lead with Contributor on sub-payments-prod tries to give a new developer Reader in the portal and sees "You do not have permissions to add role assignments in this scope". The developer is blocked from starting work.

**Interview Answer:**

"This is expected behaviour, not a bug. The built-in Contributor role can create and manage all resources, but its definition has Microsoft.Authorization/\*/Write and Microsoft.Authorization/\*/Delete in NotActions. That means Contributor cannot create or remove role assignments.

To assign roles, you need Microsoft.Authorization/roleAssignments/write. That comes from Owner, User Access Administrator, or Role Based Access Control Administrator. I would not jump to Owner. My preferred option is Role Based Access Control Administrator at the resource group scope with a condition that limits which roles can be assigned — for example only Reader and Log Analytics Reader. Then the team lead can onboard people without the risk of giving someone Owner.

Before changing anything, I'd confirm the business need, check the user's effective permissions with Check access, and decide whether this is a one-off or a regular need. For a one-off, I or the platform team make the assignment. For a regular need, I make the constrained role eligible through PIM so it's time-bound and audited. And I'd assign the developer's access to a group rather than the individual, so future onboarding is just group membership."

**Technical Deep Dive:**

- Role definitions have Actions, NotActions, DataActions, NotDataActions. Effective permission = Actions minus NotActions. NotActions is not a deny — another role can grant it back.

- Roles that can write role assignments: **Owner**, **User Access Administrator**, **Role Based Access Control Administrator** (GA in 2024; designed to be used with conditions).

- **Conditions on role assignments** (ABAC delegation) can restrict which role definition IDs and which principal types can be assigned.

- Scope inheritance: management group → subscription → resource group → resource.

**Step-by-Step Troubleshooting:**

**1.** Confirm the exact error and the scope the user tried to assign at.

**2.** Check the user's role assignments at that scope and above (az role assignment list --assignee … --include-inherited).

**3.** Confirm Contributor is the highest role they hold; confirm no PIM role is eligible but not activated.

**4.** Confirm the business need with the manager or service owner.

**5.** Grant a constrained role (RBAC Administrator with conditions) or do the assignment centrally.

**6.** Ask the user to sign out/in or wait a few minutes for propagation, then retry.

**Azure Portal Steps:** Subscription or resource group → **Access control (IAM)** → **Check access** → select user → view effective roles. To grant: **Add → Add role assignment → Privileged administrator roles → Role Based Access Control Administrator → Conditions → Allow user to only assign selected roles**.

**Commands:**

**BASH**

\# Effective assignments including inherited ones

az role assignment list --assignee \<user-upn\> --all --include-inherited -o table

\# Show Contributor NotActions

az role definition list --name "Contributor" --query "\[0\].permissions\[0\].notActions"

\# Grant RBAC Administrator at RG scope (condition is usually added via portal or a condition string)

az role assignment create --assignee \<team-lead-object-id\> \\

--role "Role Based Access Control Administrator" \\

--scope /subscriptions/\<sub-id\>/resourceGroups/\<rg\>

**Root Cause:** By design, Contributor excludes Microsoft.Authorization write/delete. Confirm by reading the role definition.

**Prevention:** Document a role catalogue (who gets what); delegate role assignment only with conditions; manage access through Entra ID groups; use PIM for privileged roles; alert on new Owner/User Access Administrator assignments.

**Interviewer Follow-Up Questions:**

- *"Why not just give Owner?"* — Owner can assign Owner to anyone, so one compromised account can take over the subscription. It also violates least privilege and usually fails audit.

- *"How do you write a condition that blocks assigning Owner?"* — In the portal choose "Allow user to assign all roles except privileged administrator roles Owner, UAA, RBAC Administrator", or constrain to selected role IDs. The condition checks @Request\[Microsoft.Authorization/roleAssignments:RoleDefinitionId\].

- *"Assignment done but user still blocked?"* — Wait for propagation (usually minutes), refresh token by signing out, check deny assignments, and check that the user activated their PIM role.

**Common Mistakes:** Saying "Contributor is broken"; recommending Owner as the fix; assigning roles directly to individuals; forgetting PIM activation.

**Key Points to Remember:** Contributor ≠ access management · need roleAssignments/write · RBAC Administrator + conditions is the least-privilege answer · assign to groups.

## A2. Expired service principal credential breaks the pipeline

**Question:** A production service principal credential has expired and the deployment pipeline is failing. What steps would you take?

**Scenario:** At 09:00 UK time all production releases fail at the Azure login step with AADSTS7000222: The provided client secret keys for app '\<app-id\>' are expired. A hotfix is waiting.

**Interview Answer:**

"First I restore deployments, then I remove the reason this can happen again.

I'd confirm the error code — AADSTS7000222 means the secret expired. From the Azure DevOps service connection I find the app registration it uses. Then I create a new client secret on that app registration with the --append flag, so I don't remove any other credential that something else still uses. I update the service connection with the new secret, verify it, and re-run the pipeline. I also check if the same secret was copied anywhere else — another pipeline, Key Vault or an application config.

Then the permanent fix: I convert the service connection to workload identity federation. The pipeline then gets a short-lived OIDC token for each run, so there is no secret to expire, leak or rotate. Azure DevOps supports converting an existing connection in place.

Finally, I'd add monitoring for any remaining secrets — a scheduled script or Logic App that queries Microsoft Graph for credentials expiring in the next 30 days and notifies the owners. And I'd make sure each app registration has named owners."

**Technical Deep Dive:**

- An app registration (application object) holds credentials; the service principal (enterprise app) is its identity in the tenant and holds the RBAC assignments.

- **Workload identity federation**: Entra ID trusts tokens issued by Azure DevOps for a specific subject (sc://\<org\>/\<project\>/\<service-connection\>). No secret is stored.

- Error codes: **AADSTS7000222** expired secret; **AADSTS7000215** invalid secret; **AADSTS700016** application not found in tenant.

**Step-by-Step Troubleshooting:**

**1.** Read the failing task log; capture the AADSTS code.

**2.** Azure DevOps → Project settings → Service connections → open the connection → note the App (client) ID and tenant.

**3.** Entra ID → App registrations → the app → Certificates & secrets → check expiry dates.

**4.** Create a new secret (append), update the service connection, click **Verify**.

**5.** Re-run the failed stage.

**6.** Search for other uses of the old secret; plan conversion to workload identity federation.

**Azure Portal Steps:** Microsoft Entra ID → **App registrations** → All applications → search App ID → **Certificates & secrets** → **New client secret**. In Azure DevOps: **Project settings → Service connections → (connection) → Edit**, or **Convert** to workload identity federation.

**Commands:**

**BASH**

az ad app credential list --id \<app-id\> --query "\[\].{Name:displayName, End:endDateTime}" -o table

az ad app credential reset --id \<app-id\> --display-name "ado-prod-2026-11" --years 1 --append

**POWERSHELL**

\# List app registrations with secrets expiring in 30 days (Microsoft Graph PowerShell)

Connect-MgGraph -Scopes "Application.Read.All"

\$limit = (Get-Date).AddDays(30)

Get-MgApplication -All \| ForEach-Object {

foreach (\$s in \$\_.PasswordCredentials) {

if (\$s.EndDateTime -lt \$limit) {

\[pscustomobject\]@{ App = \$\_.DisplayName; AppId = \$\_.AppId; Expires = \$s.EndDateTime }

}

}

}

**Root Cause:** Client secrets have a maximum lifetime and nobody tracked expiry. Confirm via the credential's endDateTime.

**Prevention:** Workload identity federation for all pipeline connections; managed identities for Azure-hosted workloads; expiry monitoring; owners on every app registration; an Entra ID app management policy that restricts secret lifetimes.

**Interviewer Follow-Up Questions:**

- *"What if you can't access the app registration?"* — Escalate to an Application Administrator or the app owner; in the incident, document who has rights. Long term, make the platform team owner of pipeline identities.

- *"Certificate vs secret?"* — Certificates are better than secrets (private key not sent), but both expire. Federation is better than both.

- *"How do you convert without downtime?"* — The convert action keeps the same app/SP and RBAC; test with a non-prod connection first, and Azure DevOps lets you revert within a period.

**Common Mistakes:** Running credential reset without --append; creating a brand new SP (loses RBAC); pasting the secret into chat; fixing the symptom but not moving to federation.

**Key Points to Remember:** AADSTS7000222 · append new secret → update connection → re-run · convert to workload identity federation · monitor expiry.

## A3. Designing a least-privilege RBAC model

**Question:** How would you design Azure RBAC for 10 product teams across dev, test and production?

**Scenario:** A growing company has three subscriptions and 60 engineers who all have Contributor on everything. An audit flagged excessive access.

**Interview Answer:**

"I'd fix it in layers. First the structure: a management group hierarchy — for example Platform, Landing Zones split into Production and Non-production, and Sandbox. Subscriptions separate environments and, where it makes sense, workloads, because a subscription is a clear security and billing boundary.

Second, identity: no direct user assignments. Each team gets Entra ID groups per environment and function — readers, operators, contributors. Roles are assigned to groups at the lowest scope that works, usually the resource group.

Third, environment rules: in non-production, team groups can have Contributor on their resource groups. In production, the default is Reader. Contributor is eligible through PIM with MFA, justification and a time limit, and approval for the most sensitive scopes. Changes to production go through pipelines that use workload identities, not people.

Fourth, data planes: Key Vault Secrets User, Storage Blob Data Reader and so on instead of broad roles.

Finally, governance: quarterly access reviews on the privileged groups, alerts on Owner and User Access Administrator assignments, and RBAC defined in Terraform so changes are reviewed in pull requests."

**Technical Deep Dive:**

- Azure RBAC limits: role assignments per subscription are capped (currently 4,000), another reason to use groups.

- PIM supports **eligible** and **active** assignments, activation duration, approval, MFA, justification and ticket number; PIM for Groups lets you make group membership eligible.

- Entra ID roles (directory, e.g., Global Administrator) are separate from Azure RBAC roles (resources).

**Step-by-Step (implementation):**

**1.** Export current assignments; identify direct user assignments and Owner/Contributor counts.

**2.** Design management groups and group naming (grp-\<team\>-\<env\>-\<role\>).

**3.** Create groups and assign roles in Terraform.

**4.** Move users into groups; enable PIM for production elevated roles.

**5.** Remove direct user assignments in phases with communication.

**6.** Set up access reviews and alerts.

**Azure Portal Steps:** **Management groups** → create hierarchy. **Entra ID → Groups** → new security group. Scope → **Access control (IAM)** → Add role assignment → select group. **Privileged Identity Management → Azure resources** → discover resource → **Assignments → Add assignments → Eligible**.

**Terraform:**

**HCL**

resource "azuread_group" "payments_prod_readers" {

display_name = "grp-payments-prod-readers"

security_enabled = true

}

resource "azurerm_role_assignment" "payments_prod_reader" {

scope = azurerm_resource_group.payments_prod.id

role_definition_name = "Reader"

principal_id = azuread_group.payments_prod_readers.object_id

}

**Root Cause (of the audit finding):** Access granted for convenience, directly to people, never reviewed.

**Prevention:** Access reviews, PIM, RBAC-as-code, Defender for Cloud recommendations on owners and external accounts, alerting on privileged role assignment.

**Interviewer Follow-Up Questions:**

- *"How do you handle break-glass?"* — Two emergency accounts excluded from Conditional Access lockouts, long random passwords/FIDO2 keys stored securely, monitored for any sign-in.

- *"How do you migrate 60 engineers without breaking work?"* — Report-only phase, group equivalents first, then remove direct access team by team with a rollback plan.

**Common Mistakes:** Designing only roles and forgetting scope; ignoring data-plane roles; no plan for break-glass; making everything a custom role.

**Key Points to Remember:** Hierarchy → groups → lowest scope → PIM in prod → data-plane roles → reviews and alerts → as code.

## A4. Managed identity vs service principal

**Question:** When do you use a managed identity and when a service principal?

**Scenario:** A developer stores a storage account key in an App Service app setting so the app can upload files.

**Interview Answer:**

"Both are Entra ID identities for workloads. A managed identity is a special service principal whose credentials Azure creates and rotates for you, so there's no secret in config at all. I use a managed identity whenever the code runs on an Azure service that supports it — App Service, Functions, VMs, AKS through workload identity, Logic Apps, Data Factory and so on.

System-assigned identity is tied to one resource and deleted with it. User-assigned is a separate resource I can share across several resources and give RBAC before the app exists — useful for scale sets, blue-green deployments and AKS workload identity.

A service principal with credentials is for workloads outside Azure — an on-premises job or a third-party SaaS — and even there I prefer federation where the platform supports OIDC, like GitHub Actions, Azure DevOps or Kubernetes outside Azure.

For this scenario, I'd enable a managed identity on the App Service, give it Storage Blob Data Contributor on the container, change the code to use DefaultAzureCredential, then remove the key and disable shared key access on the storage account."

**Technical Deep Dive:** Managed identity tokens come from the local identity endpoint (IMDS on VMs, IDENTITY_ENDPOINT on App Service). Tokens are cached; role changes can take time to apply because tokens are cached for up to 24 hours for some services. DefaultAzureCredential tries environment, workload identity, managed identity, then developer credentials.

**Step-by-Step:** Enable identity → assign data-plane role at the narrowest scope → update code/config → deploy → verify → remove keys → disable shared key access → rotate the old key.

**Azure Portal Steps:** App Service → **Identity** → System assigned → On. Storage account → **Access control (IAM)** → Add role assignment → Storage Blob Data Contributor → Managed identity. Storage account → **Configuration** → Allow storage account key access → Disabled.

**Commands:**

**BASH**

az webapp identity assign -g \<rg\> -n \<app\>

principalId=\$(az webapp identity show -g \<rg\> -n \<app\> --query principalId -o tsv)

az role assignment create --assignee-object-id \$principalId --assignee-principal-type ServicePrincipal \\

--role "Storage Blob Data Contributor" \\

--scope /subscriptions/\<sub-id\>/resourceGroups/\<rg\>/providers/Microsoft.Storage/storageAccounts/\<sa\>/blobServices/default/containers/\<container\>

az storage account update -g \<rg\> -n \<sa\> --allow-shared-key-access false

**Root Cause:** Habit of using connection strings and keys.

**Prevention:** Azure Policy "Storage accounts should prevent shared key access"; code review standards; secret scanning.

**Interviewer Follow-Up Questions:**

- *"Managed identity gets 403 right after role assignment?"* — Propagation and token caching; wait or restart the app to get a fresh token.

- *"Can a managed identity be used across tenants?"* — Not directly; use a multi-tenant app or federated identity credentials on an app registration that trust the managed identity.

**Common Mistakes:** Giving the identity Contributor instead of a data role; forgetting to disable keys; thinking managed identity works from a laptop.

**Key Points to Remember:** No secrets · system vs user-assigned · data-plane role · disable keys.

## A5. Creating a custom RBAC role

**Question:** Built-in roles are too broad for your operations team. How do you create and manage a custom role?

**Scenario:** The NOC team must be able to start, stop and restart VMs and read monitoring data in production, but never delete or resize anything.

**Interview Answer:**

"First I check if a built-in role fits — Virtual Machine Contributor is too broad because it allows delete. So I'd create a custom role with only the actions needed: read on VMs, start, restart, deallocate/power off, plus Monitoring Reader-style read actions.

I'd define it as code — JSON or Terraform — with AssignableScopes set to the production management group or subscriptions, so it can't be used everywhere. Then I assign it to the NOC Entra ID group at the right scope.

I test it with a test account: confirm start and restart work, and confirm delete and resize fail. I avoid wildcards like Microsoft.Compute/\* because new actions added by Microsoft would be granted automatically. Custom roles are reviewed like code, and I keep the number small because each one needs maintenance."

**Technical Deep Dive:** Custom roles are tenant-wide objects with assignable scopes; limit is 5,000 custom roles per tenant. Wildcards in Actions include future operations. DataActions cover data plane. Use az provider operation show to find action names.

**Step-by-Step:** List required operations → find exact action strings → write JSON → create → assign to group → test allow and deny cases → store in repo.

**Azure Portal Steps:** Subscription → **Access control (IAM)** → **Add → Add custom role** → Start from scratch or clone → Permissions → Assignable scopes → Review + create.

**Code:**

**JSON**

{

"Name": "VM Operator (No Delete)",

"Description": "Start, restart and stop VMs and read monitoring data",

"Actions": \[

"Microsoft.Compute/virtualMachines/read",

"Microsoft.Compute/virtualMachines/instanceView/read",

"Microsoft.Compute/virtualMachines/start/action",

"Microsoft.Compute/virtualMachines/restart/action",

"Microsoft.Compute/virtualMachines/deallocate/action",

"Microsoft.Compute/virtualMachines/powerOff/action",

"Microsoft.Insights/metrics/read",

"Microsoft.Insights/alertRules/read",

"Microsoft.Resources/subscriptions/resourceGroups/read"

\],

"NotActions": \[\],

"AssignableScopes": \[ "/subscriptions/\<prod-sub-id\>" \]

}

**BASH**

az role definition create --role-definition @vm-operator.json

az provider operation show --namespace Microsoft.Compute --query "resourceTypes\[?name=='virtualMachines'\].operations\[\].name" -o tsv

**Root Cause (if role doesn't work):** Missing read action on parent resource, wrong assignable scope, or propagation delay.

**Prevention:** Custom roles in Git with PR review; periodic review of custom role usage.

**Interviewer Follow-Up Questions:**

- *"Why didn't you put delete in NotActions?"* — NotActions only subtracts from wildcards in the same role; if I don't grant it, it isn't there. It doesn't block other roles.

- *"How do you actually block deletion even for owners?"* — Resource locks (CanNotDelete) or deny assignments via deployment stacks.

**Common Mistakes:** Using wildcards; thinking NotActions is a deny; assignable scope /.

**Key Points to Remember:** Check built-in first · explicit actions · limited assignable scopes · test allow and deny · keep as code.

## A6. Privileged Identity Management (PIM)

**Question:** How would you implement PIM for production access, and what problems might engineers face?

**Scenario:** Security wants zero standing privileged access in production within one quarter.

**Interview Answer:**

"I'd onboard the production subscriptions to PIM and change Owner, Contributor and User Access Administrator assignments from active to eligible. Engineers keep Reader permanently and activate a higher role when they need it.

I'd set activation rules per role: Contributor for up to 4 hours with MFA and justification; Owner and User Access Administrator require approval from a second person. Activations notify the security channel.

I'd use PIM for Groups where possible — the group has the role, and membership is eligible — so it's simpler to manage. I'd also run access reviews every quarter on eligible assignments.

Common problems: people forget to activate, or activate and don't see access immediately because their token hasn't refreshed — they need to sign out or refresh the portal. During an incident at night, approval delays can hurt, so I'd make sure on-call has pre-approved eligibility for the operational role without approval, and break-glass accounts exist for emergencies."

**Technical Deep Dive:** PIM requires Microsoft Entra ID P2 or Entra ID Governance licences for users who benefit. Settings per role: max activation duration, MFA (or Conditional Access authentication context), justification, ticket info, approval, notifications. Audit history in PIM and Entra audit logs.

**Step-by-Step:** Inventory privileged assignments → configure role settings → create eligible assignments → communicate and train → convert active to eligible → monitor activations → access reviews.

**Azure Portal Steps:** **Microsoft Entra Privileged Identity Management → Azure resources → Manage resource** → choose subscription → **Settings** (per role) → **Assignments → Add assignments** → Assignment type: Eligible. Users: **My roles → Azure resources → Activate**.

**Commands:** PIM is usually managed in the portal, via Microsoft Graph or Terraform (azurerm_pim_eligible_role_assignment).

**HCL**

resource "azurerm_pim_eligible_role_assignment" "prod_contrib" {

scope = "/subscriptions/\<prod-sub-id\>"

role_definition_id = "/subscriptions/\<prod-sub-id\>\${data.azurerm_role_definition.contributor.id}"

principal_id = azuread_group.payments_prod_operators.object_id

schedule {

expiration { duration_days = 365 }

}

justification = "Eligible production operator access"

}

**Root Cause (common issues):** Token not refreshed; activation pending approval; role assigned at different scope; Conditional Access requiring compliant device.

**Prevention:** Clear runbook for activation; on-call exceptions; access reviews; alerts on activation of the most privileged roles.

**Interviewer Follow-Up Questions:**

- *"PIM vs Conditional Access?"* — PIM controls when you hold a role; Conditional Access controls how/where you can sign in. Use both.

- *"What about service principals?"* — PIM is for humans; for workloads use least-privilege static assignments and workload identity federation.

**Common Mistakes:** Requiring approval for everything (slows incidents); forgetting break-glass; no reviews of eligible assignments.

**Key Points to Remember:** Eligible not active · MFA + justification + time limit · approval for Owner/UAA · PIM for Groups · reviews.

## A7. Access reviews and removing stale access

**Question:** How do you make sure people who leave a team lose access?

**Scenario:** An engineer moved to another department six months ago but still has Contributor on production.

**Interview Answer:**

"Two controls: lifecycle automation and periodic reviews. Access should come from group membership, and group membership should follow HR data — for example dynamic groups based on department, or joiner-mover-leaver workflows in Entra ID Governance. When someone moves team, they drop out of the group automatically.

Then Microsoft Entra access reviews catch what automation misses. I'd configure quarterly reviews on privileged groups and Azure role assignments in production, with the group owner or manager as reviewer, and 'auto-apply results' so denied or unanswered users are removed. Guest users get reviewed more often.

For this specific case, I'd remove the access immediately, check the activity log to see whether the account made changes in production since the move, and fix the process that allowed it."

**Technical Deep Dive:** Access reviews (Entra ID Governance/P2) for groups, apps, Entra roles and Azure resource roles via PIM. Options: reviewer types, recurrence, auto-apply, default decision if no response, recommendations based on sign-in inactivity.

**Step-by-Step:** Find stale accounts → remove → audit actions → configure reviews → automate lifecycle.

**Azure Portal Steps:** **Entra ID → Identity Governance → Access reviews → New access review** → scope (Teams + groups, or Azure resource roles via PIM) → reviewers → recurrence → **Auto apply results**.

**KQL (who used the account recently):**

**KQL**

AzureActivity

\| where TimeGenerated \> ago(180d)

\| where Caller =~ "\<user-upn\>"

\| summarize Ops = count() by OperationNameValue, ResourceGroup

\| order by Ops desc

**Root Cause:** Direct assignments and no lifecycle process.

**Prevention:** Group-based access, dynamic groups, lifecycle workflows, access reviews with auto-apply.

**Interviewer Follow-Up Questions:**

- *"Reviewers just click approve all?"* — Use recommendations (inactive 30 days → deny), smaller review scopes, and track reviewer decisions.

- *"Guests?"* — Separate review, shorter recurrence, and remove from tenant if denied.

**Common Mistakes:** Manual spreadsheets; reviews without auto-apply; ignoring service principals.

**Key Points to Remember:** Groups + lifecycle automation + quarterly reviews with auto-apply.

## A8. Key Vault access denied

**Question:** An application gets 403 Forbidden when reading a secret from Key Vault. How do you troubleshoot?

**Scenario:** After moving the vault from access policies to the Azure RBAC permission model, a Function App fails with Forbidden — Caller is not authorized to perform action on resource.

**Interview Answer:**

"Key Vault 403 has three common causes: permission model, network, and identity.

First, the permission model. When a vault switches to Azure RBAC, access policies are ignored. The function's managed identity now needs a data-plane role like Key Vault Secrets User on the vault or the specific secret. Contributor on the vault does not give secret read access — that's control plane.

Second, the network. If the firewall is enabled or public access is disabled, the caller must come through an allowed network or private endpoint. The error message then mentions the client IP or 'ForbiddenByFirewall'.

Third, the identity. I confirm which identity the app actually uses — system-assigned or user-assigned — and that the client ID is correct in the code if it's user-assigned.

I'd check Key Vault diagnostic logs: the AuditEvent shows the caller object ID, the operation and the result, which tells me exactly which of these it is."

**Technical Deep Dive:** Permission models: vault access policy (legacy) vs Azure RBAC (recommended). RBAC roles: Key Vault Administrator, Secrets Officer, Secrets User, Crypto User, Certificates Officer, Reader (metadata only). Network: firewall, trusted Microsoft services, private endpoint.

**Step-by-Step:**

**1.** Read the full error message (firewall vs authorisation).

**2.** Check vault → Access configuration → permission model.

**3.** Check role assignments for the app's principal ID.

**4.** Check Networking settings and DNS resolution from the app.

**5.** Query AuditEvent logs for the caller and result.

**6.** Fix the role/network; restart app to refresh token if needed.

**Azure Portal Steps:** Key Vault → **Access configuration**; **Access control (IAM)** → Check access; **Networking** → Firewalls and virtual networks / Private endpoint connections; **Logs**.

**KQL:**

**KQL**

AzureDiagnostics

\| where ResourceProvider == "MICROSOFT.KEYVAULT" and TimeGenerated \> ago(1h)

\| where httpStatusCode_d \>= 400

\| project TimeGenerated, OperationName, httpStatusCode_d, ResultSignature, identity_claim_oid_g, CallerIPAddress, requestUri_s

\| order by TimeGenerated desc

> If diagnostic settings use resource-specific mode, query the AZKVAuditLogs table instead of AzureDiagnostics.

**Commands:**

**BASH**

az keyvault show -n \<kv\> --query "properties.enableRbacAuthorization"

az role assignment create --assignee-object-id \<principal-id\> --assignee-principal-type ServicePrincipal \\

--role "Key Vault Secrets User" --scope \$(az keyvault show -n \<kv\> --query id -o tsv)

**Root Cause:** Permission model changed without migrating access policies to RBAC roles.

**Prevention:** Migrate with a mapping checklist; test in non-prod; Key Vault diagnostic logs and an alert on 403 spikes.

**Interviewer Follow-Up Questions:**

- *"Why RBAC over access policies?"* — Consistent with Azure RBAC, works with PIM, per-secret scope, and access policies allowed privilege escalation by Contributors who could edit policies.

- *"App Service Key Vault reference shows an error status?"* — Check the reference status in Configuration, identity used (keyVaultReferenceIdentity), and network.

**Common Mistakes:** Granting Contributor to read secrets; forgetting the vault firewall; not checking which identity is used.

**Key Points to Remember:** Model (RBAC vs policy) · network · identity · AuditEvent logs.

## A9. Azure DevOps service connection design

**Question:** How do you design Azure DevOps service connections securely for multiple environments?

**Scenario:** One service connection with Owner on the whole tenant root is used by all pipelines.

**Interview Answer:**

"That's a big risk — any pipeline in the project could change anything. I'd split it: one service connection per environment and per workload area, each using workload identity federation, each with the minimum role at the right scope — usually Contributor on the target resource groups. If a pipeline must assign roles, I'd give it RBAC Administrator with a condition, not Owner.

Then I'd protect the connections in Azure DevOps: restrict 'pipeline permissions' so only approved pipelines can use the production connection, and add approvals and checks on the connection itself — branch control so only main can use it, required template, and an approval. Project-level permissions limit who can edit the connection.

That way, even if someone writes a malicious YAML in a feature branch, it can't use production credentials."

**Technical Deep Dive:** Service connection security: user permissions (Reader/User/Creator/Administrator), pipeline permissions (open access vs specific pipelines), approvals and checks (approval, branch control, business hours, required template, exclusive lock, Azure Function/REST checks). Federation subject is unique per connection.

**Step-by-Step:** Inventory connections → create new federated connections per env → assign minimal RBAC → restrict pipelines → add checks → migrate pipelines → delete old connection.

**Azure Portal / ADO Steps:** **Project settings → Service connections → New → Azure Resource Manager → Workload identity federation (automatic)** → scope subscription/RG. Open connection → **⋮ → Security** (pipeline permissions) and **Approvals and checks**.

**YAML:**

**YAML**

\- task: AzureCLI@2

inputs:

azureSubscription: sc-payments-prod-wif \# restricted, checked connection

scriptType: bash

scriptLocation: inlineScript

inlineScript: az group show -n rg-payments-prod

**Root Cause:** Convenience; connection created once and reused.

**Prevention:** Standards for connection creation; periodic audit of connection RBAC; branch control checks.

**Interviewer Follow-Up Questions:**

- *"How would an attacker abuse an open connection?"* — Create a branch, edit YAML to run az commands with the connection, exfiltrate data or create backdoor role assignments. Branch control and pipeline permissions stop this.

- *"Manual vs automatic federation?"* — Automatic creates the app registration for you; manual lets you use an existing managed identity or app registration — useful when you can't create apps in Entra ID.

**Common Mistakes:** Tenant-root Owner; "grant access to all pipelines"; secrets-based connections.

**Key Points to Remember:** Per-environment connections · federation · minimal RBAC · pipeline permissions · branch control + approvals.

## A10. Security incident: excessive permissions abused

**Question:** You discover a compromised service principal with Owner on a subscription created new VMs for crypto-mining. How do you respond?

**Scenario:** Defender for Cloud raises a high-severity alert; the cost dashboard shows a spike; 40 GPU VMs were created overnight in a region the company doesn't use.

**Interview Answer:**

"I'd treat it as a security incident and follow the incident process with the security team. Order matters: contain, preserve evidence, eradicate, recover, learn.

Contain: disable the service principal or remove its credentials and role assignments, and revoke sessions. Stop the attacker's resources — deallocate VMs, but preserve evidence: snapshot disks if forensics are needed and take an export of the Activity Log.

Investigate scope: in the Activity Log and Entra sign-in logs, find every operation by that principal — what was created, which role assignments were added, whether any other identities or credentials were created as persistence, and where the secret leaked from — often a repo or pipeline log.

Eradicate: delete malicious resources and backdoor assignments, rotate any secrets the SP could read, and fix the leak.

Recover and prevent: replace the SP with workload identity federation, least privilege, Azure Policy 'allowed locations' and 'allowed VM SKUs', quota controls, and alerts on role assignments and unusual resource creation."

**Technical Deep Dive:** Sources: Activity Log (AzureActivity), Entra ID AADServicePrincipalSignInLogs, AuditLogs, Defender for Cloud alerts, Microsoft Sentinel. Service principal sign-in logs show IP addresses.

**Step-by-Step:**

**1.** Declare incident; involve security.

**2.** Disable SP: remove credentials / disable sign-in; remove role assignments.

**3.** Export logs; snapshot evidence.

**4.** Enumerate attacker actions (KQL below).

**5.** Remove persistence (new SPs, credentials, role assignments, automation accounts, Logic Apps).

**6.** Delete resources; contact Microsoft support about fraudulent costs.

**7.** Post-incident review.

**KQL:**

**KQL**

AzureActivity

\| where TimeGenerated \> ago(7d)

\| where Caller == "\<sp-object-id-or-app-id\>"

\| summarize Count = count(), Regions = make_set(tostring(parse_json(Properties).resourceLocation))

by OperationNameValue, ActivityStatusValue

\| order by Count desc

AADServicePrincipalSignInLogs

\| where TimeGenerated \> ago(7d) and AppId == "\<app-id\>"

\| project TimeGenerated, IPAddress, Location, ResultType, ResourceDisplayName

**Commands:**

**BASH**

az ad sp update --id \<app-id\> --set accountEnabled=false

az role assignment list --assignee \<app-id\> --all -o table

az role assignment delete --assignee \<app-id\> --scope /subscriptions/\<sub-id\>

**Root Cause:** Over-privileged long-lived secret leaked; no guardrails on region/SKU.

**Prevention:** Least privilege, federation, secret scanning, allowed locations/SKUs policies, Defender for Cloud, Sentinel analytics, budgets/anomaly alerts.

**Interviewer Follow-Up Questions:**

- *"Delete or deallocate first?"* — Deallocate to stop cost while preserving evidence; delete after security sign-off.

- *"How did you find the leak?"* — Search repos and pipeline logs for the app ID/secret; check where the secret was stored and who had access.

**Common Mistakes:** Deleting everything immediately (losing evidence); only rotating the secret (attacker may have created persistence); not involving security.

**Key Points to Remember:** Contain → evidence → scope → remove persistence → recover → prevent.

## A11. Role assigned but user still gets access denied

**Question:** You assigned a role, but the user still sees "AuthorizationFailed". What could be wrong?

**Scenario:** A developer is given Reader on rg-orders-prod but still can't see the resource group.

**Interview Answer:**

"I'd check five things. One, propagation and token: role assignments can take a few minutes to apply and the user's token must refresh — sign out and back in. Two, scope: was it assigned on the right resource group, in the right subscription? Three, the principal: was it assigned to the correct user or group, and is the user actually a member — nested groups and guest accounts can confuse this. Four, PIM: if the assignment is eligible, the user must activate it. Five, deny assignments or Azure Policy: a deny assignment blocks even with the right role, and a policy can deny the action they're trying to do — the error message then says 'RequestDisallowedByPolicy', which is different.

Check access in the portal shows the effective roles and deny assignments, so that's my first tool."

**Technical Deep Dive:** Error types: AuthorizationFailed (RBAC), RequestDisallowedByPolicy (Policy), ScopeLocked (lock), DenyAssignmentAuthorizationFailed (deny assignment). Directory changes and group membership can take time to appear in tokens.

**Step-by-Step:** Read the error code → Check access → verify scope/principal → PIM status → deny assignments → policy → sign out/in.

**Azure Portal Steps:** Resource group → **Access control (IAM)** → **Check access** → user → also **Deny assignments** tab. Subscription → **Policy → Compliance** for denies.

**Commands:**

**BASH**

az role assignment list --assignee \<upn\> --scope /subscriptions/\<sub-id\>/resourceGroups/rg-orders-prod --include-inherited -o table

az ad group member check --group \<group-object-id\> --member-id \<user-object-id\>

**Root Cause:** Usually token/propagation or wrong scope.

**Prevention:** Group-based onboarding runbook; self-service checks.

**Interviewer Follow-Up Questions:**

- *"What's the difference between AuthorizationFailed and RequestDisallowedByPolicy?"* — The first is RBAC (who), the second is Policy (what).

- *"Can Reader see Key Vault secrets?"* — No; Reader is control plane. Secrets need a data role.

**Common Mistakes:** Re-assigning repeatedly; granting a higher role instead of finding the cause.

**Key Points to Remember:** Token · scope · principal/group · PIM · deny/policy/lock — read the error code.

## A12. Management groups and subscription design

**Question:** How do you structure management groups and subscriptions for an enterprise?

**Scenario:** Everything runs in one subscription and teams hit limits and RBAC confusion.

**Interview Answer:**

"I follow the Azure landing zone approach, adapted to company size. At the top, under the tenant root group, an organisation management group. Under it: Platform — with Identity, Management and Connectivity subscriptions — and Landing Zones split into Corp, for internal workloads connected to the hub network, and Online, for internet-facing apps. Plus Sandbox for experiments, and Decommissioned.

Policies and RBAC are assigned at management group level so they're inherited: for example allowed regions and diagnostic settings at the top, stricter network rules under Corp.

Subscriptions are the unit of scale, billing and isolation, so I'd give each major workload and environment its own subscription — for example payments-prod and payments-nonprod — created through subscription vending automation so they arrive with networking, policy and RBAC ready."

**Technical Deep Dive:** Up to six levels of management group depth (excluding root and subscription). A subscription has one parent. Moving subscriptions between management groups changes inherited policy/RBAC — test first.

**Step-by-Step (migration):** Design hierarchy → create MGs → assign policies in audit → create new subscriptions → move workloads gradually (resource move or redeploy via IaC).

**Azure Portal Steps:** **Management groups** → Create → Add subscription. Assign policy at MG: **Policy → Assignments → Scope**.

**Terraform:**

**HCL**

resource "azurerm_management_group" "landing_zones" {

display_name = "Landing Zones"

parent_management_group_id = azurerm_management_group.org.id

}

resource "azurerm_management_group_subscription_association" "payments_prod" {

management_group_id = azurerm_management_group.landing_zones.id

subscription_id = "/subscriptions/\<sub-id\>"

}

**Root Cause (of original pain):** No hierarchy; single subscription hits quotas and RBAC sprawl.

**Prevention:** Subscription vending, landing zone policies, documented ownership.

**Interviewer Follow-Up Questions:**

- *"Why not resource groups instead of subscriptions?"* — Subscriptions give quota isolation, billing separation, cleaner RBAC and policy boundaries.

- *"What goes in the Management subscription?"* — Central Log Analytics, Automation, monitoring resources.

**Common Mistakes:** Deep hierarchies by department; assigning everything at tenant root.

**Key Points to Remember:** Platform vs Landing Zones · inherit policy/RBAC · subscription per workload/env · vending.

## A13. Users, groups and guest access

**Question:** How do you manage users, groups and external contractors' access to Azure?

**Scenario:** A contractor company needs read access to logs in production for three months.

**Interview Answer:**

"For contractors, I'd use Entra ID B2B guest accounts, so they use their own company identity and we don't manage passwords. I'd add them to a dedicated group — for example grp-ext-vendorx-prod-logreaders — with a narrow role like Log Analytics Reader on the specific workspace or resource-context access to their resources only.

I'd set an expiry: either an access package in Entitlement Management with a 90-day end date and sponsor approval, or at least an access review. Conditional Access would require MFA for guests. When the contract ends, the access package expires and the guest is removed.

For internal users, the source of truth is HR-driven provisioning, and groups — ideally dynamic or managed through access packages — rather than manual membership."

**Technical Deep Dive:** Entitlement management access packages bundle groups/apps/roles with policies (who can request, approval, expiry, reviews). Log Analytics resource-context RBAC lets users see logs only for resources they can read.

**Step-by-Step:** Create group → assign role → create access package with expiry → invite guest → Conditional Access → review.

**Azure Portal Steps:** **Entra ID → Identity Governance → Entitlement management → Access packages → New**. **Users → Invite external user**.

**Commands:**

**BASH**

az ad group create --display-name grp-ext-vendorx-prod-logreaders --mail-nickname vendorxlogs

az role assignment create --assignee \<group-object-id\> --role "Log Analytics Reader" \\

--scope /subscriptions/\<sub-id\>/resourceGroups/\<rg\>/providers/Microsoft.OperationalInsights/workspaces/\<law\>

**Root Cause (common failure):** Guests added directly with no expiry; access never removed.

**Prevention:** Access packages with expiry; guest access reviews; Conditional Access for guests.

**Interviewer Follow-Up Questions:**

- *"Can a guest have Owner?"* — Technically yes, but it should be blocked by process and flagged by Defender for Cloud.

- *"How to limit logs to their app only?"* — Resource-context access or table-level RBAC rather than workspace-wide Reader.

**Common Mistakes:** Creating internal accounts for contractors; no MFA; no expiry.

**Key Points to Remember:** B2B guests · narrow group · access packages with expiry · Conditional Access.

## A14. AKS RBAC and workload identity

**Question:** How do you control access to an AKS cluster and give pods access to Azure resources?

**Scenario:** Developers share the cluster admin kubeconfig, and pods use a storage key stored in a Kubernetes secret.

**Interview Answer:**

"Two problems: human access and workload access.

For humans, I'd enable Microsoft Entra ID integration with Azure RBAC for Kubernetes authorisation and disable local accounts, so nobody uses the shared admin certificate. Then I assign built-in roles like Azure Kubernetes Service RBAC Reader or Writer per namespace to Entra groups — developers get Writer on their namespace only, platform team gets Cluster Admin through PIM.

For workloads, I'd use Microsoft Entra Workload ID. I create a user-assigned managed identity, add a federated credential that trusts the cluster's OIDC issuer and the pod's Kubernetes service account, and give that identity the data-plane role it needs. The pod gets tokens automatically, with no secret stored in the cluster."

**Technical Deep Dive:** --enable-aad --enable-azure-rbac --disable-local-accounts. Workload identity requires --enable-oidc-issuer --enable-workload-identity, service account annotation azure.workload.identity/client-id, pod label azure.workload.identity/use: "true". Pod-managed identity is deprecated.

**Step-by-Step:** Enable Entra integration → assign roles → disable local accounts → enable OIDC/workload identity → create UAMI + federated credential → annotate service account → remove secrets.

**Commands:**

**BASH**

az aks update -g \<rg\> -n \<aks\> --enable-aad --enable-azure-rbac --disable-local-accounts

az aks update -g \<rg\> -n \<aks\> --enable-oidc-issuer --enable-workload-identity

ISSUER=\$(az aks show -g \<rg\> -n \<aks\> --query oidcIssuerProfile.issuerUrl -o tsv)

az identity create -g \<rg\> -n id-orders-api

az identity federated-credential create --name orders-api-fc --identity-name id-orders-api -g \<rg\> \\

--issuer \$ISSUER --subject system:serviceaccount:orders:orders-api --audiences api://AzureADTokenExchange

az role assignment create --assignee \<namespace-dev-group-id\> --role "Azure Kubernetes Service RBAC Writer" \\

--scope \$(az aks show -g \<rg\> -n \<aks\> --query id -o tsv)/namespaces/orders

**YAML**

apiVersion: v1

kind: ServiceAccount

metadata:

name: orders-api

namespace: orders

annotations:

azure.workload.identity/client-id: \<uami-client-id\>

---

\# In the pod template:

\# metadata.labels: azure.workload.identity/use: "true"

\# spec.serviceAccountName: orders-api

**Root Cause:** Default cluster setup with local admin; legacy secret-based access.

**Prevention:** Azure Policy for AKS (disable local accounts); cluster templates with these defaults.

**Interviewer Follow-Up Questions:**

- *"Kubernetes RBAC vs Azure RBAC for Kubernetes?"* — Kubernetes RBAC uses Role/RoleBinding in-cluster; Azure RBAC manages it from Azure with Entra groups, PIM and audit. Both can coexist.

- *"Pod gets 'AADSTS70021 no matching federated identity'?"* — Subject (namespace/service account) or issuer mismatch.

**Common Mistakes:** Sharing admin kubeconfig; using pod-managed identity in new designs.

**Key Points to Remember:** Entra integration + Azure RBAC + no local accounts · Workload ID with federated credential.

## A15. Auditing RBAC changes

**Question:** How do you detect and alert when someone grants Owner in production?

**Scenario:** The CISO asks: "Would we know within 5 minutes if someone gave themselves Owner?"

**Interview Answer:**

"Yes, if we set it up. Role assignment creation is recorded in the Azure Activity Log as Microsoft.Authorization/roleAssignments/write. I'd create an Activity Log alert on that operation at subscription scope — or better, send Activity Logs from all subscriptions to the central Log Analytics workspace and use a log search alert that filters for privileged roles like Owner, User Access Administrator and RBAC Administrator. That alert goes to an action group that pages security and posts to the security channel.

Activity Log alerts are near real-time, so it's within minutes. If we use Microsoft Sentinel, there are built-in analytics rules for this too. PIM also sends notifications for privileged activations.

The bigger point: alerts detect, but prevention is better — PIM for Owner, and few people who can assign it."

**KQL:**

**KQL**

AzureActivity

\| where TimeGenerated \> ago(1h)

\| where OperationNameValue =~ "MICROSOFT.AUTHORIZATION/ROLEASSIGNMENTS/WRITE"

\| where ActivityStatusValue == "Success"

\| extend RoleDefId = tostring(parse_json(tostring(parse_json(Properties).requestbody)).Properties.RoleDefinitionId)

\| where RoleDefId has_any ("8e3af657-a8ff-443c-a75c-2fe8c4bcb635", // Owner

"18d7d88d-d35e-4fb5-a5c3-7773c20a72d9", // User Access Administrator

"f58310d9-a9f6-439a-9e8d-f62e7b41a168") // RBAC Administrator

\| project TimeGenerated, Caller, CallerIpAddress, \_ResourceId, RoleDefId

**Step-by-Step:** Route Activity Log via diagnostic settings (policy) → create log alert → action group → test by assigning in non-prod.

**Azure Portal Steps:** **Monitor → Alerts → Create → Alert rule** → Scope: subscription → Condition: Activity Log signal "Create role assignment" → Action group. Or **Log search** rule in the workspace with the KQL.

**Root Cause (for gaps):** Activity Log not exported; no alerts.

**Prevention:** Policy to export Activity Log from all subscriptions; Sentinel; PIM.

**Interviewer Follow-Up Questions:**

- *"Activity Log retention?"* — 90 days in Azure by default; export to Log Analytics/Storage for longer.

- *"What about Entra directory roles?"* — Those are in Entra AuditLogs, not Azure Activity Log.

**Common Mistakes:** Only alerting at one subscription; not testing the alert.

**Key Points to Remember:** roleAssignments/write in Activity Log · central workspace · filter privileged role IDs · page security.

# Section 2B — Azure Monitoring and Observability (20 Questions)

## B1. App Service suddenly returns HTTP 500

**Question:** An application hosted on Azure App Service suddenly starts returning HTTP 500 errors. How do you investigate?

**Scenario:** At 14:10 UK time, availability tests fail and 40% of /api/orders calls return 500. A release went out at 14:00.

**Interview Answer:**

"First impact and timing: what percentage of requests fail, which endpoints, and what changed. The release at 14:00 lines up, so if we use deployment slots I'd swap back first — that takes about a minute and protects customers. Then I investigate calmly.

In Application Insights, the Failures blade shows which operations fail and the top exception types. I open a sample and look at the end-to-end transaction — is the exception in our code, or is a dependency failing, like SQL timing out or Key Vault returning 403? Live Metrics shows whether it's still happening right now.

On the App Service side, 'Diagnose and solve problems' has HTTP 5xx and application crash detectors, and the Activity Log shows configuration changes like app settings. I compare app settings between slots — a missing slot setting is a very common cause.

Once I know the root cause, I fix it through the pipeline, then add prevention: a smoke test on the staging slot before swap, a health check path, and an alert on failure rate."

**Technical Deep Dive:** 500 = unhandled exception or dependency failure in app; 502 = bad gateway (often front-end can't reach worker/app crashed); 503 = unavailable (app stopped, overloaded, or startup). App Service logs: application logging, web server logging, detailed error messages, failed request tracing. Health check removes unhealthy instances after consecutive failures (instance replaced after an hour unhealthy).

**Step-by-Step Troubleshooting:**

**1.** Confirm scope: Failures blade by operation and result code; instance split.

**2.** Correlate with changes: deployments, app settings, slot swaps (Activity Log; Deployment Center).

**3.** Mitigate: slot swap back / redeploy previous artifact / scale out if resource-bound.

**4.** Root cause: exceptions, dependency failures, memory/CPU, startup errors in Log stream.

**5.** Fix via pipeline, verify in staging, swap.

**6.** Add alerts, smoke tests, health check.

**Azure Portal Steps:** App Service → **Diagnose and solve problems → Availability and Performance**; **Log stream**; **Deployment slots**; **Configuration** (compare slot settings); Application Insights → **Failures**, **Live Metrics**, **Transaction search**.

**KQL:**

**KQL**

AppRequests

\| where TimeGenerated \> ago(2h)

\| summarize Total = count(), Failed = countif(ResultCode startswith "5") by bin(TimeGenerated, 5m), AppRoleInstance

\| extend FailPct = round(100.0 \* Failed / Total, 1)

\| order by TimeGenerated asc

AppExceptions

\| where TimeGenerated \> ago(1h)

\| summarize Count = count() by ProblemId, OuterMessage

\| top 10 by Count

**Commands:**

**BASH**

az webapp log tail -g \<rg\> -n \<app\>

az webapp config appsettings list -g \<rg\> -n \<app\> --slot staging -o table

az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --target-slot production

**Root Cause:** Typical: missing configuration (connection string not marked as slot setting), code defect, dependency failure (SQL/Key Vault/API), resource exhaustion.

**Prevention:** Slot-based deploys with smoke tests; health check; failure-rate alert; configuration in IaC.

**Interviewer Follow-Up Questions:**

- *"How do you see the actual exception if App Insights isn't enabled?"* — Enable application logging (filesystem), use Log stream, Kudu (/api/logstream, LogFiles), or detailed errors.

- *"Errors only on one instance?"* — Health check or Advanced Application Restart for that instance; check instance-specific disk/memory.

- *"How fast is a slot swap?"* — Swap warms the source slot before switching; the switch itself is near-instant.

**Common Mistakes:** Restarting the app before capturing evidence; debugging for an hour before rolling back.

**Key Points to Remember:** What changed? → mitigate (swap) → Failures blade → end-to-end transaction → fix via pipeline → prevent.

## B2. VM CPU consistently above 90%

**Question:** CPU is consistently above 90% on a production VM. How do you identify the root cause?

**Scenario:** A Windows VM running an IIS API has been at 92–98% CPU for three days. Response times doubled.

**Interview Answer:**

"I'd first look at the trend over at least seven days to see if it started suddenly or grew gradually. A sudden change points to a change — deployment, patch, scheduled task, scan. A gradual rise points to growth in load.

Then I find the process. If the Azure Monitor Agent collects process-level data through VM insights, I can see which process uses CPU. Otherwise I use Run Command or Bastion to check Task Manager or Get-Process on Windows, or top on Linux. I also check whether it's a B-series VM out of CPU credits.

If it's the application, Application Insights profiler can show which code path is hot. If it's load, I check request counts. If it's something like antivirus or a stuck process, I fix that.

Long-term fix: right-size, or scale out using a VM Scale Set behind a load balancer, and alert with a dynamic threshold so we see it early."

**Technical Deep Dive:** Host metric Percentage CPU (no agent needed). Guest counters via AMA + DCR into Perf or InsightsMetrics. VM insights adds performance and map (dependency agent). B-series: CPU Credits Remaining, CPU Credits Consumed.

**Step-by-Step:**

**1.** Metrics: CPU, network, disk, B-series credits — 7–30 days.

**2.** Correlate with Activity Log / Change Analysis / Update Manager history.

**3.** Identify process (VM insights, Run Command).

**4.** Check application telemetry (requests, profiler).

**5.** Mitigate (stop runaway process, scale up/out).

**6.** Permanent fix and alerting.

**Azure Portal Steps:** VM → **Metrics** → Percentage CPU; **Insights → Performance**; **Run command → RunPowerShellScript**; **Diagnose and solve problems → VM performance**; **Change analysis** (via Resource Graph changes).

**Commands:**

**BASH**

az monitor metrics list --resource \<vm-resource-id\> --metric "Percentage CPU" \\

--start-time 2026-11-01T00:00:00Z --interval PT1H --aggregation Average Maximum -o table

az vm run-command invoke -g \<rg\> -n \<vm\> --command-id RunPowerShellScript \\

--scripts "Get-Process \| Sort-Object CPU -Descending \| Select-Object -First 10 Name,Id,CPU,WS"

**KQL:**

**KQL**

Perf

\| where TimeGenerated \> ago(7d) and Computer == "\<vm-name\>"

\| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "\_Total"

\| summarize AvgCPU = avg(CounterValue) by bin(TimeGenerated, 1h)

\| render timechart

**Root Cause:** Common: application regression, runaway process, AV scan, Windows Update, under-sized VM, credit exhaustion.

**Prevention:** Dynamic-threshold CPU alert; capacity reviews; VMSS autoscale; change management.

**Interviewer Follow-Up Questions:**

- *"Host CPU is 95% but guest Task Manager shows 60%?"* — Different measurement windows/sampling; check guest counter averages and steal; also hidden system processes.

- *"How to resize with minimal downtime?"* — Resize requires restart; with VMSS or multiple VMs behind LB, roll through instances.

**Common Mistakes:** Resizing immediately without finding the process; ignoring B-series credits.

**Key Points to Remember:** Trend → change correlation → process → credits → fix → alert.

## B3. Application Insights stopped receiving telemetry

**Question:** Application Insights stopped receiving telemetry after a deployment. How would you troubleshoot?

**Scenario:** The Failures and Performance blades are empty since last night's release; the app still works for customers.

**Interview Answer:**

"Because it started after a deployment, I'd compare configuration before and after. The most common cause is the APPLICATIONINSIGHTS_CONNECTION_STRING app setting missing or pointing to another resource — for example a template that overwrote all app settings, or a slot setting that didn't follow the swap.

Then I check the agent or SDK: did the new build remove the SDK or OpenTelemetry distro, or was the codeless agent disabled? Then network: if the app has outbound restrictions or uses Azure Monitor Private Link Scope, the ingestion endpoint might be blocked or resolve wrongly. If local authentication is disabled on the App Insights resource, the app needs Entra ID auth for ingestion.

Then the data side: did the workspace hit its daily cap, or did someone set sampling extremely low?

Live Metrics is a quick test — if Live Metrics shows data, the app is sending and the problem is ingestion; if not, it's the app or network."

**Technical Deep Dive:** Connection string contains InstrumentationKey + IngestionEndpoint + LiveEndpoint (regional). Instrumentation-key-only ingestion support ended 31 March 2025. Workspace-based App Insights stores data in the linked Log Analytics workspace (daily cap can be on both). AMPLS changes DNS for all Azure Monitor endpoints in the network.

**Step-by-Step:**

**1.** Check app setting and the App Insights resource it points to.

**2.** Live Metrics test.

**3.** Check SDK/agent version and startup logs.

**4.** Network: outbound rules, DNS for \*.in.applicationinsights.azure.com, AMPLS access mode.

**5.** Workspace daily cap and sampling.

**6.** Fix in IaC; add a "no data" alert.

**Azure Portal Steps:** App Service → **Configuration** / **Application Insights** blade; App Insights → **Live Metrics**; **Usage and estimated costs → Daily cap**; **Network isolation**; **Properties → Local authentication**.

**Commands:**

**BASH**

az webapp config appsettings list -g \<rg\> -n \<app\> --query "\[?name=='APPLICATIONINSIGHTS_CONNECTION_STRING'\]" -o table

az monitor app-insights component show -g \<rg\> -a \<appi\> --query "{conn:connectionString, ws:workspaceResourceId}"

**KQL (from the workspace):**

**KQL**

union AppRequests, AppTraces, AppDependencies

\| where TimeGenerated \> ago(2d) and AppRoleName == "\<role\>"

\| summarize Count = count() by bin(TimeGenerated, 1h), Type

\| render timechart

**Root Cause:** Config overwrite during deployment is the most common.

**Prevention:** Connection string defined in IaC; "no telemetry" log alert; availability test; deployment checklist.

**Interviewer Follow-Up Questions:**

- *"Data arrives but delayed?"* — Ingestion latency is typically under 5 minutes; check Service Health for Azure Monitor issues.

- *"Some telemetry types missing?"* — Sampling or telemetry processors filtering; check itemCount for sampled data.

**Common Mistakes:** Recreating the App Insights resource (loses history, changes key); assuming the app is broken.

**Key Points to Remember:** Connection string → Live Metrics → SDK/agent → network/AMPLS/local auth → daily cap/sampling.

## B4. Azure Monitor architecture

**Question:** Explain the Azure Monitor data platform and how its components fit together.

**Scenario:** A new team asks, "Where do we send our logs and how do we see them?"

**Interview Answer:**

"Azure Monitor is the umbrella. Data comes from many sources — Azure platform, guest OS, applications, containers — and lands in two main stores: the metrics database and Log Analytics workspaces.

Platform metrics are collected automatically for most resources, kept for 93 days and are great for fast alerts and charts. Resource logs are not collected by default — you route them with diagnostic settings. The Activity Log records control-plane operations at subscription level.

For VMs and servers, the Azure Monitor Agent collects guest data defined in Data Collection Rules. Applications use Application Insights, which is workspace-based, so telemetry lives in the same Log Analytics workspace. Containers use Container Insights and the managed Prometheus service.

On top we have the consumption tools: Metrics explorer, Log Analytics with KQL, Workbooks, dashboards, Managed Grafana, alerts with action groups, and exports to Event Hubs or Sentinel."

**Technical Deep Dive:** Data sources → collection (diagnostic settings, AMA + DCR, Logs Ingestion API, OTel) → stores (Metrics, Logs, Azure Monitor workspace for Prometheus metrics, Change data) → insights (VM, Container, Network, Application) → actions (alerts, autoscale, Logic Apps).

**Step-by-Step (onboarding a team):** Workspace decision → diagnostic settings by policy → App Insights with connection string → DCR for VMs → workbook → alerts.

**Azure Portal Steps:** **Monitor** → Metrics / Logs / Alerts / Workbooks / Data Collection Rules / Diagnostic settings.

**Diagram:**

![Azure monitoring architecture](assets/f46480f8178196996e52bb8dec6e6b1a5dff2bc1.png)

**Root Cause (common gap):** Teams assume resource logs are collected automatically — they are not.

**Prevention:** Policy-driven diagnostic settings.

**Interviewer Follow-Up Questions:**

- *"Is Activity Log the same as resource logs?"* — No; Activity Log is subscription-level control plane; resource logs are per-resource data-plane operations.

- *"Where do Prometheus metrics go?"* — Azure Monitor workspace (managed Prometheus), visualised in Managed Grafana.

**Common Mistakes:** Confusing Log Analytics workspace with Azure Monitor workspace.

**Key Points to Remember:** Metrics vs logs stores · diagnostic settings · AMA + DCR · workspace-based App Insights.

## B5. Centralised logging for 100+ resources

**Question:** How would you implement centralised logging and telemetry across multiple subscriptions?

**Scenario:** 6 subscriptions, ~150 resources, inconsistent diagnostics; incident investigations take hours because logs are missing.

**Interview Answer:**

"I'd build it as a platform. A central Log Analytics workspace per environment in the Management subscription, designed with the security team so Sentinel can use the same workspace if needed.

Collection is enforced, not requested: Azure Policy initiatives with DeployIfNotExists assigned at management group level create diagnostic settings for all supported resource types, using category groups like 'allLogs' or 'audit'. Activity Logs from every subscription go to the same workspace. VMs get the Azure Monitor Agent and a standard DCR through policy too. App Insights resources are workspace-based and point to the same workspace.

Access uses resource-context RBAC, so a team that can read its resources can query its own logs without seeing everyone else's.

Then I add the value layer: standard workbooks per service type, baseline alerts, and cost controls — table plans, DCR transformations, retention by table. And I track compliance on the Policy dashboard so we know coverage is 100%."

**Technical Deep Dive:** Built-in initiatives "Enable allLogs category group resource logging for supported resources to Log Analytics" (and audit variants). Remediation tasks fix existing resources. Workspace access mode "Use resource or workspace permissions". Resource-specific vs AzureDiagnostics destination tables — prefer resource-specific.

**Step-by-Step:**

**1.** Workspace design (count, region, retention, access mode).

**2.** Assign policy initiatives at MG scope with managed identity.

**3.** Run remediation tasks.

**4.** Activity Log export for all subscriptions.

**5.** AMA + DCR policies for VMs/Arc.

**6.** Workbooks and baseline alerts; measure coverage.

**Azure Portal Steps:** **Policy → Definitions** → search "allLogs" → **Assign** at MG → Remediation tab → create remediation task. **Monitor → Data Collection Rules → Create**.

**Terraform:**

**HCL**

resource "azurerm_monitor_diagnostic_setting" "kv" {

name = "diag-to-law"

target_resource_id = azurerm_key_vault.kv.id

log_analytics_workspace_id = azurerm_log_analytics_workspace.central.id

log_analytics_destination_type = "Dedicated" \# resource-specific tables where supported

enabled_log { category_group = "audit" }

enabled_metric { category = "AllMetrics" }

}

**KQL (coverage check — which resources sent logs today):**

**KQL**

union withsource=TableName \*

\| where TimeGenerated \> ago(1d) and isnotempty(\_ResourceId)

\| summarize Tables = make_set(TableName) by \_ResourceId

\| count

**Root Cause (original problem):** Manual, per-team configuration.

**Prevention:** Policy + compliance dashboard + onboarding as part of subscription vending.

**Interviewer Follow-Up Questions:**

- *"How do you handle a resource type without a built-in policy?"* — Custom DINE policy or deploy diagnostics in the IaC module.

- *"Cross-region workspace?"* — Possible but adds egress cost and data residency considerations; prefer regional workspace per geography.

**Common Mistakes:** Too many workspaces; sending everything with no cost plan; forgetting Activity Log.

**Key Points to Remember:** Central workspace · Policy DINE + remediation · AMA/DCR · resource-context RBAC · cost controls.

## B6. Designing proactive alerting

**Question:** How do you design an alerting strategy that is proactive and actionable?

**Scenario:** Today customers report outages before engineers notice.

**Interview Answer:**

"I start with what users experience. For each critical service, I define SLIs like availability and latency and set alerts on those — for example 'failure rate above 2% for 5 minutes' or 'p95 latency above 1 second'. Availability tests from several regions catch total outages even with no traffic.

Then I add early-warning alerts on causes that predict an outage: disk filling, certificate expiry within 30 days, database DTU near 90%, queue length growing, autoscale at maximum.

Every alert has a severity and an action group based on severity: Sev 0–1 pages on-call; Sev 2 goes to a Teams channel and the backlog. Every alert description links to a runbook.

I also include platform signals: Service Health alerts for Azure incidents in our regions and Resource Health for key resources.

And I deploy alerts as code, so every new service gets the same baseline."

**Technical Deep Dive:** Alert rule types: metric (static/dynamic, multi-resource for same type/region), log search (KQL, frequency/look-back, dimension splitting), Activity Log, Service Health, Resource Health, Prometheus rules, smart detection. Stateful log alerts auto-resolve. Azure Monitor Baseline Alerts (AMBA) provide policy-based baseline alerts for landing zones.

**Step-by-Step (implementation):** Inventory critical services → define SLIs/thresholds → build rules → action groups by severity → runbooks → test with fault injection → review monthly.

**Azure Portal Steps:** **Monitor → Alerts → Create → Alert rule**; **Action groups**; **Service Health → Health alerts → Create service health alert**; App Insights → **Availability → Add Standard test**.

**Bicep (metric alert):**

**BICEP**

resource http5xx 'Microsoft.Insights/metricAlerts@2018-03-01' = {

name: 'alert-app-orders-http5xx'

location: 'global'

properties: {

severity: 1

enabled: true

scopes: \[ appService.id \]

evaluationFrequency: 'PT1M'

windowSize: 'PT5M'

criteria: {

'odata.type': 'Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria'

allOf: \[

{

name: 'Http5xx'

metricName: 'Http5xx'

operator: 'GreaterThan'

threshold: 20

timeAggregation: 'Total'

criterionType: 'StaticThresholdCriterion'

}

\]

}

actions: \[ { actionGroupId: agOnCall.id } \]

}

}

**Root Cause (of reactive culture):** Alerts on infrastructure only, no user-facing signals.

**Prevention:** SLO-based alerts; baseline alerts as policy; monthly alert review.

**Interviewer Follow-Up Questions:**

- *"What's an SLO burn-rate alert?"* — Alert when the error budget is being consumed too fast (e.g., 2% budget in 1 hour), reducing noise from brief spikes.

- *"How do you test alerts?"* — Trigger conditions in non-prod, use Azure Chaos Studio, or test action groups with the built-in test feature.

**Common Mistakes:** Alerting on everything; no severity; no runbook.

**Key Points to Remember:** Symptom-based first · availability tests · leading indicators · severity → action group · as code.

## B7. Reducing alert noise

**Question:** On-call gets 400 alerts a week and starts ignoring them. How do you fix alert fatigue?

**Scenario:** Most alerts auto-resolve within minutes; some fire every night at the same time.

**Interview Answer:**

"First I measure. I export alert history from Azure Resource Graph or Log Analytics, then group by alert rule: how many fired, how many led to action. Usually 10–20% of rules create 80% of the noise.

For each noisy rule I ask: is it actionable? If nobody does anything, delete it or downgrade it to a non-paging severity. If it's real but flappy, tune it — use dynamic thresholds, longer windows, require several violations, or alert on rate instead of a single spike. If it fires during known batch or maintenance windows, use alert processing rules to suppress notifications during that schedule.

I also de-duplicate — one alert per symptom, not five alerts from five related resources. And I move from cause-based to symptom-based paging.

Finally I make it a process: a monthly alert review where we look at the top noisy rules, and every page must have a runbook. Within a few weeks pages typically drop significantly and people trust alerts again."

**Technical Deep Dive:** Alert processing rules: suppression (with schedule — one-time or recurring) or add action groups; scope by subscription/RG/resource, filter by severity, alert rule, monitor service. Dynamic thresholds learn seasonality (needs some history). "Number of violations to trigger" reduces flapping.

**KQL / Resource Graph:**

**KUSTO**

// Azure Resource Graph (alertsmanagementresources)

alertsmanagementresources

\| where type == "microsoft.alertsmanagement/alerts"

\| where todatetime(properties.essentials.startDateTime) \> ago(7d)

\| summarize Fired = count() by AlertRule = tostring(properties.essentials.alertRule),

Severity = tostring(properties.essentials.severity)

\| order by Fired desc

**Step-by-Step:** Measure → classify actionable/non-actionable → tune or delete → suppression rules → consolidate → review cadence.

**Azure Portal Steps:** **Monitor → Alerts** (summary by rule); **Alert processing rules → Create → Suppress notifications → Scheduling**; edit rule → **Threshold: Dynamic**.

**CLI:**

**BASH**

az monitor alert-processing-rule create -g \<rg\> -n apr-batch-window \\

--rule-type RemoveAllActionGroups --scopes /subscriptions/\<sub-id\>/resourceGroups/rg-batch \\

--schedule-recurrence-type Daily --schedule-start-time "01:00:00" --schedule-end-time "03:00:00" \\

--schedule-time-zone "GMT Standard Time" --description "Nightly batch window"

**Root Cause:** Thresholds copied from templates; no ownership; alerts on causes not symptoms.

**Prevention:** Alert ownership; review cadence; alerts as code with PR review.

**Interviewer Follow-Up Questions:**

- *"Dynamic thresholds — any downsides?"* — Need history; may miss slow degradation; less predictable for audits. Combine with a static hard limit.

- *"Does suppression stop the alert from being recorded?"* — No, the alert still fires and is visible; only notifications are removed.

**Common Mistakes:** Just muting alerts; raising thresholds until nothing fires.

**Key Points to Remember:** Measure → delete/downgrade → tune (dynamic, windows) → suppress windows → review monthly.

## B8. Action groups and notification design

**Question:** How do you design action groups for different teams and severities?

**Scenario:** All alerts email a shared mailbox that nobody reads at night.

**Interview Answer:**

"Action groups are reusable notification and automation targets. I'd create them by team and severity: for example ag-payments-sev1 that triggers the on-call system — PagerDuty, Opsgenie or ServiceNow via webhook or the ITSM connector — plus a Teams post; and ag-payments-sev3 that just posts to Teams and creates a ticket.

I'd use the common alert schema, so every integration receives the same JSON format. For automated remediation I can add an Automation runbook, Azure Function or Logic App — for example restart a stuck service or scale out — but only for well-understood, safe actions.

Action groups are deployed as code and referenced by alert rules. Alert processing rules can add action groups at scale — for example all Sev 0 alerts in production also notify the major incident manager."

**Technical Deep Dive:** Notification types: email, SMS, Azure app push, voice, email ARM role. Actions: Automation runbook, Azure Function, Event Hub, ITSM, Logic App, secure webhook (Entra auth), webhook. Rate limits apply to SMS/voice/email. Common alert schema standardises payloads.

**Step-by-Step:** Define severity model → build action groups → integrate with on-call tool → test with "Test action group" → attach to rules or via processing rules.

**Azure Portal Steps:** **Monitor → Alerts → Action groups → Create** → Notifications / Actions → **Enable common alert schema** → **Test action group**.

**Terraform:**

**HCL**

resource "azurerm_monitor_action_group" "payments_sev1" {

name = "ag-payments-sev1"

resource_group_name = azurerm_resource_group.monitoring.name

short_name = "paysev1"

webhook_receiver {

name = "oncall-tool"

service_uri = var.oncall_webhook_url \# stored as a secret variable

use_common_alert_schema = true

}

email_receiver {

name = "payments-team"

email_address = "payments-team@example.com"

use_common_alert_schema = true

}

}

**Root Cause (shared mailbox problem):** No routing by severity, no paging integration.

**Prevention:** Severity model and on-call integration; periodic test of action groups.

**Interviewer Follow-Up Questions:**

- *"Secure webhook vs webhook?"* — Secure webhook uses Entra ID auth to the receiving endpoint.

- *"Auto-remediation risks?"* — Can hide real problems or loop; log every action and limit to safe operations.

**Common Mistakes:** One action group for everything; email-only for Sev 1.

**Key Points to Remember:** By team + severity · on-call integration · common alert schema · test.

## B9. Building custom monitoring dashboards

**Question:** You need to build a dashboard for engineering and one for leadership. How do you approach it?

**Scenario:** Leadership wants "one page that shows if the platform is healthy"; engineers want drill-down.

**Interview Answer:**

"Different audiences need different views. For engineers, I'd build an Azure Monitor Workbook per service with parameters for environment and time range: the golden signals — traffic, errors, latency, saturation — then dependency health, and drill-down from a failing operation to its exceptions. Workbooks are interactive and can mix KQL, metrics and Resource Graph.

For leadership, a simpler view: availability against SLO for each critical service, number of incidents, and maybe cost trend — with red/amber/green status. That could be a shared Azure Dashboard, a workbook in 'reader mode', or Managed Grafana if the company already uses Grafana.

Both are stored as code — workbook JSON in Git and deployed with Terraform — so they are consistent across environments and can be reviewed."

**Technical Deep Dive:** Workbook features: parameters (subscription, resource, time range, dropdowns from KQL), conditional visibility, grids with heatmaps/thresholds, links to other workbooks, Resource Graph queries, metrics. Shared workbooks require RBAC (Workbook Contributor to save). Dashboards: up to 100 tiles, shared via RBAC, JSON export. Managed Grafana: Azure Monitor data source, Entra SSO.

**Step-by-Step:** Interview users → choose signals → write KQL → build workbook → add parameters → publish shared → export JSON to repo → deploy via IaC → link from alerts.

**Azure Portal Steps:** **Monitor → Workbooks → New** → Add query / metric / parameters → **Save** (shared) → **Advanced editor** to copy JSON.

**KQL (SLO availability per service):**

**KQL**

AppRequests

\| where TimeGenerated \> ago(30d)

\| summarize Total = count(), Good = countif(Success == true and DurationMs \< 1000) by AppRoleName

\| extend AvailabilityPct = round(100.0 \* Good / Total, 3)

\| extend Status = iff(AvailabilityPct \>= 99.9, "Green", iff(AvailabilityPct \>= 99.5, "Amber", "Red"))

**Terraform:**

**HCL**

resource "azurerm_application_insights_workbook" "orders" {

name = "5b1f2a3c-0000-4000-8000-000000000001" \# must be a GUID

resource_group_name = azurerm_resource_group.monitoring.name

location = azurerm_resource_group.monitoring.location

display_name = "Orders Service Health"

data_json = file("\${path.module}/workbooks/orders.json")

}

**Root Cause (dashboards nobody uses):** Built without users; too many tiles; not linked from incidents.

**Prevention:** Design with users; link from alerts/runbooks; review usage.

**Interviewer Follow-Up Questions:**

- *"Workbook vs Grafana?"* — Workbooks are native and free; Grafana is better for multi-source, Prometheus-heavy and existing Grafana users.

- *"How do you make one workbook work for 20 services?"* — Parameters (AppRoleName/resource dropdown) and templates.

**Common Mistakes:** Vanity metrics; no thresholds; hard-coded resource IDs.

**Key Points to Remember:** Audience first · golden signals · parameters · as code · link from alerts.

## B10. Writing KQL for incident investigation

**Question:** Walk me through KQL you would write during an incident.

**Scenario:** Users report slowness on checkout for the last 30 minutes.

**Interview Answer:**

"I write KQL in layers. First, is it real and when did it start — latency percentiles over time for the checkout operation. Second, is it everywhere or one place — split by instance, region or client. Third, where's the time — join with dependencies to see which call got slower. Fourth, any errors — exceptions in the same window. Fifth, what changed — Activity Log in the same window.

I use percentiles rather than averages, because averages hide tail latency. And I always filter on time early in the query to keep it fast."

**KQL:**

**KQL**

// 1. Latency over time for checkout

AppRequests

\| where TimeGenerated \> ago(2h) and Name has "checkout"

\| summarize P50 = percentile(DurationMs, 50), P95 = percentile(DurationMs, 95), Count = count()

by bin(TimeGenerated, 5m)

\| render timechart

// 2. Split by instance

AppRequests

\| where TimeGenerated \> ago(30m) and Name has "checkout"

\| summarize P95 = percentile(DurationMs, 95) by AppRoleInstance

// 3. Which dependency got slower (join via operation id)

AppRequests

\| where TimeGenerated \> ago(30m) and Name has "checkout"

\| project OperationId

\| join kind=inner (AppDependencies \| where TimeGenerated \> ago(30m)) on OperationId

\| summarize P95 = percentile(DurationMs, 95), Calls = count(), Failed = countif(Success == false) by Target, Name

\| order by P95 desc

// 4. Exceptions in the window

AppExceptions

\| where TimeGenerated \> ago(30m)

\| summarize count() by ExceptionType, OuterMessage

// 5. Changes in the window

AzureActivity

\| where TimeGenerated \> ago(2h) and OperationNameValue endswith "write"

\| project TimeGenerated, Caller, OperationNameValue, \_ResourceId

**Technical Deep Dive:** Operators to know: where, project, extend, summarize, bin, percentile, join, union, make_series, render, parse_json, mv-expand, top, arg_max. Time filter first for performance.

**Step-by-Step:** Confirm → localise → decompose → errors → changes → hypothesis → mitigate.

**Azure Portal Steps:** App Insights → **Logs**, or Log Analytics workspace → **Logs**; pin results to a workbook.

**Root Cause:** (Depends — e.g., downstream payment API latency.)

**Prevention:** Save queries in a query pack; workbook for checkout.

**Interviewer Follow-Up Questions:**

- *"\`requests\` vs \`AppRequests\`?"* — Same data; classic names in the App Insights Logs context, App\* tables in the workspace. Column names differ (duration vs DurationMs, operation_Id vs OperationId).

- *"How do you find the slowest single request?"* — top 1 by DurationMs then open in transaction search.

**Common Mistakes:** Using averages; no time filter; joining huge tables without filtering.

**Key Points to Remember:** Percentiles · localise · join on OperationId · changes.

## B11. Metrics vs logs vs traces

**Question:** Explain metrics, logs and traces and how you use them together in Azure.

**Scenario:** A junior engineer asks why we need all three.

**Interview Answer:**

"Metrics are numbers over time — cheap, fast, ideal for alerts and dashboards, but with little context. Logs are detailed events with properties — good for 'what exactly happened'. Traces connect events across services for one request — good for 'where did the time or error happen'.

In Azure, platform metrics go to the metrics store automatically; logs go to Log Analytics; Application Insights gives distributed tracing using W3C Trace Context, so each request has an operation ID shared across services.

In practice: a metric alert says error rate jumped; logs show the exception type; the trace shows that the error came from the inventory service calling SQL. Each answers a different question."

**Technical Deep Dive:** Metrics: pre-aggregated, dimensions, 1-minute granularity, 93-day retention (platform). Logs: billed by ingestion and retention. Traces: spans with parent/child IDs (OperationId, ParentId, Id). App Insights also produces log-based and standard (pre-aggregated) metrics.

**Step-by-Step:** Alert (metric) → narrow (logs) → localise (trace) → fix.

**Azure Portal Steps:** App Insights → **Metrics**; **Logs**; **Transaction search → end-to-end transaction**; **Application map**.

**KQL (trace for one operation):**

**KQL**

union AppRequests, AppDependencies, AppExceptions, AppTraces

\| where OperationId == "\<operation-id\>"

\| project TimeGenerated, Type, Name, DurationMs, Success, ResultCode, Message, AppRoleName

\| order by TimeGenerated asc

**Root Cause / Prevention:** Missing correlation when services don't propagate headers — use SDK/OpenTelemetry everywhere.

**Interviewer Follow-Up Questions:**

- *"Log-based vs pre-aggregated metrics in App Insights?"* — Pre-aggregated are computed before sampling and are accurate; log-based come from stored telemetry and are affected by sampling.

- *"Custom metrics?"* — TrackMetric/OTel meters; prefer pre-aggregation to control cost.

**Common Mistakes:** Logging everything as text; no correlation IDs.

**Key Points to Remember:** Metrics = alert, logs = detail, traces = path; OperationId ties them.

## B12. Distributed tracing across microservices

**Question:** How do you implement distributed tracing across microservices on AKS and App Service?

**Scenario:** Five services; when a request fails, nobody knows which service caused it.

**Interview Answer:**

"I'd instrument every service with the Azure Monitor OpenTelemetry distro — or the classic Application Insights SDKs for older apps — all sending to Application Insights resources linked to the same workspace. Each service sets a cloud role name, so the Application Map shows each service as a node.

OpenTelemetry automatically propagates the W3C traceparent header on HTTP calls, and the SDKs propagate context over Service Bus and Event Hubs. So one user request has one trace ID across all services.

Then I use the end-to-end transaction view to see the waterfall, and Application Map to see failure rates and latency between services. For sampling, I use consistent sampling so whole traces are kept or dropped together.

If there's an API gateway like API Management or Front Door, I make sure it forwards trace headers too."

**Technical Deep Dive:** OTEL_SERVICE_NAME / cloud_RoleName; traceparent header format; sampling types: fixed-rate, adaptive (classic SDK), rate-limited (OTel distro). APIM has App Insights integration.

**Code (.NET with OTel distro):**

**CSHARP**

// Program.cs

builder.Services.AddOpenTelemetry().UseAzureMonitor(); // reads APPLICATIONINSIGHTS_CONNECTION_STRING

// Set role name via environment variable: OTEL_SERVICE_NAME=orders-api

**Step-by-Step:** Choose SDK/OTel → set role names → single workspace → verify Application Map → verify header propagation through gateways/queues → configure sampling.

**Azure Portal Steps:** App Insights → **Application map**; **Failures → Drill into samples**; **Transaction search**.

**KQL (failure rate between services):**

**KQL**

AppDependencies

\| where TimeGenerated \> ago(1h)

\| summarize Calls = count(), FailPct = round(100.0 \* countif(Success == false) / count(), 2) by AppRoleName, Target

\| order by FailPct desc

**Root Cause (broken traces):** Missing instrumentation in one service, gateway stripping headers, inconsistent sampling.

**Prevention:** Instrumentation in service templates; check traces in pipeline tests.

**Interviewer Follow-Up Questions:**

- *"One App Insights resource or many?"* — Either, as long as they share a workspace for queries; separate resources per service give separate access/cost control.

- *"Trace across a queue?"* — Producer adds context to message properties; consumer starts a linked span.

**Common Mistakes:** Different role names per instance; aggressive independent sampling.

**Key Points to Remember:** OTel distro · role names · W3C traceparent · Application Map · consistent sampling.

## B13. Application performance monitoring

**Question:** How do you find why an API endpoint is slow when infrastructure metrics look fine?

**Scenario:** /api/reports takes 6 seconds; CPU and memory are normal.

**Interview Answer:**

"If infrastructure is fine, the time is usually spent waiting — on a dependency, a lock, or inefficient code. In Application Insights' Performance blade I select the operation and look at the duration distribution and the dependencies it calls. If 5 of the 6 seconds is a SQL call, I go to the database: Query Store to see the query plan and waits.

If dependencies are fast, it's in the code — I'd enable the Application Insights Profiler on App Service, which captures call stacks for slow requests, and the Snapshot Debugger for exceptions. Common findings: N+1 queries, synchronous calls in loops, thread-pool starvation from blocking async code, or large payload serialisation.

Then fix, measure again with the same percentiles, and add a latency alert on that operation."

**Technical Deep Dive:** Performance blade: operations, durations (P50/P95/P99), dependency breakdown, 'Drill into samples'. Profiler (Windows/.NET and Linux .NET) traces run on a sample. Thread starvation appears as high latency with low CPU.

**Step-by-Step:** Performance blade → dependency breakdown → dependency investigation (SQL Query Store / Redis / HTTP) → profiler traces → fix → compare.

**Azure Portal Steps:** App Insights → **Performance** → operation → **Profiler traces**; App Service → **Application Insights → Profiler: On**; SQL → **Query Performance Insight**.

**KQL:**

**KQL**

AppRequests

\| where TimeGenerated \> ago(1d) and Name == "GET /api/reports"

\| project OperationId, DurationMs

\| join kind=inner (AppDependencies \| where TimeGenerated \> ago(1d)) on OperationId

\| summarize DepTimeMs = sum(DurationMs1), Calls = count() by OperationId, DurationMs

\| extend DepShare = round(100.0 \* DepTimeMs / DurationMs, 1)

\| summarize avg(DepShare), avg(Calls), percentile(DurationMs, 95)

**Root Cause:** e.g., N+1 queries — 120 SQL calls per request.

**Prevention:** Performance tests in CI; latency SLOs; code review for data access patterns.

**Interviewer Follow-Up Questions:**

- *"How do you spot thread pool starvation?"* — Latency high, CPU low, many requests queued; .NET counters threadpool-queue-length; profiler shows blocking waits.

- *"Is the profiler safe in production?"* — Yes, it samples briefly with low overhead; still enable thoughtfully.

**Common Mistakes:** Scaling up when it's a code problem.

**Key Points to Remember:** Performance blade → dependencies → Query Store → Profiler → fix → re-measure.

## B14. Azure Monitor Agent and Data Collection Rules

**Question:** How do you migrate from the legacy Log Analytics agent to the Azure Monitor Agent, and what are DCRs?

**Scenario:** 200 VMs still run the MMA agent after its retirement; some data stopped flowing.

**Interview Answer:**

"The Log Analytics agent, MMA, was retired in August 2024, so it's no longer supported and data ingestion may stop. The replacement is the Azure Monitor Agent, which is configured by Data Collection Rules instead of workspace settings.

A DCR defines what to collect — performance counters, Windows events, syslog, text logs — where to send it, and optional KQL transformations. One DCR can be associated with many machines, and a machine can have several DCRs — for example a baseline DCR for all servers and an extra DCR for SQL servers.

For migration, I'd inventory agents, use the DCR config generator to convert the existing workspace configuration into DCRs, deploy AMA and DCR associations through Azure Policy — Azure VMs need a managed identity, Arc for on-premises servers — run both agents in parallel briefly to validate, check for duplicate data, then remove MMA. Solutions like VM insights, Defender and Update Management also have AMA-based replacements."

**Technical Deep Dive:** AMA uses managed identity to authenticate. DCR association (DCRA) links resource to DCR. Data Collection Endpoints needed for some scenarios (e.g., private link, custom logs). Transformations run at ingestion (source \| where ...).

**Step-by-Step:** Inventory (Heartbeat table shows agent category) → design DCRs → policy assignment → validate → remove MMA.

**Azure Portal Steps:** **Monitor → Data Collection Rules → Create** → Resources → Collect and deliver → data source + destination. **Policy** → "Configure Windows/Linux machines to run Azure Monitor Agent and associate them to a DCR" initiatives.

**KQL:**

**KQL**

Heartbeat

\| where TimeGenerated \> ago(1h)

\| summarize LastSeen = max(TimeGenerated) by Computer, Category, Version

\| order by Category

// Category: "Azure Monitor Agent" vs "Direct Agent" (MMA)

**CLI:**

**BASH**

az vm extension set -g \<rg\> --vm-name \<vm\> --name AzureMonitorWindowsAgent \\

--publisher Microsoft.Azure.Monitor --enable-auto-upgrade true

az monitor data-collection rule association create --name dcra-baseline \\

--rule-id \<dcr-resource-id\> --resource \<vm-resource-id\>

**Root Cause (data stopped):** Unsupported agent after retirement; no DCR association after AMA install.

**Prevention:** Policy-based deployment; heartbeat alert for missing agents.

**Interviewer Follow-Up Questions:**

- *"AMA installed but no data?"* — Missing DCR association, missing managed identity, network to DCE/ingestion endpoints, wrong destination.

- *"Can DCRs filter data?"* — Yes, XPath queries for events and KQL transformations.

**Common Mistakes:** Installing AMA without DCR; not removing MMA (duplicate cost).

**Key Points to Remember:** MMA retired · AMA + DCR + DCRA · policy rollout · heartbeat check.

## B15. Diagnostic settings

**Question:** What are diagnostic settings and what goes wrong with them?

**Scenario:** During an investigation, you find the SQL database never sent audit logs.

**Interview Answer:**

"Diagnostic settings tell an Azure resource where to send its resource logs and platform metrics — to a Log Analytics workspace, a storage account for archiving, Event Hubs for streaming, or a partner solution. Resource logs aren't collected by default, so without a diagnostic setting you have nothing.

Common problems: the setting was never created; only some categories were chosen; it was sent to a workspace in a different subscription that someone deleted; or AzureDiagnostics mode was used and hit column limits. A resource can have up to five diagnostic settings.

My approach is policy-driven: DeployIfNotExists policies at management group scope with category groups like allLogs or audit, plus a compliance check. For important resources, the IaC module creates the diagnostic setting too."

**Technical Deep Dive:** Category groups (allLogs, audit) auto-include new categories. Destination table modes: Azure diagnostics vs Resource-specific (recommended). Activity Log has its own subscription-level diagnostic setting.

**Step-by-Step:** Check resource → Diagnostic settings; verify destination exists; verify categories; verify data in workspace.

**Azure Portal Steps:** Resource → **Monitoring → Diagnostic settings → Add diagnostic setting**.

**Commands:**

**BASH**

az monitor diagnostic-settings list --resource \<resource-id\> -o table

az monitor diagnostic-settings create --name diag-law --resource \<resource-id\> \\

--workspace \<law-resource-id\> --logs '\[{"categoryGroup":"allLogs","enabled":true}\]' \\

--metrics '\[{"category":"AllMetrics","enabled":true}\]'

**Root Cause:** Manual process, missing on new resources.

**Prevention:** Policy DINE; module defaults.

**Interviewer Follow-Up Questions:**

- *"How do you send to a third-party SIEM?"* — Event Hubs destination; or Log Analytics data export.

- *"Cost concern with allLogs?"* — Use audit group where enough; DCR transformations on workspace; table plans.

**Common Mistakes:** Thinking metrics/logs are automatic; forgetting Activity Log.

**Key Points to Remember:** Not on by default · destinations · category groups · policy.

## B16. Log Analytics workspace design and retention

**Question:** How do you design Log Analytics workspaces, retention and access?

**Scenario:** Security wants 2 years of audit logs; developers want 30 days of app logs; the cost must stay controlled.

**Interview Answer:**

"I'd keep the number of workspaces small — usually one per environment per region or geography — and use table-level settings for retention. Interactive retention is set per table: for example 30–90 days for application logs, and longer for audit tables. Long-term retention, up to 12 years, keeps data cheaply for compliance; it's searchable via search jobs and restore rather than normal interactive queries.

Table plans also matter: Analytics for data we alert on and query often; Basic or Auxiliary for high-volume verbose logs that are rarely queried.

For access, I use 'resource or workspace permissions' mode, so developers see logs for resources they have access to, and table-level RBAC for sensitive tables. Security gets workspace-wide reader. If security uses Sentinel, it sits on the same workspace or a dedicated security workspace — depending on separation needs."

**Technical Deep Dive:** Default retention 30 days (90 for Sentinel-enabled and App Insights tables free up to 90). Long-term retention (formerly archive) up to 12 years total. Search jobs and restore to query long-term data. Commitment tiers.

**Step-by-Step:** Requirements per data type → workspace count → table plans → retention per table → access mode → cost estimate.

**Azure Portal Steps:** Workspace → **Tables** → table → **Manage table** (plan, interactive retention, total retention). Workspace → **Properties → Access control mode**.

**CLI:**

**BASH**

az monitor log-analytics workspace table update -g \<rg\> --workspace-name \<law\> -n AzureActivity \\

--retention-time 90 --total-retention-time 730

**Root Cause (typical cost blow-up):** Long interactive retention on high-volume tables.

**Prevention:** Retention policy by table, reviewed quarterly.

**Interviewer Follow-Up Questions:**

- *"How do you query data in long-term retention?"* — Search job (results to a new table) or restore a time range.

- *"Separate workspace for security?"* — When security needs strict separation or different region/retention; otherwise one workspace simplifies correlation.

**Common Mistakes:** Workspace per app; same retention for everything.

**Key Points to Remember:** Few workspaces · per-table retention and plans · long-term retention · resource-context access.

## B17. Container and AKS monitoring

**Question:** How do you monitor an AKS cluster end to end?

**Scenario:** A new AKS platform goes live next month; you own observability.

**Interview Answer:**

"Four layers. Cluster and node health: Container Insights for logs and inventory, and Azure Monitor managed service for Prometheus for metrics, visualised in Managed Grafana with the built-in dashboards. Control plane: diagnostic settings for kube-apiserver, kube-audit-admin, cluster-autoscaler logs. Workloads: Application Insights via OpenTelemetry for request traces and dependencies. And platform alerts: recommended Prometheus alert rules for node CPU/memory, pod restarts, OOMKills and deployment replica mismatch.

For cost, I'd use the ContainerLogV2 schema, collect stdout/stderr only from namespaces that need it, and consider the Basic plan for verbose container logs. Cost Analysis add-on for AKS shows namespace-level cost."

**Technical Deep Dive:** Container Insights tables: ContainerLogV2, KubePodInventory, KubeEvents, KubeNodeInventory, InsightsMetrics. Managed Prometheus stores in Azure Monitor workspace; Grafana uses managed identity. DCR for Container Insights controls namespaces and cost presets.

**Step-by-Step:** Enable monitoring add-on → enable Prometheus + Grafana → control-plane diagnostics → alert rule groups → app instrumentation → cost tuning.

**Commands:**

**BASH**

az aks enable-addons -g \<rg\> -n \<aks\> -a monitoring --workspace-resource-id \<law-id\>

az aks update -g \<rg\> -n \<aks\> --enable-azure-monitor-metrics \\

--azure-monitor-workspace-resource-id \<amw-id\> --grafana-resource-id \<grafana-id\>

**KQL:**

**KQL**

KubeEvents

\| where TimeGenerated \> ago(1h) and Reason in ("BackOff","OOMKilling","FailedScheduling","Unhealthy")

\| summarize count() by Namespace, Name, Reason

\| order by count\_ desc

**Azure Portal Steps:** AKS → **Monitor → Insights**; **Settings → Diagnostic settings**; **Monitor → Prometheus rule groups**.

**Root Cause / Prevention:** Missing namespace filtering causes cost spikes — set it from day one.

**Interviewer Follow-Up Questions:**

- *"Container Insights vs Prometheus?"* — Container Insights = logs and inventory; Prometheus = metrics with PromQL; Microsoft recommends both.

- *"Alert on pod restarts?"* — Prometheus rule increase(kube_pod_container_status_restarts_total\[15m\]) \> 3.

**Common Mistakes:** Collecting all namespaces including kube-system verbose logs.

**Key Points to Remember:** Container Insights + Managed Prometheus + Grafana · control-plane diagnostics · app OTel · cost presets.

## B18. Availability tests and synthetic monitoring

**Question:** How do you monitor availability from the user's perspective?

**Scenario:** An outage at 03:00 went unnoticed because there was no traffic.

**Interview Answer:**

"Real-user telemetry needs traffic, so I add synthetic tests. In Application Insights, standard availability tests call key URLs from multiple Azure regions — usually five — every 5 minutes, checking status code, response time, content match and SSL certificate expiry. I alert when, say, 3 of 5 locations fail, which avoids noise from a single location.

For complex flows like login and checkout, I use custom TrackAvailability tests — for example an Azure Function or Playwright script on a timer that runs the user journey and reports results to Application Insights.

For private endpoints, tests must run from inside the network, so I use a custom test running in the VNet."

**Technical Deep Dive:** Standard test features: HTTP verbs, headers, SSL validity check with days-before-expiry, dependent requests. URL ping tests are being retired — use standard tests. Alert: "failed locations ≥ N".

**Step-by-Step:** Identify critical endpoints → create standard tests → alert rule → custom journeys → private tests.

**Azure Portal Steps:** App Insights → **Availability → Add Standard test** → URL, frequency, locations, success criteria → alert.

**Terraform:**

**HCL**

resource "azurerm_application_insights_standard_web_test" "home" {

name = "wt-orders-home"

resource_group_name = azurerm_resource_group.monitoring.name

location = azurerm_resource_group.monitoring.location

application_insights_id = azurerm_application_insights.orders.id

geo_locations = \["emea-gb-db3-azr", "emea-nl-ams-azr", "us-va-ash-azr", "emea-fr-pra-edge", "emea-se-sto-edge"\]

frequency = 300

request { url = "https://orders.example.com/health" }

validation_rules {

expected_status_code = 200

ssl_check_enabled = true

ssl_cert_remaining_lifetime = 14

}

}

**KQL:**

**KQL**

AppAvailabilityResults

\| where TimeGenerated \> ago(1d)

\| summarize SuccessPct = 100.0 \* countif(Success == true) / count() by Name, Location

**Root Cause (missed outage):** No synthetic monitoring.

**Prevention:** Standard tests for every public endpoint by default.

**Interviewer Follow-Up Questions:**

- *"Test hits health endpoint only — enough?"* — Health endpoint should check critical dependencies lightly; plus a journey test.

- *"Cost?"* — Standard tests are billed per execution; keep frequency and locations sensible.

**Common Mistakes:** Alerting on single location failure.

**Key Points to Remember:** Standard tests · multiple regions · N-locations alert · SSL check · custom journeys.

## B19. Log Analytics ingestion failure / data missing

**Question:** A Log Analytics workspace stopped showing data from several resources. How do you troubleshoot?

**Scenario:** Since 11:00, no new rows in AzureDiagnostics or Perf; dashboards are blank.

**Interview Answer:**

"First, is it all data or some? If everything stopped at the same time, I suspect the workspace: daily cap reached, workspace deleted/recreated, or an Azure Monitor incident in Service Health. The workspace has an \_LogOperation function and Operation table that record ingestion problems and daily-cap events.

If only some sources stopped, I check those collection paths: diagnostic settings still pointing to the right workspace ID, AMA heartbeats and DCR associations, network to ingestion endpoints or AMPLS, and whether someone changed a DCR transformation that now drops everything.

I also check for ingestion latency — data may be arriving late rather than missing — by comparing ingestion_time() with TimeGenerated."

**KQL:**

**KQL**

\_LogOperation

\| where TimeGenerated \> ago(1d)

\| project TimeGenerated, Category, Operation, Level, Detail

\| order by TimeGenerated desc

// Ingestion latency

Heartbeat

\| where TimeGenerated \> ago(1h)

\| extend LatencySec = datetime_diff('second', ingestion_time(), TimeGenerated)

\| summarize avg(LatencySec), max(LatencySec)

// Which sources went quiet

Heartbeat

\| summarize LastSeen = max(TimeGenerated) by Computer

\| where LastSeen \< ago(30m)

**Technical Deep Dive:** Daily cap stops billable ingestion until reset time; some tables exempt. Ingestion volume rate limit (default high limit per workspace) can throttle. DCR transformation errors appear in DCR error logs.

**Step-by-Step:** Scope → Service Health → \_LogOperation → daily cap → per-source path checks → latency → fix → alert on cap and heartbeat.

**Azure Portal Steps:** Workspace → **Usage and estimated costs → Daily cap**; **Insights** (Workspace Insights → Health); **Service Health**.

**Root Cause:** e.g., daily cap set to 10 GB after a cost review.

**Prevention:** Alert on \_LogOperation daily cap events; don't use caps in production except as safety net with headroom.

**Interviewer Follow-Up Questions:**

- *"What happens to data when cap is hit?"* — It is dropped, not queued.

- *"How to alert before the cap?"* — Log alert on Usage volume reaching 80% of cap.

**Common Mistakes:** Recreating workspace; ignoring partial outages.

**Key Points to Remember:** All vs some · \_LogOperation · daily cap · DCR/diag paths · latency.

## B20. Leading a production incident using monitoring data

**Question:** Describe how you would lead the troubleshooting of a P1 incident using Azure Monitor.

**Scenario (illustrative):** At 10:05 UK time, the Sev 1 alert "checkout failure rate \> 5%" fires. Multiple teams join a bridge.

**Interview Answer:**

"I'd split roles: an incident commander — maybe me — a communications lead, and investigators. As commander I keep the timeline and decisions.

Then a structured investigation using monitoring. One: confirm impact — failure rate, which regions, which customers — from the workbook. Two: check what changed in the last two hours — deployments, config changes in Activity Log, Azure Service Health. Three: localise — Application Map to see which dependency turned red. Four: decide mitigation quickly — rollback, failover, scale, or feature flag off — even before full root cause. Five: verify recovery with the same metrics, then keep watching for 30 minutes.

Throughout, stakeholders get updates every 30 minutes with impact, actions, and next update time. After recovery, a blameless post-incident review with a timeline from the logs, root cause, and actions — usually including a new alert or test so we detect it earlier next time."

**Technical Deep Dive:** Tools: workbook, Application Map, Failures, Live Metrics, Activity Log, Service Health, Change Analysis (Resource Graph changes), alert history for timeline.

**Step-by-Step:** Declare → roles → impact → changes → localise → mitigate → verify → communicate → review.

**Azure Portal Steps:** Monitor → **Alerts** (alert details & history); App Insights → **Application map**, **Live metrics**; **Service Health**.

**KQL (timeline):**

**KQL**

union

(AppRequests \| where TimeGenerated between (datetime(2026-11-05 09:30) .. datetime(2026-11-05 11:00))

\| summarize Failed = countif(Success == false) by bin(TimeGenerated, 1m) \| extend Event = "Failures"),

(AzureActivity \| where TimeGenerated between (datetime(2026-11-05 09:30) .. datetime(2026-11-05 11:00))

\| where OperationNameValue endswith "write" \| project TimeGenerated, Event = OperationNameValue)

\| order by TimeGenerated asc

**Root Cause:** Determined in review; the point is the process.

**Prevention:** Action items with owners and dates.

**Interviewer Follow-Up Questions:**

- *"Two teams blame each other?"* — Focus on data; the commander keeps it blameless and moves to mitigation.

- *"When do you declare resolved?"* — When user-facing SLIs are back within SLO for a sustained period.

**Common Mistakes:** Everyone investigating the same thing; no communication; no review.

**Key Points to Remember:** Roles · impact · changes · localise · mitigate fast · communicate · review.

# Section 2C — Azure Scalability and Performance (15 Questions)

## C1. Slow at 20,000 concurrent users

**Question:** Your application works normally with 1,000 users but becomes slow with 20,000 concurrent users. How would you investigate and scale the architecture?

**Scenario:** A retail web app on App Service (3 × P1v3) with Azure SQL (S3) slows to 8-second responses during a sale.

**Interview Answer:**

"I'd find the bottleneck with data before adding capacity, because adding web servers in front of a saturated database makes it worse.

I'd reproduce with Azure Load Testing while watching Application Insights and Azure Monitor: where is the time going — web tier CPU or memory, thread starvation, database DTU, a third-party API, or connection limits like SNAT port exhaustion on outbound calls?

In this scenario, the most common finding is the database: DTU at 100%, a few expensive queries, missing indexes. So I'd fix queries and indexes using Query Store, scale the database to vCore with more capacity, add Azure Cache for Redis for read-heavy data like the product catalogue, and serve static content through Front Door with caching.

Then the web tier: make it stateless, turn off ARR affinity, set autoscale rules on CPU and HTTP queue length with a sensible maximum, and pre-warm before the sale. Long-running work like order emails moves to Service Bus and a background worker.

Finally, I run the load test again to confirm we meet the target with headroom."

**Technical Deep Dive:** App Service autoscale (rules-based, or automatic scaling for Premium v2/v3 based on HTTP traffic), per-app scaling, ARR affinity, SNAT ports and VNet integration with NAT Gateway, connection pooling. SQL: DTU vs vCore, Hyperscale, read scale-out on Premium/Business Critical/Hyperscale, Query Store.

**Step-by-Step Troubleshooting:**

**1.** Define target (users, RPS, p95 latency).

**2.** Load test with monitoring.

**3.** Identify saturated component.

**4.** Fix the largest bottleneck first; re-test.

**5.** Add caching/async/CDN.

**6.** Configure autoscale + alerts; capacity plan.

**Azure Portal Steps:** **Azure Load Testing → Create test**; App Insights → **Performance** & **Application map**; SQL database → **Query Performance Insight**, **Intelligent Performance → Recommendations**; App Service plan → **Scale out (App Service plan)**.

**Commands:**

**BASH**

az monitor autoscale create -g \<rg\> --resource \<plan-id\> --name as-orders --min-count 3 --max-count 15 --count 3

az monitor autoscale rule create -g \<rg\> --autoscale-name as-orders --condition "CpuPercentage \> 70 avg 5m" --scale out 2

az monitor autoscale rule create -g \<rg\> --autoscale-name as-orders --condition "CpuPercentage \< 35 avg 10m" --scale in 1

az webapp update -g \<rg\> -n \<app\> --client-affinity-enabled false

**KQL:**

**KQL**

AzureMetrics

\| where ResourceProvider == "MICROSOFT.SQL" and MetricName in ("dtu_consumption_percent","cpu_percent","log_write_percent")

\| where TimeGenerated \> ago(6h)

\| summarize max(Maximum) by MetricName, bin(TimeGenerated, 5m)

\| render timechart

**Root Cause:** Database saturation from inefficient queries; stateful web tier limiting scale-out.

**Prevention:** Regular load tests in pipeline; autoscale; capacity reviews before peak events; latency SLO alerts.

**Interviewer Follow-Up Questions:**

- *"What's SNAT exhaustion and how do you fix it?"* — Outbound connections from App Service share limited SNAT ports; fix with connection reuse/pooling, private endpoints, or VNet integration with NAT Gateway.

- *"Autoscale reacted too slowly?"* — Scale-out takes minutes; pre-scale with schedule-based profiles before known peaks; use automatic scaling with pre-warmed instances.

**Common Mistakes:** "Just increase the App Service plan"; ignoring database; no load test.

**Key Points to Remember:** Measure → database first → cache/CDN/async → stateless autoscale → re-test.

## C2. AKS intermittent latency and pod restarts

**Question:** An AKS application is experiencing intermittent latency and pod restarts. How would you troubleshoot?

**Scenario:** The orders-api deployment shows 15 restarts in an hour; p95 latency spikes every few minutes.

**Interview Answer:**

"I'd split it into two questions: why do pods restart, and why is latency spiky — they're often related.

For restarts: kubectl describe pod shows Last State and exit code. Exit code 137 with OOMKilled means memory limit too low or a leak. Liveness probe failures in Events mean the probe is killing the container — often because the app is slow under load, so the probe times out, which causes more load on the remaining pods — a cascade. kubectl logs --previous shows the crash output.

For latency: CPU throttling is a common hidden cause — if CPU limits are tight, the container is throttled every 100 ms period even when the node is idle. I'd check throttling metrics in Prometheus, node pressure with kubectl top, evictions, and whether HPA is scaling or stuck at max.

Fixes: right requests and limits based on real usage, separate liveness from readiness with sensible timeouts, a startup probe, HPA on CPU or custom metrics, cluster autoscaler for node capacity, and PodDisruptionBudgets."

**Technical Deep Dive:** QoS classes (Guaranteed/Burstable/BestEffort) affect eviction. CFS quota throttling: container_cpu_cfs_throttled_periods_total. HPA requires metrics-server and requests. Cluster autoscaler adds nodes when pods are Pending.

**Step-by-Step:**

**1.** kubectl get pods -o wide — restarts, nodes.

**2.** describe pod — exit code, probe failures, events.

**3.** logs --previous.

**4.** top pods/nodes, throttling metrics, events for evictions.

**5.** HPA status: kubectl get hpa.

**6.** Fix resources/probes; roll out; monitor.

**Commands:**

**BASH**

kubectl get pods -n orders -o wide

kubectl describe pod \<pod\> -n orders \| sed -n '/Last State/,/Ready/p'

kubectl logs \<pod\> -n orders --previous --tail=100

kubectl top pods -n orders --containers

kubectl get hpa -n orders

kubectl get events -n orders --field-selector reason=Evicted

**YAML**

resources:

requests: { cpu: "250m", memory: "512Mi" }

limits: { memory: "1Gi" } \# many teams omit CPU limits to avoid throttling

startupProbe:

httpGet: { path: /health/startup, port: 8080 }

failureThreshold: 30

periodSeconds: 5

livenessProbe:

httpGet: { path: /health/live, port: 8080 }

timeoutSeconds: 3

periodSeconds: 10

failureThreshold: 3

readinessProbe:

httpGet: { path: /health/ready, port: 8080 }

periodSeconds: 5

**PromQL (managed Prometheus):**

**PROMQL**

sum(rate(container_cpu_cfs_throttled_periods_total{namespace="orders"}\[5m\]))

/ sum(rate(container_cpu_cfs_periods_total{namespace="orders"}\[5m\]))

**Root Cause:** e.g., CPU limit 200m caused throttling; latency rose; liveness timed out at 1s; pods restarted — cascading.

**Prevention:** Resource requests from observed usage (VPA recommendations); probe standards; alerts on restarts and throttling.

**Interviewer Follow-Up Questions:**

- *"Should liveness check the database?"* — No; liveness should only check the process itself, or a DB outage restarts every pod.

- *"Pods Pending?"* — Insufficient resources, node selectors/taints, PVC zone mismatch; cluster autoscaler events.

**Common Mistakes:** Increasing replicas without fixing probes; deleting pods repeatedly.

**Key Points to Remember:** Exit code + events + previous logs · throttling · probes · requests/limits · HPA + CA.

## C3. App Service scaling options

**Question:** Explain the scaling options for Azure App Service.

**Scenario:** A team asks whether to use P1v3 with 10 instances or P3v3 with 3.

**Interview Answer:**

"Scale up changes the plan tier and size — more CPU, memory and features like slots and VNet integration. Scale out changes the number of instances. All apps in a plan share the plan's instances.

Scale-out options: manual, rules-based autoscale on metrics or schedules, and automatic scaling on Premium v2/v3 that scales on HTTP traffic with pre-warmed instances, per app.

Choosing: more smaller instances give better resilience and smoother scaling, and zone redundancy needs at least the minimum instances across zones. Bigger instances help memory-heavy or CPU-bound single requests. I'd start from a load test and usually prefer scale-out with a stateless design, using per-app scaling if a plan hosts several apps with different needs."

**Technical Deep Dive:** Zone-redundant App Service plans (Premium v2/v3, Isolated v2) with at least 2–3 instances. Max instances depend on tier (Premium v3 up to 30; more on Isolated). Per-app scaling (numberOfWorkers per site).

**Step-by-Step (choose):** Load test → per-instance capacity → required instances + N+1 → zone requirements → cost compare.

**Azure Portal Steps:** App Service plan → **Scale up** / **Scale out** (Manual, Rules Based, Automatic).

**CLI:**

**BASH**

az appservice plan update -g \<rg\> -n \<plan\> --sku P1v3 --number-of-workers 6

az appservice plan update -g \<rg\> -n \<plan\> --elastic-scale true --max-elastic-worker-count 20 \# automatic scaling

**Root Cause / Prevention:** Wrong sizing → periodic right-sizing using metrics and Advisor.

**Interviewer Follow-Up Questions:**

- *"Does scale-up cause downtime?"* — Generally no restart required for same family, but apps may recycle; test in non-prod.

- *"Why is my autoscale flapping?"* — Scale-in threshold too close to scale-out; use a gap and cool-down.

**Common Mistakes:** Too many apps on one plan; no scale-in rule.

**Key Points to Remember:** Up vs out · rules vs automatic · zone redundancy · per-app scaling.

## C4. VM Scale Sets and autoscale failure

**Question:** Autoscale didn't add instances during a traffic spike. How do you troubleshoot?

**Scenario:** A VMSS stayed at 4 instances while CPU was 95% for 30 minutes.

**Interview Answer:**

"I'd look at the autoscale run history first — Azure records every evaluation and why it did or didn't scale. Common reasons: the profile in effect was a schedule profile with a fixed count; the max count was already reached; the metric chosen wasn't the one spiking — for example the rule used guest memory but the agent wasn't sending it; the cooldown period blocked further actions; or scale-out was attempted but failed because of quota, SKU capacity in the zone, or a failing extension or image.

Then I fix the specific reason: raise the max, fix the metric source, request quota, allow more SKUs or zones, and add an alert on autoscale failures and 'reached max' events."

**Technical Deep Dive:** Autoscale settings: profiles (default/recurrence/fixed date), rules, cooldown (default 5 min), flapping protection. Notifications via autoscale settings. VMSS Flexible vs Uniform orchestration. Instance health via Application Health extension + automatic repairs.

**Step-by-Step:** Autoscale run history → Activity Log for failed scale operations → quota → metric availability → fix → test.

**Azure Portal Steps:** VMSS → **Scaling → Run history**; **Activity log** filtered on "Autoscale"; **Usage + quotas**.

**KQL:**

**KQL**

AutoscaleEvaluationsLog

\| where TimeGenerated \> ago(6h)

\| project TimeGenerated, Profile, MetricName, MetricValue, Threshold, ObservedValue, EstimateCapacityRuleAction, Reason = OperationName

// requires diagnostic settings on the autoscale setting resource

AzureActivity

\| where TimeGenerated \> ago(6h) and OperationNameValue has "autoscale"

\| project TimeGenerated, OperationNameValue, ActivityStatusValue, Properties

**CLI:**

**BASH**

az monitor autoscale show -g \<rg\> -n \<autoscale-name\> --query "profiles\[\].{name:name, cap:capacity}"

az vm list-usage --location uksouth -o table \| grep -i "Dv5"

**Root Cause:** e.g., regional vCPU quota reached.

**Prevention:** Quota monitoring and alerts; capacity reservations for critical scale; test autoscale in load tests.

**Interviewer Follow-Up Questions:**

- *"Predictive autoscale?"* — VMSS supports predictive autoscale on CPU based on historical patterns (forecast mode first).

- *"Scale in killing busy instances?"* — Scale-in policy and instance protection from scale-in.

**Common Mistakes:** Not checking run history; assuming metric exists.

**Key Points to Remember:** Run history · max/cooldown/profile · metric source · quota/capacity · alert.

## C5. Azure Load Balancer troubleshooting

**Question:** Traffic through an Azure Standard Load Balancer to VMs is failing. How do you troubleshoot?

**Scenario:** An internal load balancer fronting two VMs returns timeouts; the VMs respond locally.

**Interview Answer:**

"With Load Balancer, the health probe decides everything. I'd check the 'Health Probe Status' metric — if backends are unhealthy, the LB won't send traffic. Usually the probe port or path is wrong, the app isn't listening on that interface, or an NSG or guest firewall blocks the probe source, which is the AzureLoadBalancer service tag, 168.63.129.16.

Then: is the backend pool correct, is the load-balancing rule on the right frontend and backend port, and for Standard SKU — which is secure by default — is there an NSG allowing the client traffic? Standard LB blocks inbound unless an NSG allows it.

Data path availability metric tells me whether the frontend itself is healthy. Connection Troubleshoot in Network Watcher can test the path from a client VM."

**Technical Deep Dive:** Standard vs Basic (Basic retired September 2025). Probes: TCP/HTTP/HTTPS. Floating IP, session persistence, HA ports for NVAs. Outbound rules / NAT Gateway for SNAT. Metrics: Data Path Availability (VIP availability), Health Probe Status (DIP availability), SNAT connections.

**Step-by-Step:** Probe status → NSG/firewall for 168.63.129.16 → rule ports → backend membership → client NSG → Network Watcher tests.

**Azure Portal Steps:** Load balancer → **Metrics** (Health Probe Status split by Backend IP); **Insights**; **Network Watcher → Connection troubleshoot / IP flow verify**.

**Commands:**

**BASH**

az network lb probe list -g \<rg\> --lb-name \<lb\> -o table

az network lb rule list -g \<rg\> --lb-name \<lb\> -o table

az network watcher test-ip-flow --direction Inbound --protocol TCP --local \<vm-ip\>:443 --remote 168.63.129.16:\* --vm \<vm-name\> -g \<rg\>

**Root Cause:** e.g., guest firewall blocked probe port after hardening.

**Prevention:** Standard NSG rule allowing AzureLoadBalancer; alert on Health Probe Status \< 100.

**Interviewer Follow-Up Questions:**

- *"LB vs App Gateway for a web app?"* — App Gateway for HTTP features (TLS, WAF, path routing); LB for L4 performance/any TCP/UDP.

- *"Why can a VM behind internal LB not reach itself via the LB IP?"* — Hairpin traffic is not supported for backend to its own frontend.

**Common Mistakes:** Forgetting probe source IP in firewall rules.

**Key Points to Remember:** Probe is king · 168.63.129.16 · Standard = closed by default · Network Watcher.

## C6. Application Gateway 502 errors

**Question:** Application Gateway returns 502 Bad Gateway. How do you troubleshoot?

**Scenario:** After a certificate renewal on the backend App Service, App Gateway (WAF v2) returns 502 for all requests.

**Interview Answer:**

"502 means App Gateway couldn't get a valid response from the backend. First check is Backend health in the portal — it says why each backend is unhealthy.

Common causes: health probe failing — wrong path, host header or expected status code; backend certificate not trusted for end-to-end TLS — for example a changed certificate chain or a hostname that doesn't match the certificate; NSG or route table on the App Gateway subnet blocking backend traffic or the required infrastructure ports 65200–65535; backend request timeout too short for slow requests; or DNS failing to resolve the backend FQDN.

For App Service backends, I set 'pick host name from backend target' in the backend settings and use a custom probe with the same host, otherwise App Service rejects the request.

In this scenario, after a certificate change, I'd look at backend health for a certificate error and check the backend settings' host name and trusted root."

**Technical Deep Dive:** v2 SKU trusts well-known CAs for backend certs automatically; private CA needs trusted root certificate upload. Access logs: ApplicationGatewayAccessLog (or AGWAccessLogs resource-specific) show serverStatus, serverRouted, timeTaken. Infra subnet requirements.

**Step-by-Step:**

**1.** Backend health blade → error text.

**2.** Access logs: which backend, status, timing.

**3.** Probe config vs backend reality (curl from a VM in same VNet).

**4.** Certificates (CN/SAN, chain).

**5.** NSG/UDR on AppGW subnet.

**6.** Timeouts and DNS.

**Azure Portal Steps:** Application Gateway → **Monitoring → Backend health**; **Settings → Backend settings / Health probes**; **Logs**.

**KQL:**

**KQL**

AGWAccessLogs

\| where TimeGenerated \> ago(1h) and HttpStatus == 502

\| summarize count() by BackendPoolName, BackendServer = ServerRouted, ServerStatus, RuleName

**CLI:**

**BASH**

az network application-gateway show-backend-health -g \<rg\> -n \<agw\> \\

--query "backendAddressPools\[\].backendHttpSettingsCollection\[\].servers\[\].{addr:address,health:health,log:healthProbeLog}" -o table

**Root Cause:** e.g., backend settings override host name to an old custom domain not on the new certificate.

**Prevention:** Alert on UnhealthyHostCount \> 0; certificate automation (Key Vault-referenced certs); config in IaC.

**Interviewer Follow-Up Questions:**

- *"502 only on long requests?"* — Request timeout in backend settings (default 20s); increase or make the operation async.

- *"How does App Gateway get certificates from Key Vault?"* — User-assigned managed identity with Key Vault Secrets User; listener references the secret ID.

**Common Mistakes:** Restarting the backend without reading backend health.

**Key Points to Remember:** Backend health first · probe/host header · cert trust · NSG/UDR · timeout.

## C7. Front Door for global performance and failover

**Question:** When and how do you use Azure Front Door?

**Scenario:** Users in Asia and the US complain about slow page loads from a UK-hosted app; the business also wants regional failover.

**Interview Answer:**

"Front Door is a global layer 7 entry point on Microsoft's edge network. Users connect to the nearest edge location, TLS terminates there, static content is cached, and dynamic requests travel over Microsoft's backbone to the origin — which reduces latency. It also has WAF and DDoS protection at the edge.

For failover, I'd configure an origin group with origins in two regions, health probes, and priority routing — UK South active and UK West or another region as standby — or latency-based routing for active-active. If the primary fails probes, Front Door routes to the secondary within its probe interval.

For security, the Premium tier connects to origins through Private Link, so the App Service doesn't need public access; otherwise, I restrict origin access to the AzureFrontDoor.Backend service tag plus the X-Azure-FDID header check."

**Technical Deep Dive:** Standard vs Premium (Premium adds Private Link origins, managed WAF rule sets, bot protection). Rules engine; caching with query string behaviour; compression. Health probe frequency affects failover time. Classic Front Door retirement path → Standard/Premium.

**Step-by-Step (setup):** Profile → endpoint → origin group (probes, load balancing settings) → origins → route → WAF policy → custom domain + managed cert → lock down origin.

**Azure Portal Steps:** **Front Door and CDN profiles → Create** → endpoint → **Origin groups** → **Routes** → **Security policies**.

**CLI:**

**BASH**

az afd profile create -g \<rg\> --profile-name afd-shop --sku Premium_AzureFrontDoor

az afd endpoint create -g \<rg\> --profile-name afd-shop --endpoint-name shop

az afd origin-group create -g \<rg\> --profile-name afd-shop --origin-group-name og-web \\

--probe-path /health --probe-protocol Https --probe-request-type GET --probe-interval-in-seconds 30 \\

--sample-size 4 --successful-samples-required 3 --additional-latency-in-milliseconds 50

**Root Cause (slow global users):** Single-region origin with no edge caching.

**Prevention:** CDN caching, compression, monitoring with Front Door logs and latency metrics.

**Interviewer Follow-Up Questions:**

- *"Front Door vs Traffic Manager?"* — Front Door proxies HTTP with caching/WAF and fast failover; Traffic Manager is DNS-only and protocol-agnostic.

- *"How to stop direct access to App Service?"* — Private Link origin, or access restrictions with service tag + FDID header.

**Common Mistakes:** Leaving origins public; caching dynamic authenticated content.

**Key Points to Remember:** Global L7 · edge TLS + cache + WAF · origin groups with probes · Private Link (Premium).

## C8. High availability with Availability Zones

**Question:** How do you make a web application highly available within a region?

**Scenario:** The business asks for 99.95%+ availability for an internal API in UK South.

**Interview Answer:**

"Within a region, availability zones are the main tool — physically separate datacentres with independent power, cooling and networking. I'd make every tier zone-redundant: a zone-redundant App Service plan with at least the minimum instances, or AKS node pools spread across zones; Azure SQL with zone redundancy; zone-redundant storage, ZRS; zone-redundant Application Gateway v2 and Standard Load Balancer; and zone-redundant Key Vault and Service Bus Premium where applicable — many of those are zone-redundant by default in zone-enabled regions.

Then the application must tolerate an instance or zone loss: stateless instances, retries with backoff, health checks, and no single VM. I'd confirm with a zone-down test in Chaos Studio.

The SLA of the whole system is the product of component SLAs, so I'd remove single points of failure and not depend on one non-redundant service."

**Technical Deep Dive:** Zonal vs zone-redundant resources. Composite SLA = multiply. AKS: --zones 1 2 3, topology spread constraints, ZRS disks for stateful workloads. Not every region or SKU supports zones.

**Step-by-Step:** Map components → zone support per service → configure redundancy → app resilience patterns → test.

**Azure Portal Steps:** Creation blades: **Zone redundancy: Enabled** (App Service plan, SQL, App Gateway); **Availability zones** for VMs/VMSS.

**CLI:**

**BASH**

az appservice plan create -g \<rg\> -n plan-api --sku P1v3 --zone-redundant --number-of-workers 3

az aks nodepool add -g \<rg\> --cluster-name \<aks\> -n userpool --zones 1 2 3 --node-count 3

az sql db update -g \<rg\> -s \<server\> -n \<db\> --zone-redundant true

**Root Cause (typical gap):** One non-zonal component (e.g., single VM jumpbox or Basic SKU) breaks HA.

**Prevention:** Policy to require zone redundancy for production SKUs; chaos tests.

**Interviewer Follow-Up Questions:**

- *"Composite SLA example?"* — 99.95% × 99.99% × 99.95% ≈ 99.89%.

- *"Zones protect against what not?"* — Regional outage, bad deployments, data corruption — need DR/backups for those.

**Common Mistakes:** Equating zones with DR.

**Key Points to Remember:** Zone-redundant every tier · stateless app · composite SLA · test.

## C9. Disaster recovery across regions

**Question:** How would you design disaster recovery for a critical application across Azure regions?

**Scenario:** RTO 1 hour, RPO 15 minutes for an order platform: App Service, Azure SQL, Storage, Service Bus.

**Interview Answer:**

"Requirements first — RTO one hour and RPO fifteen minutes allow a warm-standby design rather than full active-active.

Primary in UK South, secondary in UK West or another region allowed by data residency. Front Door routes users with priority routing and health probes. Azure SQL uses an auto-failover group, which replicates asynchronously with an RPO usually in seconds and gives a stable listener endpoint, so the app connection string doesn't change. Storage uses GZRS or RA-GZRS, with customer-managed failover if needed. Service Bus Premium uses geo-replication or geo-disaster recovery. The secondary App Service runs a small number of instances and autoscales after failover. Infrastructure is fully in Terraform so we can rebuild anything missing.

Key Vault secrets and certificates are replicated or deployed to both regions by pipeline. And we run documented failover drills every quarter — that's what proves the RTO."

**Technical Deep Dive:** SQL failover group: read-write listener \<fog\>.database.windows.net, grace period for automatic failover. Storage account failover changes primary; LRS in new primary until re-configured. Service Bus geo-DR replicates metadata only (not messages) — geo-replication (newer) replicates data. Paired regions.

**Step-by-Step (failover runbook):** Declare DR → confirm primary down (Service Health) → fail over SQL group → storage failover if needed → scale secondary → Front Door routes (automatic) → validate → communicate → plan failback.

**Azure Portal Steps:** SQL server → **Failover groups → Add group**; Storage → **Redundancy → Prepare for failover**; Front Door origin group priorities.

**CLI:**

**BASH**

az sql failover-group create -g \<rg\> -s \<primary-server\> -n fog-orders --partner-server \<secondary-server\> \\

--add-db orders --failover-policy Automatic --grace-period 1

az sql failover-group set-primary -g \<rg-secondary\> -s \<secondary-server\> -n fog-orders \# planned failover

**Root Cause (common DR failure):** Untested runbooks; config only in primary region; hard-coded endpoints.

**Prevention:** Quarterly DR drills; IaC for both regions; health dashboards for secondary.

**Interviewer Follow-Up Questions:**

- *"Automatic vs manual SQL failover?"* — Automatic reduces RTO but may fail over during transient issues with possible data loss; many teams choose manual (customer-managed) with clear decision rules.

- *"How do you test without impacting customers?"* — Planned failover in a maintenance window, or test in a cloned environment.

**Common Mistakes:** Confusing backup with DR; forgetting secrets, DNS, and certificates.

**Key Points to Remember:** RTO/RPO → pattern · Front Door · SQL failover groups · GZRS · IaC · drills.

## C10. Azure SQL database latency

**Question:** Azure SQL queries suddenly become slow. How do you investigate?

**Scenario:** Order search went from 200 ms to 4 s after this morning; no code release.

**Interview Answer:**

"I'd check resource saturation first — CPU, data IO, log IO, workers — in the database metrics. If it's near 100%, either load increased or a query got worse.

Then Query Store: I compare top queries by duration and CPU before and after. A sudden change without a release is often a plan regression — the optimiser picked a worse plan, maybe because statistics changed or parameter sniffing. Query Store shows plan changes and lets me force the previous good plan as a quick fix. Automatic tuning can do that automatically with FORCE_LAST_GOOD_PLAN.

I also check blocking and waits — sys.dm_exec_requests, sys.dm_os_wait_stats — long-running transactions or a missing index causing scans and locks.

Fixes: force the good plan short term, then add the right index, update statistics, fix the query, or scale the tier if it's genuine growth."

**SQL:**

**SQL**

-- Top queries by CPU in the last hour (Query Store)

SELECT TOP 10 q.query_id, qt.query_sql_text, SUM(rs.count_executions) AS execs,

AVG(rs.avg_duration)/1000 AS avg_ms, AVG(rs.avg_cpu_time)/1000 AS avg_cpu_ms

FROM sys.query_store_runtime_stats rs

JOIN sys.query_store_plan p ON rs.plan_id = p.plan_id

JOIN sys.query_store_query q ON p.query_id = q.query_id

JOIN sys.query_store_query_text qt ON q.query_text_id = qt.query_text_id

JOIN sys.query_store_runtime_stats_interval i ON rs.runtime_stats_interval_id = i.runtime_stats_interval_id

WHERE i.start_time \> DATEADD(hour, -1, SYSUTCDATETIME())

GROUP BY q.query_id, qt.query_sql_text

ORDER BY avg_cpu_ms DESC;

-- Current blocking

SELECT session_id, blocking_session_id, wait_type, wait_time, status, command

FROM sys.dm_exec_requests WHERE blocking_session_id \<\> 0;

-- Force previous good plan

EXEC sp_query_store_force_plan @query_id = 123, @plan_id = 456;

**Technical Deep Dive:** DTU vs vCore; resource metrics; Query Store (on by default); automatic tuning; Intelligent Insights; Database Watcher for monitoring at scale.

**Step-by-Step:** Metrics → Query Store regressions → waits/blocking → quick fix (force plan/scale) → permanent fix → alerts.

**Azure Portal Steps:** SQL database → **Metrics**; **Query Performance Insight**; **Automatic tuning**; **Intelligent Performance**.

**Root Cause:** Plan regression from parameter sniffing after statistics update.

**Prevention:** Automatic tuning FORCE_LAST_GOOD_PLAN; alerts on CPU/DTU \> 80%; performance tests.

**Interviewer Follow-Up Questions:**

- *"Read-heavy load?"* — Read scale-out replica (ApplicationIntent=ReadOnly) on supported tiers, or caching.

- *"Connection errors 40613/40501?"* — Transient/throttling; implement retry logic.

**Common Mistakes:** Scaling up first; ignoring Query Store.

**Key Points to Remember:** Saturation → Query Store → waits → force plan → index/fix → alert.

## C11. Network troubleshooting between Azure services

**Question:** An App Service can't connect to a VM-hosted API in a peered VNet. How do you troubleshoot?

**Scenario:** App Service with regional VNet integration in spoke A calls 10.2.1.4:443 in spoke B; requests time out.

**Interview Answer:**

"Timeouts usually mean routing or filtering. I check the path hop by hop.

First, App Service VNet integration: is it enabled to the right subnet, and is 'Route All' on so traffic goes into the VNet? Then peering: hub-and-spoke means spoke A to spoke B isn't transitive — traffic must go through the hub firewall with UDRs, or the spokes need direct peering. Then UDRs: does the integration subnet's route table send 10.2.0.0/16 to the firewall, and does the firewall have a rule allowing it, and is return traffic routed symmetrically? Then NSGs on both subnets and the VM's guest firewall.

Tools: from App Service I use the Kudu console with tcpping and nameresolver; Network Watcher's connection troubleshoot and IP flow verify; NSG flow logs or VNet flow logs; and the firewall logs."

**Technical Deep Dive:** VNet peering not transitive. Effective routes on NIC. VNet flow logs (replacing NSG flow logs; NSG flow log creation retired mid-2025). Azure Firewall logs: AZFWNetworkRule, AZFWApplicationRule.

**Step-by-Step:**

**1.** tcpping 10.2.1.4:443 from Kudu.

**2.** Check VNet integration + route all.

**3.** Effective routes on integration subnet path / VM NIC.

**4.** Firewall logs for deny.

**5.** NSG rules (both sides), IP flow verify.

**6.** Guest firewall and service listening.

**Azure Portal Steps:** App Service → **Networking → VNet integration**; **Advanced Tools (Kudu) → Debug console**; VM NIC → **Effective routes**, **Effective security rules**; **Network Watcher → Connection troubleshoot**.

**Commands:**

**BASH**

\# From Kudu console (App Service)

tcpping 10.2.1.4:443

nameresolver api.internal.example.com

az network nic show-effective-route-table -g \<rg\> -n \<vm-nic\> -o table

az network watcher test-connectivity -g \<rg\> --source-resource \<source-vm\> --dest-address 10.2.1.4 --dest-port 443

**KQL (firewall denies):**

**KQL**

AZFWNetworkRule

\| where TimeGenerated \> ago(1h) and DestinationIp == "10.2.1.4" and Action == "Deny"

\| project TimeGenerated, SourceIp, DestinationPort, Policy, RuleCollection, Rule

**Root Cause:** e.g., missing firewall network rule from spoke A integration subnet to spoke B.

**Prevention:** Firewall rules as code; network diagrams; connectivity tests in pipeline.

**Interviewer Follow-Up Questions:**

- *"Asymmetric routing?"* — Return path bypasses firewall; stateful firewall drops it. Ensure UDRs on both sides.

- *"Why tcpping not ping?"* — ICMP is blocked in App Service sandbox.

**Common Mistakes:** Assuming peering is transitive; forgetting route-all.

**Key Points to Remember:** Hop by hop · integration + route all · peering not transitive · UDR + firewall · NSG · Network Watcher.

## C12. Caching strategy with Azure Cache for Redis

**Question:** How and when would you use Azure Cache for Redis to improve performance?

**Scenario:** The product catalogue is read 50,000 times a minute and changes a few times a day.

**Interview Answer:**

"This is ideal for cache-aside. The app first reads from Redis; on a miss, it reads from SQL and writes to Redis with a TTL. When a product changes, we update or delete the cache key. That removes most read traffic from the database and gives sub-millisecond reads.

I'd choose a tier based on size and availability — Standard has a replica; Premium or Enterprise adds zone redundancy, clustering, persistence and VNet options — and use Entra ID authentication and a private endpoint rather than access keys.

Risks to design for: cache stampede when a hot key expires — use jittered TTLs or locking; memory pressure and eviction — monitor used memory and evictions; and connection storms — reuse a single multiplexer connection. Redis also works well for session state so the web tier can stay stateless."

**Technical Deep Dive:** Patterns: cache-aside, write-through, output caching. Metrics: Server Load, Used Memory, Cache Hits/Misses, Connected Clients, Evicted Keys. Eviction policy volatile-lru default. Azure Managed Redis is the newer offering.

**Step-by-Step:** Identify hot reads → design keys + TTL → implement cache-aside → monitor hit ratio → tune.

**Azure Portal Steps:** Redis → **Metrics** (Cache hit ratio), **Advanced settings** (maxmemory-policy), **Authentication** (Entra), **Private endpoint**.

**Code (C# cache-aside):**

**CSHARP**

var cached = await db.StringGetAsync(\$"product:{id}");

if (cached.HasValue) return JsonSerializer.Deserialize\<Product\>(cached!);

var product = await repo.GetProductAsync(id);

await db.StringSetAsync(\$"product:{id}", JsonSerializer.Serialize(product),

TimeSpan.FromMinutes(30 + Random.Shared.Next(0, 5))); // jitter avoids stampede

return product;

**Root Cause (common issue):** Low hit ratio due to bad keys or short TTL; timeouts due to high server load or many connections.

**Prevention:** Alerts on server load \> 80%, evictions, and connection count.

**Interviewer Follow-Up Questions:**

- *"Redis timeouts?"* — Check server load, large values, client thread pool, network; reuse connection.

- *"Data consistency?"* — Invalidate on write, accept short staleness, or use event-driven invalidation.

**Common Mistakes:** Caching without TTL; new connection per request.

**Key Points to Remember:** Cache-aside · TTL + jitter · invalidation · monitor hit ratio/server load · Entra + private endpoint.

## C13. Asynchronous processing for scale (Service Bus / Functions)

**Question:** How would you use queues and serverless to make an order system scale and stay responsive?

**Scenario:** Order submission waits for payment, email and ERP calls; it times out under load.

**Interview Answer:**

"I'd separate the user-facing part from the slow work. The API validates the order, saves it, publishes an 'OrderPlaced' message to Azure Service Bus and returns 202 Accepted quickly. Background consumers — Azure Functions with a Service Bus trigger, or workers on AKS with KEDA — process payment, email and ERP integration independently.

This absorbs spikes because the queue buffers work, and consumers scale based on queue length. Service Bus gives reliability: peek-lock, retries, dead-letter queue for messages that keep failing, and duplicate detection.

For Functions, I'd use the Flex Consumption or Premium plan if I need VNet integration and no cold starts. I'd make handlers idempotent, monitor queue length and dead-letter count, and alert when the oldest message age grows."

**Technical Deep Dive:** Service Bus tiers (Standard vs Premium — Premium for VNet/private endpoints, zones, larger messages). Topics/subscriptions for fan-out. Functions hosting: Flex Consumption, Premium (EP), Dedicated, Container Apps. KEDA ScaledObject for AKS.

**Step-by-Step:** Identify slow synchronous steps → define messages/events → queue/topic design → consumers with retries + DLQ → idempotency → monitoring.

**Azure Portal Steps:** Service Bus namespace → **Queues/Topics** → Metrics (Active Messages, Dead-lettered Messages); Function App → **Scale out**.

**Code (Function, isolated worker):**

**CSHARP**

\[Function("ProcessOrder")\]

public async Task Run(\[ServiceBusTrigger("orders", Connection = "ServiceBus")\] OrderPlaced msg)

{

if (await \_store.AlreadyProcessedAsync(msg.OrderId)) return; // idempotency

await \_payments.ChargeAsync(msg);

await \_store.MarkProcessedAsync(msg.OrderId);

}

// "ServiceBus\_\_fullyQualifiedNamespace" app setting + managed identity = no connection string

**KQL / Metrics:** Alert on DeadletteredMessages \> 0 and ActiveMessages growth.

**Root Cause (original timeouts):** Synchronous chain of slow external calls.

**Prevention:** Async design standard for slow work; queue depth alerts.

**Interviewer Follow-Up Questions:**

- *"Ordering?"* — Use sessions in Service Bus for per-key ordering.

- *"Poison messages?"* — Max delivery count → DLQ; monitor and replay after fix.

**Common Mistakes:** Non-idempotent consumers; ignoring DLQ.

**Key Points to Remember:** 202 + queue · Functions/KEDA scale on queue length · DLQ · idempotency · alerts.

## C14. Reducing application latency end to end

**Question:** What steps would you take to improve overall application responsiveness?

**Scenario:** Business wants p95 page load under 1.5 seconds globally; currently 4 seconds.

**Interview Answer:**

"I'd break latency into parts: network to the user, edge, application, and data — and measure each. Application Insights browser telemetry gives real user page load times by country; server-side telemetry gives server time; dependency data shows database and API time.

Then improve the biggest parts. Network and edge: Front Door with caching, compression, HTTP/2, and static assets on CDN. Application: async calls, avoid chatty dependencies, connection pooling, keep instances warm — Always On and health check for App Service. Data: indexes, caching with Redis, read replicas, and placing compute in the same region as data. Payload: smaller responses, pagination.

I'd set a latency SLO, track it in a workbook, and run performance tests in the pipeline so regressions are caught before production."

**Technical Deep Dive:** Browser telemetry (AppPageViews, AppBrowserTimings); Always On setting; regional co-location; HTTP keep-alive; Front Door caching rules.

**KQL:**

**KQL**

AppPageViews

\| where TimeGenerated \> ago(7d)

\| summarize P95 = percentile(DurationMs, 95) by ClientCountryOrRegion

\| order by P95 desc

AppRequests

\| where TimeGenerated \> ago(7d)

\| summarize P95 = percentile(DurationMs, 95) by Name

\| top 10 by P95

**Step-by-Step:** Measure by layer → biggest contributor first → fix → re-measure → SLO tracking.

**Azure Portal Steps:** App Insights → **Usage → Page views**, **Performance**; App Service → **Configuration → General settings → Always on**.

**Root Cause:** e.g., uncached 3 MB images and cross-region DB calls.

**Prevention:** Performance budgets; pipeline load tests.

**Interviewer Follow-Up Questions:**

- *"Cold starts on App Service?"* — Always On, warm-up via slot swap with applicationInitialization.

- *"Front-end vs back-end time?"* — Compare page view duration with server request duration.

**Common Mistakes:** Only looking at server time.

**Key Points to Remember:** Measure per layer · edge/CDN · app async · data cache · SLO.

## C15. Kubernetes scaling: HPA, KEDA and cluster autoscaler

**Question:** Explain how scaling works on AKS and how you'd configure it.

**Scenario:** A queue-processing service on AKS falls behind during peak; nodes are at 90% allocation.

**Interview Answer:**

"There are two levels. Pod scaling: the Horizontal Pod Autoscaler adds replicas based on CPU or memory relative to requests, or custom metrics. For event-driven work like queues, KEDA is better — it scales on queue length, and can scale to zero. Node scaling: the cluster autoscaler adds nodes when pods are Pending because there isn't room, and removes underused nodes. Node auto-provisioning is another option that picks VM sizes automatically.

For this case: enable the KEDA add-on, create a ScaledObject on the Service Bus queue with a target messages-per-replica, make sure the pods have realistic requests so the scheduler and autoscaler make good decisions, and set the node pool's cluster autoscaler min and max high enough — with quota to match. A separate user node pool, maybe with spot instances for this tolerant workload, saves cost."

**YAML (KEDA with workload identity):**

**YAML**

apiVersion: keda.sh/v1alpha1

kind: TriggerAuthentication

metadata: { name: sb-auth, namespace: orders }

spec:

podIdentity: { provider: azure-workload }

---

apiVersion: keda.sh/v1alpha1

kind: ScaledObject

metadata: { name: order-processor, namespace: orders }

spec:

scaleTargetRef: { name: order-processor }

minReplicaCount: 1

maxReplicaCount: 50

triggers:

\- type: azure-servicebus

metadata:

queueName: orders

namespace: sb-orders-prod

messageCount: "50"

authenticationRef: { name: sb-auth }

**Commands:**

**BASH**

az aks update -g \<rg\> -n \<aks\> --enable-keda

az aks nodepool update -g \<rg\> --cluster-name \<aks\> -n workers --enable-cluster-autoscaler --min-count 2 --max-count 20

kubectl get hpa -n orders \# KEDA creates an HPA behind the scenes

**Technical Deep Dive:** HPA formula desired = ceil(current \* metric / target). Cluster autoscaler scans every ~10s; scale-down after node underutilised ~10 min. PodDisruptionBudgets affect scale-down.

**Step-by-Step:** Requests set → HPA/KEDA → cluster autoscaler → quotas → test with load → alerts on Pending pods and max replicas.

**Azure Portal Steps:** AKS → **Node pools → Scale node pool → Autoscale**; **Settings → Application scaling (KEDA)**.

**Root Cause:** Fixed replica count; autoscaler max too low.

**Prevention:** Alerts on queue age and Pending pods; capacity planning.

**Interviewer Follow-Up Questions:**

- *"HPA not scaling?"* — Missing requests or metrics-server; kubectl describe hpa shows "unable to get metrics".

- *"Spot node risks?"* — Eviction at short notice — only for interruptible workloads with taints/tolerations.

**Common Mistakes:** No requests; HPA and KEDA on the same deployment.

**Key Points to Remember:** HPA (pods) · KEDA (events) · cluster autoscaler (nodes) · requests · quota.

# Section 2D — Azure Cost Optimisation (10 Questions)

## D1. Bill jumps from \$20,000 to \$35,000

**Question:** The company's Azure monthly bill suddenly increases from \$20,000 to \$35,000. How would you investigate and reduce the cost?

**Scenario:** Finance escalates on the 5th of the month; nobody knows what changed.

**Interview Answer:**

"I'd follow a simple path: find it, fix it, prevent it.

Find it: in Cost Management Cost analysis, compare last month with the previous month, grouped by service name. That tells me which service grew — for example Virtual Machines, Log Analytics or bandwidth. Then I drill down by subscription, resource group and resource, and switch to daily view to find the exact date the increase started. I match that date with the Activity Log or deployment history. I also check reservations — an expired reservation silently moves VMs back to pay-as-you-go prices.

Fix it: talk to the owner — tags tell me who — then delete, stop, right-size or reconfigure. Quick wins are often idle environments, oversized SKUs, unattached disks, and verbose logging.

Prevent it: budgets per subscription and resource group with actual and forecast alerts, anomaly alerts, required tags enforced by Azure Policy, a weekly cost review with Advisor recommendations, and showback reports to teams."

**Technical Deep Dive:** Cost analysis views: Accumulated costs, Daily costs, Cost by service, Invoice details; group by Meter category/subcategory. Amortised vs actual cost view (reservations). Anomaly detection in Cost Management (daily, subscription scope). Exports to storage for Power BI/FinOps tools.

**Step-by-Step:**

**1.** Cost analysis: month vs month by service.

**2.** Drill to resource; daily granularity.

**3.** Correlate with Activity Log changes.

**4.** Check reservation/savings plan expiry and utilisation.

**5.** Owner conversation; fix.

**6.** Budgets, anomalies, tags, review cadence.

**Azure Portal Steps:** **Cost Management → Cost analysis** → Scope → View: Cost by resource → Group by: Service name → Granularity: Daily → Compare. **Reservations** → Utilisation. **Budgets → Add**. **Cost alerts → Anomaly alerts**.

**Commands / Queries:**

**BASH**

\# Unattached disks

az disk list --query "\[?diskState=='Unattached'\].{name:name,rg:resourceGroup,gb:diskSizeGb,sku:sku.name}" -o table

\# Unassociated public IPs

az network public-ip list --query "\[?ipConfiguration==null && natGateway==null\].{name:name,rg:resourceGroup}" -o table

**KUSTO**

// Azure Resource Graph: VMs by size and power state

resources

\| where type == "microsoft.compute/virtualmachines"

\| extend size = tostring(properties.hardwareProfile.vmSize), state = tostring(properties.extended.instanceView.powerState.code)

\| summarize count() by size, state

**Root Cause (example):** A performance-test environment with 20 D16 VMs left running; plus Log Analytics ingestion doubled from debug logs.

**Prevention:** Auto-shutdown for non-prod; budgets with action groups; policy-required tags; anomaly alerts; FinOps review.

**Interviewer Follow-Up Questions:**

- *"How fast does cost data appear?"* — Usually within 8–24 hours; not real-time — so also monitor usage metrics.

- *"Can budgets stop resources?"* — Budgets alert; you can trigger an action group → Automation/Logic App to shut down non-prod, but not production.

**Common Mistakes:** Cutting randomly; deleting without owner; ignoring reservations.

**Key Points to Remember:** Service → resource → day → change · reservations · owner · budgets/anomalies/tags.

## D2. Azure Advisor and rightsizing VMs

**Question:** How do you rightsize VMs safely?

**Scenario:** Advisor says 35 VMs are underutilised and could save \$6,000/month.

**Interview Answer:**

"Advisor's recommendation is a starting point, not a decision. It looks at CPU — and memory and network where available — over a lookback period, which I can configure, for example 7 to 30 days, and a CPU threshold.

I'd validate each one: look at peak, not just average — month-end jobs may need the capacity; check memory with guest metrics from the Azure Monitor Agent; and confirm with the owner. Then I resize in non-production first, then production during a change window, because a resize restarts the VM. For families, newer generations — like v5 or v6 — are often cheaper per performance.

Then I'd track the realised saving and review again in a month."

**Technical Deep Dive:** Advisor cost recommendations: rightsize/shutdown VMs, VMSS, reserved instances, savings plans, idle resources, App Service plan rightsizing. Configurable CPU threshold and lookback per subscription. Resize may require deallocation if the size isn't available on the current hardware cluster.

**Step-by-Step:** Export Advisor → validate peaks and memory → owner approval → resize non-prod → production change → measure.

**Azure Portal Steps:** **Advisor → Cost → Right-size or shutdown underutilized virtual machines**; **Advisor → Configuration → VM/VMSS right sizing** (lookback, CPU threshold).

**Commands:**

**BASH**

az advisor recommendation list --category Cost -o table

az vm list-vm-resize-options -g \<rg\> -n \<vm\> -o table

az vm resize -g \<rg\> -n \<vm\> --size Standard_D2s_v5

**KQL:**

**KQL**

Perf

\| where TimeGenerated \> ago(30d) and CounterName in ("% Processor Time","% Committed Bytes In Use")

\| summarize P95 = percentile(CounterValue, 95), Max = max(CounterValue) by Computer, CounterName

**Root Cause:** Over-provisioning at creation "just in case".

**Prevention:** Default small SKUs in modules; Advisor review monthly; policy for allowed SKUs.

**Interviewer Follow-Up Questions:**

- *"What if memory is high but CPU low?"* — Choose a memory-optimised (E-series) size instead of downsizing.

- *"Rightsize before buying reservations?"* — Always.

**Common Mistakes:** Using average CPU only; resizing prod without change window.

**Key Points to Remember:** Advisor = input · peaks + memory · owner · non-prod first · measure.

## D3. Budgets and cost alerts

**Question:** How do you set up budgets and cost alerts that actually work?

**Scenario:** A budget exists but the alert emails go to a former employee.

**Interview Answer:**

"I set budgets at the levels where people own cost — subscription per environment, and resource groups or tags per team. Each budget has thresholds on actual cost at 80% and 100%, and on forecasted cost at 100% or 110%, so we get warned before we overspend.

Alerts go to action groups or distribution lists owned by the team, not individuals. For non-production, the action group can trigger automation — for example, stop dev VMs when the forecast exceeds budget.

In addition I enable anomaly alerts, which catch unusual daily spikes even when we're still under budget. Budgets are created in Terraform so every new subscription gets them automatically."

**Technical Deep Dive:** Budget scopes: billing account, management group, subscription, resource group; filters by tags/resources/meters. Monthly/quarterly/annual. Evaluated a few times a day. Anomaly alerts at subscription scope.

**Terraform:**

**HCL**

resource "azurerm_consumption_budget_subscription" "prod" {

name = "budget-payments-prod"

subscription_id = "/subscriptions/\<sub-id\>"

amount = 12000

time_grain = "Monthly"

time_period { start_date = "2026-11-01T00:00:00Z" }

notification {

enabled = true

threshold = 80

operator = "GreaterThan"

threshold_type = "Actual"

contact_groups = \[azurerm_monitor_action_group.finops.id\]

}

notification {

enabled = true

threshold = 110

operator = "GreaterThan"

threshold_type = "Forecasted"

contact_groups = \[azurerm_monitor_action_group.finops.id\]

}

}

**Step-by-Step:** Define ownership → budgets per scope → thresholds actual + forecast → action groups → anomaly alerts → test.

**Azure Portal Steps:** **Cost Management → Budgets → Add**; **Cost alerts → Add anomaly alert**.

**Root Cause:** Individual email recipients; no forecast alerts.

**Prevention:** Group recipients; budgets as code; quarterly review of budget owners.

**Interviewer Follow-Up Questions:**

- *"Why forecast alerts?"* — They warn mid-month, when you can still act.

- *"Do budgets block spending?"* — No; they alert and can trigger automation.

**Common Mistakes:** Only 100% actual alert.

**Key Points to Remember:** Ownership scopes · actual + forecast · action groups · anomaly alerts · as code.

## D4. Reserved Instances vs Savings Plans

**Question:** How do you decide between Azure Reservations and Savings Plans for compute?

**Scenario:** Compute spend is \$14k/month; 70% is steady 24/7.

**Interview Answer:**

"Both trade a 1- or 3-year commitment for a discount. Reservations are tied to a resource type, region and — for VMs — a size family with instance size flexibility. They usually give the deepest discount and also exist for SQL, Cosmos DB, App Service, Redis, storage capacity and more.

A savings plan for compute commits to an hourly dollar amount and applies automatically across eligible compute — VMs, App Service Premium, Functions Premium, Container Instances, AKS nodes — in any region or size. It's more flexible, with slightly lower discounts than reservations.

With 70% steady usage: first rightsize. Then cover the most stable base — like database and fixed-size VMs — with reservations, cover the rest of the steady compute with a savings plan, and leave the variable 30% on pay-as-you-go or spot. I'd use Advisor's recommendations and the utilisation reports, and keep scope shared so unused commitment is applied elsewhere."

**Technical Deep Dive:** Reservation scopes: single resource group, single subscription, shared, management group. Exchanges and refunds rules (reservations can be exchanged; savings plans can't be cancelled). Savings plan applies after reservations.

**Step-by-Step:** Rightsize → analyse 30–60 days usage → Advisor recommendations → purchase → monitor utilisation → adjust.

**Azure Portal Steps:** **Reservations → Add**; **Savings plans → Add**; **Cost Management → Reservations utilisation**.

**Commands:**

**BASH**

az reservations reservation-order list -o table

az consumption reservation summary list --grain monthly --reservation-order-id \<order-id\> -o table

**Root Cause (wasted commitments):** Buying before rightsizing or migration.

**Prevention:** Utilisation alerts; quarterly commitment review.

**Interviewer Follow-Up Questions:**

- *"Planned move to AKS next year?"* — Savings plan, because it follows compute type changes.

- *"Azure Hybrid Benefit?"* — Use existing Windows Server/SQL licences with Software Assurance for further savings.

**Common Mistakes:** 3-year reservations on unstable workloads.

**Key Points to Remember:** Rightsize first · reservations = deepest, specific · savings plan = flexible · shared scope · monitor utilisation.

## D5. Finding and removing unused resources

**Question:** How do you systematically find and remove waste?

**Scenario:** Hundreds of resources with no owner; nobody wants to delete anything.

**Interview Answer:**

"I use Azure Resource Graph queries and Advisor to find common waste: unattached managed disks, old snapshots, unused public IPs, empty App Service plans, idle load balancers and gateways, stopped-but-not-deallocated VMs — which still cost money — and non-production resources running 24/7.

For deletion, I use a safe process: tag candidates with cleanup-candidate and a date, notify owners via tags or the subscription owner, wait — for example two weeks — then snapshot or back up if needed, and delete. For non-production I enable auto-shutdown schedules.

And I prevent the problem: required owner and expiry tags through policy, so every resource has someone accountable, and ephemeral environments created and destroyed by pipelines."

**Resource Graph:**

**KUSTO**

// Unattached managed disks

resources

\| where type == "microsoft.compute/disks" and properties.diskState == "Unattached"

\| project name, resourceGroup, sku = tostring(sku.name), sizeGb = toint(properties.diskSizeGB), timeCreated = properties.timeCreated

// Empty App Service plans

resources

\| where type == "microsoft.web/serverfarms" and toint(properties.numberOfSites) == 0

\| project name, resourceGroup, sku = tostring(sku.name)

// VMs stopped but still allocated (still billed for compute)

resources

\| where type == "microsoft.compute/virtualmachines"

\| where properties.extended.instanceView.powerState.code == "PowerState/stopped"

\| project name, resourceGroup

**Technical Deep Dive:** "Stopped" (OS shutdown) vs "Deallocated" (no compute billing). Disks and public IPs bill regardless. Snapshots incremental vs full.

**Step-by-Step:** Query → tag → notify → wait → backup → delete → prevent.

**Azure Portal Steps:** **Resource Graph Explorer**; **Advisor → Cost**; VM → **Auto-shutdown**; **Azure Orphaned Resources workbook** (community) for quick view.

**CLI:**

**BASH**

az vm deallocate -g \<rg\> -n \<vm\>

az resource tag --ids \<resource-id\> --tags cleanup-candidate=2026-11-20 --is-incremental

**Root Cause:** No ownership and no lifecycle.

**Prevention:** Required tags; expiry tag automation; ephemeral environments.

**Interviewer Follow-Up Questions:**

- *"How do you decide without an owner?"* — Check Activity Log for creator, metrics for usage, escalate to subscription owner, then the tag-and-wait process.

- *"Automate deletion?"* — Only in sandbox subscriptions with clear policy.

**Common Mistakes:** Deleting without notice; confusing stopped with deallocated.

**Key Points to Remember:** Resource Graph queries · tag → notify → wait → delete · auto-shutdown · tags policy.

## D6. Storage lifecycle management

**Question:** How do you reduce storage costs with lifecycle management?

**Scenario:** 400 TB of logs and backups in Hot tier; most are never read after 30 days.

**Interview Answer:**

"Blob storage has access tiers — Hot, Cool, Cold and Archive — with lower storage cost but higher access cost as you go down. Lifecycle management policies move blobs automatically based on last modified or last access time, and can delete them at end of retention.

For this case: move blobs to Cool after 30 days, Cold after 90, Archive after 180, and delete after the compliance period — say 7 years — filtered by container prefix. If access patterns vary, I'd enable last-access-time tracking and tier based on that.

I'd watch the trade-offs: early deletion charges in Cool, Cold and Archive, Archive rehydration takes hours, and many small blobs make transaction costs significant. Also check redundancy — GRS for logs that don't need geo-redundancy might be unnecessary."

**JSON policy:**

**JSON**

{

"rules": \[{

"enabled": true,

"name": "logs-tiering",

"type": "Lifecycle",

"definition": {

"filters": { "blobTypes": \["blockBlob"\], "prefixMatch": \["logs/"\] },

"actions": {

"baseBlob": {

"tierToCool": { "daysAfterModificationGreaterThan": 30 },

"tierToCold": { "daysAfterModificationGreaterThan": 90 },

"tierToArchive": { "daysAfterModificationGreaterThan": 180 },

"delete": { "daysAfterModificationGreaterThan": 2555 }

},

"snapshot": { "delete": { "daysAfterCreationGreaterThan": 90 } }

}

}

}\]

}

**BASH**

az storage account management-policy create -g \<rg\> --account-name \<sa\> --policy @policy.json

**Technical Deep Dive:** Minimum retention: Cool 30 days, Cold 90, Archive 180. Policy runs about once a day; first run can take up to 24h+.

**Step-by-Step:** Analyse access (Storage insights/metrics, blob inventory) → design rules → apply in test → apply production → monitor cost.

**Azure Portal Steps:** Storage account → **Data management → Lifecycle management → Add rule**; **Blob inventory**.

**Root Cause:** Default Hot tier and no retention.

**Prevention:** Lifecycle policy in storage module; retention policy agreed with compliance.

**Interviewer Follow-Up Questions:**

- *"Rehydration time?"* — Standard priority up to 15 hours; High priority usually under 1 hour for small objects.

- *"Immutable storage?"* — For compliance, time-based retention policies (WORM) prevent deletion — coordinate with lifecycle rules.

**Common Mistakes:** Archiving data that's read often; ignoring early-deletion fees.

**Key Points to Remember:** Tiers · rules by age/last access · minimum retention · rehydration · redundancy.

## D7. AKS cost optimisation

**Question:** How do you reduce AKS costs?

**Scenario:** An AKS cluster costs \$9k/month; node utilisation averages 25%.

**Interview Answer:**

"Low utilisation usually means pods request far more than they use, so the scheduler thinks nodes are full. I'd start by comparing requests with actual usage per namespace — the AKS cost analysis add-on and Container Insights show this. Then right-size requests, using VPA in recommendation mode.

Then node-level: cluster autoscaler with sensible min counts, the right VM sizes for the workload mix, separate node pools — a small system pool and user pools that can scale down — spot node pools for fault-tolerant jobs, and node auto-provisioning if suitable. For dev clusters, stop the cluster outside working hours.

Commercial: savings plan or reservations for the steady baseline nodes. And logs: Container Insights cost presets and namespace filtering, because log ingestion is often a big part of AKS cost."

**Technical Deep Dive:** AKS cost analysis add-on (namespace/workload cost in Cost Management). az aks stop/start. Spot pools: priority Spot, eviction policy Delete, taint kubernetes.azure.com/scalesetpriority=spot:NoSchedule. Free vs Standard tier (uptime SLA) vs Premium.

**Commands:**

**BASH**

az aks update -g \<rg\> -n \<aks\> --enable-cost-analysis

az aks nodepool add -g \<rg\> --cluster-name \<aks\> -n spotpool --priority Spot --eviction-policy Delete \\

--spot-max-price -1 --enable-cluster-autoscaler --min-count 0 --max-count 10 --node-vm-size Standard_D4s_v5

az aks stop -g \<rg\> -n \<aks-dev\>

kubectl top pods -A --sort-by=cpu

**KQL (requests vs usage):**

**KQL**

KubePodInventory

\| where TimeGenerated \> ago(1d)

\| distinct Namespace, Name, ContainerName

\| join kind=inner (

InsightsMetrics

\| where TimeGenerated \> ago(1d) and Name == "cpuUsageNanoCores"

\| extend ContainerName = tostring(parse_json(Tags)\["container.azm.ms/containerName"\])

\| summarize AvgCpuCores = avg(Val) / 1e9 by ContainerName

) on ContainerName

\| summarize sum(AvgCpuCores) by Namespace

**Step-by-Step:** Measure → right-size requests → autoscaler/node pools → spot → stop dev → commitments → logs.

**Azure Portal Steps:** AKS → **Cost analysis**; **Node pools**; **Insights → Containers**; Cost Management → Kubernetes views.

**Root Cause:** Over-requested resources and always-on oversized nodes.

**Prevention:** Request standards; quarterly review; namespace budgets/showback.

**Interviewer Follow-Up Questions:**

- *"Can you put system pods on spot?"* — No; keep system pool on regular nodes.

- *"Bin packing?"* — Fewer larger nodes vs more smaller nodes trade-off; consider pod density and blast radius.

**Common Mistakes:** Lowering requests without data; spot for stateful critical pods.

**Key Points to Remember:** Requests vs usage · autoscaler · spot · stop dev · commitments · log cost.

## D8. Log Analytics ingestion cost

**Question:** Log Analytics is now 30% of the Azure bill. How do you reduce it without losing visibility?

**Scenario:** 250 GB/day ingestion; top tables are ContainerLogV2, AppTraces and AzureDiagnostics.

**Interview Answer:**

"Measure, then reduce at source, at ingestion, and at storage.

Measure: the Usage table and Workspace Insights show GB per table and per resource. I find the top three or four sources.

At source: lower log levels — no debug in production — Application Insights sampling, and diagnostic settings that send only needed categories, for example 'audit' instead of 'allLogs' where enough.

At ingestion: DCR transformations — the workspace transformation DCR for diagnostic data or the AMA DCR — to drop noisy rows like health-probe logs, or unused columns.

At storage: Basic or Auxiliary table plans for high-volume, low-query data like verbose container logs, shorter interactive retention, and long-term retention for compliance.

Commercial: at 250 GB/day, a commitment tier gives a significant discount. Then I set an alert on daily ingestion so a new spike is caught within a day."

**KQL:**

**KQL**

Usage

\| where TimeGenerated \> ago(30d) and IsBillable

\| summarize GBPerDay = sum(Quantity) / 1000 / 30 by DataType

\| top 10 by GBPerDay

ContainerLogV2

\| where TimeGenerated \> ago(1d)

\| summarize GB = sum(\_BilledSize) / 1e9 by PodNamespace, ContainerName

\| top 10 by GB

**Workspace DCR transformation example (drop health checks from AppRequests-like table):**

**KQL**

source

\| where not(Url has "/health")

**Technical Deep Dive:** Table plans: Analytics (full features), Basic (cheaper ingest, limited queries, 30-day interactive), Auxiliary (cheapest, for verbose/audit, limited). Commitment tiers start at 100 GB/day. Transformations can reduce cost but the workspace transformation on Analytics tables may have a processing charge when filtering over 50%.

**Step-by-Step:** Measure → source changes → transformations → plans/retention → commitment tier → alert.

**Azure Portal Steps:** Workspace → **Insights → Usage**; **Tables → Manage table**; **Usage and estimated costs → Pricing tier (commitment)**.

**Root Cause:** Verbose logging defaults and allLogs everywhere.

**Prevention:** Logging standards; ingestion alerts; monthly review.

**Interviewer Follow-Up Questions:**

- *"Basic logs can't be used for what?"* — Not all KQL operators/alerts; not good for dashboards and frequent alerting.

- *"Daily cap?"* — Safety net only; it drops data.

**Common Mistakes:** Daily cap as main control; blindly cutting security logs.

**Key Points to Remember:** Usage table · source · DCR transform · table plans · commitment tier · alert.

## D9. Tagging and cost governance

**Question:** How do you implement tagging for cost allocation and governance?

**Scenario:** 45% of spend has no owner or cost-centre tag.

**Interview Answer:**

"I'd define a small mandatory tag set — for example owner, cost-centre, environment and application — with allowed values documented. Then enforce with Azure Policy: 'Require a tag on resource groups' with Deny, and 'Inherit a tag from the resource group if missing' with Modify, so resources pick up tags automatically. A remediation task fixes existing resources.

In Cost Management, I enable tag inheritance so usage records inherit resource group and subscription tags — that helps for resources that don't support tags. Then I build cost views and exports grouped by cost-centre for showback or chargeback.

I'd roll out in audit mode first, communicate, and track untagged cost weekly until it's near zero."

**Technical Deep Dive:** Tags not inherited by default (resources); policy Modify effect; Cost Management tag inheritance setting; tag limits (50 per resource). Some resources don't emit tags in usage.

**Policy assignment (CLI):**

**BASH**

az policy assignment create --name require-costcentre-rg \\

--policy "96670d01-0a4d-4649-9c89-2d3abc0a5025" \\

--params '{"tagName":{"value":"cost-centre"}}' --scope /providers/Microsoft.Management/managementGroups/\<mg\>

\# 96670d01-... = built-in "Require a tag on resource groups"

az policy assignment create --name inherit-costcentre --mi-system-assigned --location uksouth \\

--policy "ea3f2387-9b95-492a-a190-fcdc54f7b070" \\

--params '{"tagName":{"value":"cost-centre"}}' --scope /providers/Microsoft.Management/managementGroups/\<mg\>

\# cd3aa116-... = built-in "Inherit a tag from the resource group if missing"

**Step-by-Step:** Define tags → audit → enforce on RGs → inherit → remediate → Cost Management views → track.

**Azure Portal Steps:** **Policy → Definitions** → search "tag" → Assign; **Cost Management → Settings → Tag inheritance**; Cost analysis → Group by tag.

**Root Cause:** Optional tags and no enforcement.

**Prevention:** Policy + IaC modules that require tags.

**Interviewer Follow-Up Questions:**

- *"Shared costs like the hub firewall?"* — Allocate with cost allocation rules or split by agreed percentages.

- *"Deny on resources too?"* — Can break deployments of resources created by Azure (e.g., AKS node RG); prefer RG deny + inherit.

**Common Mistakes:** Too many tags; Deny on all resource types.

**Key Points to Remember:** Small mandatory set · RG require + inherit · tag inheritance in Cost Management · showback.

## D10. Building a FinOps practice

**Question:** As a senior engineer, how would you build ongoing cost governance rather than one-off savings?

**Scenario:** Leadership wants predictable cloud spend as the company grows 50% next year.

**Interview Answer:**

"I'd follow the FinOps cycle: inform, optimise, operate.

Inform: everyone can see their own costs — tags, Cost Management views per team, monthly showback reports, unit costs like cost per order or per customer where possible.

Optimise: a backlog of savings from Advisor, rightsizing, commitments, storage lifecycle, log ingestion and architecture changes, prioritised by saving versus effort and risk.

Operate: guardrails in policy — allowed SKUs and regions, required tags, auto-shutdown for dev; budgets and anomaly alerts; cost estimates in pull requests for Terraform with tools like Infracost; a monthly review with engineering and finance; and forecasting based on growth.

The aim is that engineers think about cost as a design quality, alongside reliability and security — not something finance chases afterwards."

**Technical Deep Dive:** FinOps Framework (FinOps Foundation); FinOps toolkit/hubs from Microsoft; Cost Management exports (FOCUS format); unit economics.

**Step-by-Step:** Visibility → ownership → guardrails → optimisation backlog → reviews → forecasting.

**Azure Portal Steps:** **Cost Management → Exports** (to storage, FOCUS); **Budgets**; **Advisor score**.

**Code (Infracost in pipeline):**

**YAML**

\- script: \|

infracost breakdown --path . --format json --out-file infracost.json

infracost comment azure-repos --path infracost.json --azure-access-token \$(System.AccessToken) \\

--pull-request \$(System.PullRequest.PullRequestId) --repo-url \$(Build.Repository.Uri) --behavior update

displayName: Cost estimate on PR

env:

INFRACOST_API_KEY: \$(INFRACOST_API_KEY)

**Root Cause (unpredictable spend):** No ownership, no forecasting, no design-time cost thinking.

**Prevention:** The operating cadence itself.

**Interviewer Follow-Up Questions:**

- *"How do you balance cost vs reliability?"* — Agree SLOs first; spend what's needed for them; remove waste that doesn't contribute.

- *"Metrics for success?"* — % untagged spend, commitment coverage/utilisation, unit cost trend, forecast accuracy.

**Common Mistakes:** Treating cost as finance-only.

**Key Points to Remember:** Inform → optimise → operate · ownership · guardrails · PR cost estimates · unit cost.

# Section 2E — Azure DevOps and CI/CD (15 Questions)

## E1. Production deployment fails halfway

**Question:** A production deployment fails halfway through. How would you recover without impacting customers?

**Scenario:** A release updates the App Service, then fails on the database migration step; the new code is live but the schema change didn't apply.

**Interview Answer:**

"First I check customer impact using the health endpoint, App Insights failure rate and availability tests. If customers are impacted, I roll back the application immediately — I don't debug while users are failing.

How depends on the strategy. If we deployed to a staging slot and swapped, I swap back. If we deployed directly, I redeploy the previous artifact — that's why every build is versioned and kept. On AKS, kubectl rollout undo or helm rollback.

The database is the hard part. Here the migration failed, so the schema is still the old one, and the old code matches it — rolling back the app is safe. If the migration had partly applied, I'd check the migration tool's history table to see exactly which steps ran.

Then root cause from the pipeline logs, fix forward through the pipeline, and in the review improve the process: migrations run before the app deploy and are backward-compatible — expand then contract — so either app version works with the schema; slot deployment with smoke tests; and automated rollback when health checks fail."

**Technical Deep Dive:** Expand/contract: add columns/tables (expand) → deploy code that uses both → migrate data → remove old (contract) in a later release. Migration tools: EF Core migrations, Flyway, Liquibase, DACPAC (SqlAzureDacpacDeployment). Deployment jobs support on: failure hooks for automated rollback.

**Step-by-Step:**

**1.** Assess impact (health, failure rate).

**2.** Roll back app (swap / redeploy previous / rollout undo).

**3.** Inspect DB state (migration history).

**4.** Communicate.

**5.** Root cause from logs.

**6.** Fix and redeploy; improve pipeline.

**Azure Portal / ADO Steps:** Pipelines → run → failed stage logs; **Environments → payments-prod → Deployments** (history); App Service → **Deployment slots → Swap**.

**YAML (rollback hook):**

**YAML**

\- deployment: DeployProd

environment: payments-prod

strategy:

runOnce:

deploy:

steps:

\- script: ./deploy.sh \$(imageTag)

on:

failure:

steps:

\- script: ./deploy.sh \$(previousTag)

displayName: Automatic rollback to previous version

success:

steps:

\- script: ./smoke-test.sh

**Root Cause:** e.g., migration timed out on a large table lock.

**Prevention:** Online/backward-compatible migrations; run migrations as separate stage; smoke tests; deploy smaller changes more often.

**Interviewer Follow-Up Questions:**

- *"Rollback vs roll forward?"* — Rollback when impact is ongoing; roll forward when fix is trivial/faster or rollback is impossible.

- *"How do you know the previous version?"* — Environment deployment history or release tags; Helm history; image tags.

**Common Mistakes:** Re-running the whole pipeline blindly; manual changes in production.

**Key Points to Remember:** Impact → rollback → DB state → communicate → root cause → safer pipeline.

## E2. Pipeline works in development but fails in production

**Question:** A pipeline works in development but fails in production. How would you troubleshoot?

**Scenario:** The same YAML deploys fine to dev; the prod stage fails with AuthorizationFailed at the Terraform apply step, and later with a timeout reaching Key Vault.

**Interview Answer:**

"Same code but different environment means something about the environment differs. I compare five things.

One, identity and permissions: prod uses a different service connection — does it have the right role on the right scope? AuthorizationFailed tells me it doesn't — maybe it has Contributor but the step creates a role assignment.

Two, policy: production often has stricter Azure Policy — Deny on public IPs or unapproved SKUs — so the error says RequestDisallowedByPolicy.

Three, network: production Key Vault, storage or SQL often has public access disabled. Microsoft-hosted agents run on the internet, so they can't reach private endpoints. We need self-hosted agents or Managed DevOps Pools in the VNet.

Four, variables and secrets: a missing variable group link or Key Vault secret in prod.

Five, pipeline checks: approvals, branch control or exclusive lock on the prod environment.

I read the exact error, compare the two stages side by side, fix the difference in code, and I'd add the prod checks to a pre-prod environment so it matches production more closely."

**Technical Deep Dive:** Managed DevOps Pools (Azure-managed scale set agents with VNet injection); VMSS agent pools; agent outbound IPs; private endpoints DNS from the agent VNet.

**Step-by-Step:**

**1.** Exact error per failing step.

**2.** Diff service connections/RBAC.

**3.** Check Policy compliance/denies.

**4.** Check network path from agent (nslookup/curl in a script step).

**5.** Compare variables/variable groups.

**6.** Fix in code; align pre-prod with prod.

**ADO Steps:** **Project settings → Service connections** (compare); **Pipelines → Library** (variable groups); **Environments → Approvals and checks**; **Agent pools**.

**YAML (debug step):**

**YAML**

\- task: AzureCLI@2

displayName: Diagnose prod access

inputs:

azureSubscription: sc-payments-prod

scriptType: bash

scriptLocation: inlineScript

inlineScript: \|

az account show -o table

az role assignment list --assignee \$(az account show --query user.name -o tsv) --all -o table

nslookup kv-payments-prod.vault.azure.net

curl -s -o /dev/null -w "%{http_code}\n" https://kv-payments-prod.vault.azure.net/healthstatus \|\| true

**Root Cause:** e.g., prod Key Vault only reachable via private endpoint; hosted agent couldn't connect.

**Prevention:** Pre-prod mirrors prod controls; self-hosted/Managed DevOps Pools for private resources; documented environment differences.

**Interviewer Follow-Up Questions:**

- *"Managed DevOps Pools vs VMSS agents?"* — MDP is Microsoft-managed (images, scaling, VNet injection) with less maintenance.

- *"Can you allow hosted agents through the firewall?"* — Their IP ranges are broad and change weekly; not recommended for production data planes.

**Common Mistakes:** Granting Owner to "fix" it; opening public access.

**Key Points to Remember:** Identity · policy · network/agents · variables · checks — read the error.

## E3. Designing a multi-stage YAML pipeline

**Question:** Design a multi-stage YAML pipeline for a containerised API deployed to AKS.

**Scenario:** A new microservice needs CI/CD to dev, test and prod clusters.

**Interview Answer:**

"Stages: Build, then DeployDev, DeployTest, DeployProd.

Build runs on every PR and main commit: unit tests, code analysis, dependency scan, Docker build with an immutable tag — commit SHA — image scan, push to ACR, and publish the Kubernetes manifests or Helm chart as an artifact. On PRs we stop after build.

Deployment stages use deployment jobs targeting Azure DevOps environments, with Kubernetes resources linked, so we get history and traceability. Dev deploys automatically from main; test after dev succeeds; prod requires approval and branch control on the environment.

The same image is promoted through all environments — build once, deploy many. Configuration differences come from per-environment values files and Key Vault, not rebuilds. Smoke tests run after each deployment; failure triggers rollback. Common steps live in a shared template repository."

**YAML:**

**YAML**

trigger: { branches: { include: \[ main \] } }

pr: { branches: { include: \[ main \] } }

resources:

repositories:

\- repository: templates

type: git

name: Platform/pipeline-templates

ref: refs/tags/v2.3.0

variables:

imageRepo: orders-api

tag: \$(Build.SourceVersion)

stages:

\- stage: Build

jobs:

\- job: Build

pool: { vmImage: ubuntu-latest }

steps:

\- template: steps/dotnet-test.yml@templates

\- task: Docker@2

inputs:

containerRegistry: sc-acr

repository: \$(imageRepo)

command: buildAndPush

Dockerfile: src/Dockerfile

tags: \$(tag)

\- publish: deploy/helm

artifact: chart

\- stage: DeployDev

dependsOn: Build

condition: and(succeeded(), ne(variables\['Build.Reason'\], 'PullRequest'))

jobs:

\- template: jobs/helm-deploy.yml@templates

parameters: { env: dev, serviceConnection: sc-aks-dev, valuesFile: values-dev.yaml, tag: \$(tag) }

\- stage: DeployProd

dependsOn: DeployDev

condition: and(succeeded(), eq(variables\['Build.SourceBranch'\], 'refs/heads/main'))

jobs:

\- template: jobs/helm-deploy.yml@templates

parameters: { env: prod, serviceConnection: sc-aks-prod, valuesFile: values-prod.yaml, tag: \$(tag) }

**YAML**

\# jobs/helm-deploy.yml (in templates repo)

parameters:

\- name: env

\- name: serviceConnection

\- name: valuesFile

\- name: tag

jobs:

\- deployment: Deploy\_\${{ parameters.env }}

environment: orders-\${{ parameters.env }}

pool: { vmImage: ubuntu-latest }

strategy:

runOnce:

deploy:

steps:

\- task: HelmDeploy@1

inputs:

connectionType: Azure Resource Manager

azureSubscriptionEndpoint: \${{ parameters.serviceConnection }}

azureResourceGroup: rg-orders-\${{ parameters.env }}

kubernetesCluster: aks-orders-\${{ parameters.env }}

namespace: orders

command: upgrade

chartType: FilePath

chartPath: \$(Pipeline.Workspace)/chart

releaseName: orders-api

overrideValues: image.tag=\${{ parameters.tag }}

valueFile: \$(Pipeline.Workspace)/chart/\${{ parameters.valuesFile }}

arguments: --atomic --timeout 5m

**Technical Deep Dive:** --atomic makes Helm roll back on failure. Template references pinned to a tag. Deployment jobs download pipeline artifacts automatically.

**Step-by-Step:** Template repo → build stage → environments + checks → deploy templates → smoke tests → rollback.

**ADO Steps:** **Pipelines → Environments → New** (add Kubernetes resource); **Approvals and checks**.

**Root Cause / Prevention:** N/A (design). Prevent drift with shared templates and required-template check.

**Interviewer Follow-Up Questions:**

- *"Why commit SHA tag?"* — Immutable and traceable to code.

- *"Why pin template version?"* — Template changes can't break all pipelines at once.

**Common Mistakes:** Rebuilding per environment; latest tag.

**Key Points to Remember:** Build once · environments + checks · templates pinned · Helm --atomic · smoke tests.

## E4. Deployment approvals and checks

**Question:** How do you control who and what can deploy to production?

**Scenario:** An auditor asks how you ensure only reviewed code reaches production.

**Interview Answer:**

"Several layers. In the repository, branch policies on main: required pull request reviewers, linked work items, successful build validation, and no direct pushes. So all code on main is reviewed.

In the pipeline, the production environment has approvals and checks: a branch control check so only main can deploy; a required-template check so the pipeline must extend our approved template with security scans; a manual approval from the service owner; business hours; and optionally an Azure Monitor check that blocks deployment if production alerts are active. The production service connection has the same branch control.

Everything is logged — who approved, which commit, which pipeline run — giving the auditor a full trail from work item to deployment."

**Technical Deep Dive:** Checks on protected resources: environments, service connections, agent pools, variable groups, secure files, repositories. Check types: Approvals, Branch control, Business hours, Required template, Evaluate artifact, Invoke Azure Function, Invoke REST API, Query Azure Monitor alerts, Exclusive lock. Checks are evaluated before the stage starts.

**Step-by-Step:** Branch policies → environment checks → service connection checks → pipeline permissions → audit stream.

**ADO Steps:** **Repos → Branches → main → Branch policies**; **Pipelines → Environments → (env) → ⋮ → Approvals and checks**; **Organization settings → Auditing** (stream to Log Analytics).

**YAML (extends required template):**

**YAML**

extends:

template: secure-pipeline.yml@templates

parameters:

buildSteps:

\- script: dotnet build

**Root Cause (audit failure):** Approvals only in YAML (bypassable), direct pushes allowed.

**Prevention:** Policies + checks; audit streaming.

**Interviewer Follow-Up Questions:**

- *"Can a developer bypass approvals by editing YAML?"* — No; checks live on the resource, not in YAML.

- *"Separation of duties?"* — Approver ≠ author; configure "approvers can't approve their own runs".

**Common Mistakes:** Classic release gates only; no branch control.

**Key Points to Remember:** Branch policies + environment checks + service connection checks + audit.

## E5. Secrets management in pipelines

**Question:** How do you handle secrets in Azure DevOps pipelines securely?

**Scenario:** Pipeline variables contain database passwords in plain text in YAML.

**Interview Answer:**

"Goal one is to have no secrets: workload identity federation for Azure access, managed identities for apps, Entra ID authentication for SQL and Storage.

For secrets that remain — third-party API keys, for example — they live in Azure Key Vault. The pipeline gets them either through a variable group linked to Key Vault or the AzureKeyVault task, using the service connection's identity, which needs Key Vault Secrets User. Secret variables are masked in logs and are not passed to scripts automatically — you must map them explicitly to environment variables, which avoids accidental exposure.

I'd remove the plaintext secrets from YAML, rotate them because they're in Git history, add secret scanning to block future commits, and restrict who can edit variable groups and pipelines."

**Technical Deep Dive:** Secret variables: masked, not available to forked PR builds, need explicit env: mapping. Variable group with Key Vault link fetches latest at runtime. GitHub Advanced Security for Azure DevOps: secret scanning push protection.

**YAML:**

**YAML**

variables:

\- group: kv-payments-prod \# linked to Key Vault

steps:

\- script: ./call-provider.sh

env:

PROVIDER_API_KEY: \$(provider-api-key) \# Key Vault secret names map to variables

**Step-by-Step:** Inventory secrets → remove where possible (identity) → move to Key Vault → link/task → rotate exposed ones → scanning → permissions.

**ADO Steps:** **Pipelines → Library → + Variable group → Link secrets from an Azure key vault**; **Repos → Advanced Security** settings.

**Root Cause:** Convenience; no standard.

**Prevention:** Push protection; template enforcing Key Vault usage; reviews.

**Interviewer Follow-Up Questions:**

- *"Can masking be bypassed?"* — Yes, e.g., base64-encoding output; so restrict who can edit pipelines and don't print secrets.

- *"Secure files?"* — For certificates/keystores, use the secure files library with permissions.

**Common Mistakes:** echo \$(secret); leaving old secrets unrotated.

**Key Points to Remember:** No-secret first · Key Vault · explicit env mapping · rotate exposed · scanning.

## E6. Azure Key Vault integration end to end

**Question:** Explain how an application and pipeline integrate with Key Vault, including rotation.

**Scenario:** A certificate and an API key need rotation every 90 days without downtime.

**Interview Answer:**

"The app reads secrets at runtime via managed identity — on App Service with Key Vault references, which the platform refreshes periodically, or on AKS with the Secrets Store CSI driver and workload identity, which can sync on a polling interval. The app must not cache secrets forever.

For rotation, Key Vault emits Event Grid events like 'SecretNearExpiry'. An Azure Function subscribed to that event generates a new key with the provider, stores it as a new version, and the apps pick it up on refresh. For two-key services like Storage or many APIs, I use dual-credential rotation — rotate the unused key, switch, then rotate the other — so there's no downtime.

For certificates, Key Vault can auto-renew from integrated CAs like DigiCert or for self-signed, and App Service, App Gateway and Front Door can reference the Key Vault certificate and pick up new versions automatically when referenced without a version."

**Technical Deep Dive:** App Service Key Vault reference refresh (~24h, or on config change/restart); versionless references. CSI driver rotationPollInterval. Event Grid event types: SecretNearExpiry, SecretExpired, SecretNewVersionCreated, CertificateNearExpiry.

**Code:**

**TEXT**

App setting: ProviderApiKey = @Microsoft.KeyVault(SecretUri=https://kv-payments-prod.vault.azure.net/secrets/provider-api-key/)

**YAML**

apiVersion: secrets-store.csi.x-k8s.io/v1

kind: SecretProviderClass

metadata: { name: kv-orders, namespace: orders }

spec:

provider: azure

parameters:

clientID: \<uami-client-id\> \# workload identity

keyvaultName: kv-orders-prod

tenantId: \<tenant-id\>

objects: \|

array:

\- \|

objectName: provider-api-key

objectType: secret

**BASH**

az aks enable-addons -g \<rg\> -n \<aks\> -a azure-keyvault-secrets-provider

az aks update -g \<rg\> -n \<aks\> --enable-secret-rotation --rotation-poll-interval 2m

**Step-by-Step:** Identity → RBAC → references/CSI → Event Grid rotation function → test rotation in non-prod → alerts on near-expiry.

**Azure Portal Steps:** Key Vault → **Events → + Event Subscription**; **Secrets → secret → Rotation policy** (for keys); **Certificates → Issuance policy**.

**Root Cause (typical outage):** Hard-coded secret versions; app caches secret at startup.

**Prevention:** Versionless references; rotation runbooks; expiry alerts.

**Interviewer Follow-Up Questions:**

- *"Key Vault throttling?"* — Service limits per vault; cache secrets in the app for a short period; don't read per request.

- *"Soft delete & purge protection?"* — Prevent permanent loss; purge protection mandatory for some integrations (e.g., CMK).

**Common Mistakes:** Pinning versions; reading Key Vault on every request.

**Key Points to Remember:** Managed identity · references/CSI · Event Grid rotation · dual keys · versionless certs.

## E7. Docker image builds and best practices

**Question:** How do you build secure, efficient Docker images in CI?

**Scenario:** Images are 1.8 GB, run as root, and builds take 15 minutes.

**Interview Answer:**

"Multi-stage builds: build in an SDK image, copy only the published output into a small runtime image — for .NET the aspnet or chiseled images, for Node an alpine or distroless image. That alone often cuts size by 70–90%.

Order layers so dependency restore comes before copying source, so Docker caches it. Use a .dockerignore to avoid sending bin, obj, .git into the context. Pin base image versions, and rebuild regularly to get patches.

Security: run as non-root, no secrets in layers or build args, scan the image with Trivy or Defender for Containers, and fail the build on critical vulnerabilities. Tag with the commit SHA and sign images if supply-chain requirements exist.

For build speed, use cache from the registry or ACR Tasks, and only rebuild when inputs change."

**Dockerfile:**

**DOCKERFILE**

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

COPY src/Orders.Api/Orders.Api.csproj src/Orders.Api/

RUN dotnet restore src/Orders.Api/Orders.Api.csproj

COPY . .

RUN dotnet publish src/Orders.Api/Orders.Api.csproj -c Release -o /app --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0-noble-chiseled

WORKDIR /app

COPY --from=build /app .

USER \$APP_UID

EXPOSE 8080

ENTRYPOINT \["dotnet", "Orders.Api.dll"\]

**Pipeline scan step:**

**YAML**

\- script: \|

docker run --rm -v /var/run/docker.sock:/var/run/docker.sock aquasec/trivy:latest \\

image --exit-code 1 --severity CRITICAL \<acr-name\>.azurecr.io/orders-api:\$(Build.SourceVersion)

displayName: Scan image (fail on critical)

**Technical Deep Dive:** Layer caching, BuildKit, --cache-from, chiseled images have no shell/package manager. ACR Tasks can build in Azure and trigger on base image updates.

**Step-by-Step:** Multi-stage → layer ordering → .dockerignore → non-root → scan → tag → push.

**Root Cause (slow/big images):** Single-stage SDK images; cache-busting COPY order.

**Prevention:** Dockerfile templates; scan gates.

**Interviewer Follow-Up Questions:**

- *"Debugging a chiseled image without shell?"* — kubectl debug with an ephemeral container.

- *"Why pin base images by digest?"* — Reproducibility; tags can move.

**Common Mistakes:** Secrets in ARG; latest tags; root user.

**Key Points to Remember:** Multi-stage · cache order · non-root · scan · immutable tags.

## E8. Azure Container Registry security and authentication failures

**Question:** Pods fail with ImagePullBackOff from ACR. How do you troubleshoot and secure ACR?

**Scenario:** After disabling ACR public network access, new pods can't pull images.

**Interview Answer:**

"kubectl describe pod events tell me the exact pull error. 'unauthorized' means authentication — the kubelet identity lacks AcrPull. 'not found' means a wrong name or tag. 'i/o timeout' or 'no such host' points to network or DNS — which fits disabling public access.

For network: the AKS VNet needs a private endpoint to ACR and the privatelink.azurecr.io private DNS zone linked, with records for both the registry and its regional data endpoint. If ACR is geo-replicated, each replica region needs its data endpoint record.

For auth: az aks check-acr validates both auth and connectivity from inside the cluster.

For overall security: Premium SKU for private endpoints, admin user disabled, AcrPull through the kubelet managed identity, AcrPush only for pipeline identities, Defender for Containers scanning, retention policies for untagged manifests, and optionally content trust or Notation signing."

**Commands:**

**BASH**

kubectl describe pod \<pod\> -n \<ns\> \| grep -A5 Events

az aks check-acr -g \<rg\> -n \<aks\> --acr \<acr-name\>.azurecr.io

az acr show -n \<acr-name\> --query "{public:publicNetworkAccess, admin:adminUserEnabled, sku:sku.name}"

az acr update -n \<acr-name\> --admin-enabled false

az aks update -g \<rg\> -n \<aks\> --attach-acr \<acr-name\>

nslookup \<acr-name\>.azurecr.io \# from a pod/VM in the AKS VNet → private IP expected

**Technical Deep Dive:** ACR data endpoints (\<registry\>.\<region\>.data.azurecr.io) — dedicated data endpoints. Roles: AcrPull, AcrPush, AcrDelete; or ABAC-enabled repository permissions. Trusted services exception.

**Step-by-Step:** Events → error class → auth (check-acr, role) → network (DNS, PE, data endpoint) → tag existence (az acr repository show-tags).

**Azure Portal Steps:** ACR → **Networking**; **Access control (IAM)**; **Repositories**; AKS → **Workloads → pod → Events**.

**Root Cause:** Private DNS zone missing data endpoint record in the AKS VNet.

**Prevention:** Network change runbooks include DNS; pre-change test with check-acr.

**Interviewer Follow-Up Questions:**

- *"Image pull secrets?"* — Not needed with attach-acr; use only for external registries.

- *"Pull from ACR in another tenant?"* — Use a service principal pull secret or ACR connected registry; attach-acr works within the same tenant.

**Common Mistakes:** Re-enabling public access; using admin credentials.

**Key Points to Remember:** Error class → auth vs network vs tag · check-acr · PE + data endpoint DNS · admin off.

## E9. Deploying to AKS safely

**Question:** How do you deploy applications to AKS with zero downtime?

**Scenario:** Every deployment causes a few seconds of 502 errors.

**Interview Answer:**

"Short errors during rolling updates usually come from three things. Readiness: if the readiness probe isn't accurate, new pods receive traffic before they're ready. Shutdown: when a pod is terminated, the ingress may still send it traffic for a few seconds, so the app needs a preStop delay and must handle SIGTERM gracefully, finishing in-flight requests. Capacity: maxUnavailable must allow enough healthy pods during the rollout — I often use maxUnavailable 0 and maxSurge 25%.

I'd also add a PodDisruptionBudget so node upgrades don't take down too many pods, and spread pods across zones and nodes with topology spread constraints.

For bigger changes, I'd use canary or blue-green — for example with the Azure DevOps canary strategy, Flagger or Argo Rollouts — with automated analysis on error rate."

**YAML:**

**YAML**

spec:

replicas: 4

strategy:

type: RollingUpdate

rollingUpdate: { maxUnavailable: 0, maxSurge: 1 }

template:

spec:

terminationGracePeriodSeconds: 45

topologySpreadConstraints:

\- maxSkew: 1

topologyKey: topology.kubernetes.io/zone

whenUnsatisfiable: ScheduleAnyway

labelSelector: { matchLabels: { app: orders-api } }

containers:

\- name: api

lifecycle:

preStop:

exec: { command: \["sleep", "10"\] }

readinessProbe:

httpGet: { path: /health/ready, port: 8080 }

periodSeconds: 5

---

apiVersion: policy/v1

kind: PodDisruptionBudget

metadata: { name: orders-api-pdb }

spec:

minAvailable: 3

selector: { matchLabels: { app: orders-api } }

**Technical Deep Dive:** Endpoint removal and SIGTERM happen in parallel — hence preStop sleep. Readiness gates for App Gateway ingress.

**Step-by-Step:** Probes → graceful shutdown → rollout params → PDB → spread → test with load during deploy.

**Commands:**

**BASH**

kubectl rollout status deployment/orders-api -n orders --timeout=5m

kubectl rollout undo deployment/orders-api -n orders

**Root Cause:** No preStop and inaccurate readiness.

**Prevention:** Deployment templates with these defaults; deploy under synthetic load in test.

**Interviewer Follow-Up Questions:**

- *"Why sleep in preStop?"* — Gives kube-proxy/ingress time to remove the endpoint before the app stops.

- *"Node image upgrades?"* — Use maintenance windows, max surge on node pools, PDBs.

**Common Mistakes:** Liveness = readiness; no PDB.

**Key Points to Remember:** Readiness · preStop + graceful shutdown · maxUnavailable 0 · PDB · spread.

## E10. Rollback strategies

**Question:** What rollback strategies do you design into deployments?

**Scenario:** Leadership asks "how fast can we undo a bad release?"

**Interview Answer:**

"It depends on the platform, but the principle is the previous version must be ready and deployable instantly, and data changes must be backward-compatible.

App Service: slot swap — the previous version stays in the staging slot after swap, so swapping back takes about a minute. AKS: rollout undo or Helm rollback to the previous revision, or switch traffic back in blue-green. Functions: slots on Premium/Dedicated, or redeploy the previous package. Infrastructure: revert the Terraform commit and apply through the pipeline — but some changes, like deleting a resource, can't be simply reverted, so plans are reviewed carefully.

Feature flags are also a rollback tool — turn off the feature without deploying.

Our target answer to leadership might be: application rollback in under five minutes, tested regularly, because untested rollback is not a strategy."

**Technical Deep Dive:** Artifacts retained (pipeline retention policies); image tags in ACR retention; Helm --history-max; Azure App Configuration feature flags.

**Commands:**

**BASH**

az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --target-slot production

helm rollback orders-api 0 -n orders \# 0 = previous release

kubectl rollout undo deployment/orders-api -n orders

**Step-by-Step:** Define RTO for rollback → design per platform → retain artifacts → backward-compatible data → rehearse.

**ADO Steps:** **Environments** history → redeploy previous run ("Rerun stage" on an older run).

**Root Cause (slow rollbacks):** Artifacts deleted, schema incompatible, manual steps.

**Prevention:** Retention policies; expand/contract; rollback drills.

**Interviewer Follow-Up Questions:**

- *"Rollback after a destructive migration?"* — Restore from point-in-time backup — costly — which is why destructive changes come later and separately.

- *"Who decides?"* — Pre-agreed: incident commander with service owner.

**Common Mistakes:** Assuming "redeploy old commit" is quick when it rebuilds.

**Key Points to Remember:** Previous version ready · slots/Helm/undo · feature flags · data compatibility · rehearse.

## E11. Blue-green deployments

**Question:** How would you implement blue-green deployments on Azure?

**Scenario:** A payment API needs zero-downtime releases with instant rollback.

**Interview Answer:**

"Blue-green means two full environments: blue is live, green gets the new version. We test green with real dependencies, then switch all traffic, keeping blue ready for rollback.

On App Service, deployment slots are blue-green built in. Deploy to the staging slot, warm it up with application initialisation, run smoke tests against the slot URL, then swap. Slot-specific settings, like a feature flag for 'staging', stay with the slot.

On AKS, I'd run two deployments — orders-blue and orders-green — with the Service selector pointing to one colour, or use the ingress controller to switch. Switching the selector is instant; rollback is switching it back.

For whole-stack blue-green — for example an infrastructure upgrade — I'd use Front Door or Traffic Manager to shift between two stamps.

The database is shared, so schema changes must work with both versions."

**Technical Deep Dive:** Slot swap phases: apply target settings to source, warm up (restart), swap routing. Swap with preview (multi-phase) lets you validate before final swap. WEBSITE_SWAP_WARMUP_PING_PATH.

**Commands:**

**BASH**

az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --action preview

\# validate staging with production settings

az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --action swap

kubectl patch service orders -n orders -p '{"spec":{"selector":{"app":"orders","color":"green"}}}'

**Step-by-Step:** Deploy green → warm → test → switch → monitor → keep blue → decommission later.

**Azure Portal Steps:** App Service → **Deployment slots → Swap** (with preview).

**Root Cause (failed swaps):** Slot settings mismatch; warm-up failing.

**Prevention:** Settings in IaC with slotSetting flags; warm-up path.

**Interviewer Follow-Up Questions:**

- *"Cost?"* — Slots share the plan; AKS blue-green needs double pods temporarily.

- *"Long-running sessions?"* — Use external session state; drain connections.

**Common Mistakes:** Forgetting sticky slot settings; incompatible DB changes.

**Key Points to Remember:** Two environments · test then switch · instant rollback · slots · shared DB compatibility.

## E12. Canary deployments

**Question:** How do you implement canary releases with automated health checks?

**Scenario:** The team wants to release to 10% of users and auto-stop if errors rise.

**Interview Answer:**

"Canary sends a small share of traffic to the new version and increases it if metrics stay healthy.

Options on Azure: App Service traffic routing sends a percentage to a slot. On AKS, the Azure DevOps deployment job has a canary strategy with increments, and the Kubernetes manifest task can create the canary and baseline deployments; for finer weighted routing I'd use a service mesh — the Istio-based service mesh add-on for AKS — or Argo Rollouts/Flagger.

The essential part is automated analysis: compare the canary's error rate and latency with the baseline in Application Insights or Prometheus. In Azure DevOps, a 'Query Azure Monitor alerts' check or a gate step can stop promotion if alerts fire; Flagger or Argo do the analysis automatically and roll back.

I'd tag telemetry with the version so we can separate canary and stable metrics."

**YAML (Azure DevOps canary strategy):**

**YAML**

\- deployment: Canary

environment: orders-prod.orders \# environment.namespace resource

strategy:

canary:

increments: \[10, 50\]

deploy:

steps:

\- task: KubernetesManifest@1

inputs:

action: deploy

strategy: canary

percentage: \$(strategy.increment)

manifests: manifests/deployment.yaml

containers: \<acr\>.azurecr.io/orders-api:\$(tag)

postRouteTraffic:

steps:

\- script: ./check-error-rate.sh --max 1.0

on:

failure:

steps:

\- task: KubernetesManifest@1

inputs: { action: reject, strategy: canary, manifests: manifests/deployment.yaml }

success:

steps:

\- task: KubernetesManifest@1

inputs: { action: promote, strategy: canary, manifests: manifests/deployment.yaml, containers: \<acr\>.azurecr.io/orders-api:\$(tag) }

**BASH**

az webapp traffic-routing set -g \<rg\> -n \<app\> --distribution staging=10

az webapp traffic-routing clear -g \<rg\> -n \<app\>

**Technical Deep Dive:** Without a mesh, the KubernetesManifest canary uses replica ratios, so "percentage" is approximate. SMI/mesh gives precise weights.

**KQL (compare versions):**

**KQL**

AppRequests

\| where TimeGenerated \> ago(30m)

\| summarize FailPct = round(100.0 \* countif(Success == false) / count(), 2), P95 = percentile(DurationMs, 95) by AppVersion = tostring(Properties\["AppVersion"\])

**Step-by-Step:** Version tagging → canary deploy → analysis window → promote/reject → automate.

**Root Cause / Prevention:** Canary without analysis is just a slow rollout — automate checks.

**Interviewer Follow-Up Questions:**

- *"Canary vs feature flags?"* — Canary splits by traffic for infra/code; flags target users/features independently of deploy.

- *"Minimum traffic for valid analysis?"* — Need enough requests; use longer windows or synthetic load at low traffic times.

**Common Mistakes:** No version tagging; manual eyeballing.

**Key Points to Remember:** Small % → analyse → promote/reject · automated metrics · version tags.

## E13. CI/CD security (supply chain)

**Question:** How do you secure the CI/CD pipeline itself?

**Scenario:** After an industry supply-chain attack, the CTO asks how safe your pipelines are.

**Interview Answer:**

"I think of four areas.

Source: branch policies, required reviews, signed commits if required, secret scanning with push protection, and dependency scanning — GitHub Advanced Security for Azure DevOps covers secret, dependency and code scanning.

Pipeline: YAML only — no classic UI pipelines — with an extends required template that contains mandatory security steps; restricted pipeline permissions on service connections, variable groups and agent pools; protection of the YAML pipeline settings like 'limit job authorization scope'; and no secrets exposed to PR builds from forks.

Identity and agents: workload identity federation; least-privilege service connections per environment; ephemeral agents — Microsoft-hosted or Managed DevOps Pools — so a compromised build doesn't persist.

Artifacts: pinned and verified dependencies, image scanning, signing images and verifying signatures at deploy time, an SBOM, and deploying only from our ACR — enforced by Azure Policy on AKS.

Plus audit streaming of Azure DevOps logs to the SIEM."

**Technical Deep Dive:** Org/project settings: Limit job authorization scope to current project, protect access to repositories in YAML pipelines, disable creation of classic pipelines. Azure Policy for AKS: "Kubernetes cluster containers should only use allowed images". Notation + Ratify for signature verification.

**Step-by-Step:** Assess settings → enable scanning → required templates → lock down resources → ephemeral agents → artifact integrity → audit.

**ADO Steps:** **Organization settings → Pipelines → Settings**; **Repos → Advanced Security**; **Auditing → Streams**.

**YAML (Advanced Security tasks):**

**YAML**

\- task: AdvancedSecurity-Codeql-Init@1

inputs: { languages: csharp }

\- script: dotnet build

\- task: AdvancedSecurity-Dependency-Scanning@1

\- task: AdvancedSecurity-Codeql-Analyze@1

**Root Cause (risk):** Over-privileged connections and mutable dependencies.

**Prevention:** Settings baseline reviewed quarterly.

**Interviewer Follow-Up Questions:**

- *"Self-hosted agent risks?"* — Persistent state between jobs, credential exposure; use ephemeral agents.

- *"SBOM?"* — Generate with Microsoft SBOM tool or Syft; store with artifacts.

**Common Mistakes:** Focusing only on code scanning.

**Key Points to Remember:** Source · pipeline · identity/agents · artifacts · audit.

## E14. Azure Repos branching and PR strategy

**Question:** What branching strategy and repository policies would you recommend?

**Scenario:** Long-lived feature branches cause painful merges and late bugs.

**Interview Answer:**

"I recommend trunk-based development: short-lived feature branches off main, merged within a day or two through pull requests, with feature flags for incomplete work. Main is always deployable.

Branch policies on main: minimum two reviewers for production code, reset votes on new pushes, linked work items, comment resolution, build validation that runs tests and IaC plan, and status checks for security scans. Code owners auto-add the right reviewers by path — for example the platform team for Terraform folders.

Releases come from main via the pipeline; hotfixes go through main too and are fast because the pipeline is fast. If we need release branches for regulatory reasons, they're short-lived and cut from main.

Squash merge keeps history clean and each PR maps to one commit."

**Technical Deep Dive:** Branch policies, path filters, required reviewers by path, build validation with path filters, auto-complete, merge types restriction.

**Step-by-Step:** Agree strategy → branch policies → code owners → build validation → feature flags → training.

**ADO Steps:** **Repos → Branches → main → ⋮ → Branch policies**; **Automatically included reviewers** with path filter.

**CLI:**

**BASH**

az repos policy approver-count create --branch main --repository-id \<repo-id\> \\

--minimum-approver-count 2 --creator-vote-counts false --allow-downvotes false --reset-on-source-push true \\

--blocking true --enabled true

az repos policy build create --branch main --repository-id \<repo-id\> --build-definition-id \<id\> \\

--display-name "PR validation" --blocking true --enabled true --queue-on-source-update-only false --manual-queue-only false --valid-duration 720

**Root Cause (merge pain):** Long-lived branches.

**Prevention:** Trunk-based + flags; small PRs.

**Interviewer Follow-Up Questions:**

- *"GitFlow?"* — Heavier; fine for versioned products with release trains, slower for continuous delivery.

- *"Infra PRs?"* — Include Terraform plan output as PR comment.

**Common Mistakes:** Too many required reviewers slowing everything.

**Key Points to Remember:** Trunk-based · short branches · branch policies · code owners · flags.

## E15. Terraform in Azure DevOps pipelines

**Question:** How do you integrate Terraform into Azure DevOps safely?

**Scenario:** Engineers run Terraform from laptops against production.

**Interview Answer:**

"I'd move all applies into pipelines. On pull requests, the pipeline runs fmt check, validate, tflint, a security scan like Checkov, and terraform plan against the target environment, posting the plan summary on the PR so reviewers see exactly what will change.

After merge, a pipeline runs plan again, saves the plan file as an artifact, waits for approval on the production environment, then runs terraform apply on that exact saved plan — so what was approved is what's applied.

Authentication uses a service connection with workload identity federation; the Terraform azurerm provider and backend use OIDC through environment variables. State is in an Azure Storage backend with locking. Engineers get read-only access to production and can run plan locally against dev only."

**YAML:**

**YAML**

stages:

\- stage: Plan

jobs:

\- job: Plan

pool: { vmImage: ubuntu-latest }

steps:

\- task: AzureCLI@2

displayName: terraform plan

inputs:

azureSubscription: sc-platform-prod-wif

scriptType: bash

scriptLocation: inlineScript

addSpnToEnvironment: true

inlineScript: \|

export ARM_CLIENT_ID=\$servicePrincipalId

export ARM_TENANT_ID=\$tenantId

export ARM_OIDC_TOKEN=\$idToken

export ARM_USE_OIDC=true

export ARM_SUBSCRIPTION_ID=\$(az account show --query id -o tsv)

cd infra/prod

terraform init -input=false

terraform plan -input=false -out=tfplan

terraform show -no-color tfplan \> plan.txt

\- publish: infra/prod

artifact: tfplan

\- stage: Apply

dependsOn: Plan

jobs:

\- deployment: Apply

environment: platform-prod \# approval here

pool: { vmImage: ubuntu-latest }

strategy:

runOnce:

deploy:

steps:

\- task: AzureCLI@2

inputs:

azureSubscription: sc-platform-prod-wif

scriptType: bash

scriptLocation: inlineScript

addSpnToEnvironment: true

inlineScript: \|

export ARM_CLIENT_ID=\$servicePrincipalId ARM_TENANT_ID=\$tenantId ARM_OIDC_TOKEN=\$idToken ARM_USE_OIDC=true

export ARM_SUBSCRIPTION_ID=\$(az account show --query id -o tsv)

cd \$(Pipeline.Workspace)/tfplan

terraform init -input=false

terraform apply -input=false tfplan

> Note: the OIDC token from idToken has a short lifetime; for long applies, use the Terraform task from the Microsoft DevLabs/Azure extension that refreshes tokens, or keep applies small. Same Terraform version and provider lock file must be used in both stages.

**Technical Deep Dive:** .terraform.lock.hcl committed; plan file tied to same state/serial (apply fails if state changed — "Saved plan is stale"). Self-hosted/Managed DevOps Pools if state storage is private.

**Step-by-Step:** Remote state → service connection → PR plan → saved plan + approval → apply → remove laptop access.

**Root Cause (risk):** Laptop applies, no review, no audit.

**Prevention:** RBAC (read-only for humans); drift detection pipeline.

**Interviewer Follow-Up Questions:**

- *"Saved plan is stale error?"* — State changed since plan; re-plan and re-approve.

- *"Secrets in plan output?"* — Mark sensitive; restrict artifact access; don't post full plan publicly.

**Common Mistakes:** Applying without saved plan; different TF versions between stages.

**Key Points to Remember:** PR plan · saved plan + approval · apply exact plan · OIDC · no laptop applies.

# Section 2F — Terraform and Infrastructure as Code (10 Questions)

## F1. Remote backend in Azure Storage

**Question:** How do you configure and secure a Terraform remote backend on Azure?

**Scenario:** Terraform state files are on engineers' laptops and in a shared drive.

**Interview Answer:**

"I'd create a dedicated storage account for state in the management or platform subscription — created once by a bootstrap script, not by the Terraform it serves. Settings: Standard ZRS or GRS for durability, blob versioning and soft delete so we can recover old states, public access disabled with a private endpoint or tightly scoped firewall, shared key access disabled, and Entra ID authentication.

Each environment and component gets its own key — for example connectivity/prod.tfstate, payments/prod.tfstate — so blast radius is small. Access is RBAC: pipeline identities get Storage Blob Data Contributor on the container; most humans get nothing or read-only for prod.

The backend block uses use_azuread_auth = true and in pipelines use_oidc = true. Locking is automatic through blob leases."

**Terraform:**

**HCL**

terraform {

backend "azurerm" {

resource_group_name = "rg-tfstate"

storage_account_name = "sttfstate\<unique\>"

container_name = "tfstate"

key = "payments/prod.tfstate"

use_azuread_auth = true

}

}

**Bootstrap (CLI):**

**BASH**

az group create -n rg-tfstate -l uksouth

az storage account create -n sttfstate\<unique\> -g rg-tfstate -l uksouth --sku Standard_ZRS \\

--min-tls-version TLS1_2 --allow-blob-public-access false --allow-shared-key-access false

az storage account blob-service-properties update -n sttfstate\<unique\> -g rg-tfstate \\

--enable-versioning true --enable-delete-retention true --delete-retention-days 30

az storage container create -n tfstate --account-name sttfstate\<unique\> --auth-mode login

az role assignment create --assignee \<pipeline-identity-object-id\> --role "Storage Blob Data Contributor" \\

--scope \$(az storage account show -n sttfstate\<unique\> -g rg-tfstate --query id -o tsv)/blobServices/default/containers/tfstate

**Technical Deep Dive:** Partial backend configuration (-backend-config= files) lets one codebase target multiple environments. State may contain secrets in plaintext.

**Step-by-Step:** Bootstrap storage → RBAC → backend block → terraform init -migrate-state from local → verify → delete local copies.

**Azure Portal Steps:** Storage account → **Data protection** (versioning, soft delete); **Networking**; **Configuration** (shared key access).

**Root Cause (original risk):** Local state → conflicts, loss, secrets on laptops.

**Prevention:** Policy: no local backends in CI (lint check); RBAC.

**Interviewer Follow-Up Questions:**

- *"Migrate existing local state?"* — Add backend block, terraform init -migrate-state, confirm, verify with terraform plan = no changes.

- *"Use access keys?"* — Avoid; prefer Entra ID auth.

**Common Mistakes:** State storage managed by same Terraform; no versioning.

**Key Points to Remember:** Dedicated, locked-down storage · versioning + soft delete · Entra auth · split keys.

## F2. Two engineers run terraform apply simultaneously

**Question:** Two engineers run Terraform apply simultaneously. How do you prevent state corruption?

**Scenario:** Two people applied changes to the same state 30 seconds apart; one got a lock error, the other later saw unexpected changes.

**Interview Answer:**

"The azurerm backend prevents simultaneous writes with a blob lease lock. The second apply fails with 'Error acquiring the state lock' and shows who holds the lock. So the backend protects the state file itself.

But locking alone doesn't prevent logical conflicts — one person plans, another applies, then the first applies an old view. That's why I'd use process controls: no applies from laptops in shared environments; all applies through a pipeline that uses saved plan files — Terraform refuses to apply a stale plan if the state changed; the pipeline environment has an exclusive lock check so only one run per environment at a time; and smaller state files per component reduce contention.

If a lock is stuck after a crash, I confirm no run is active, then terraform force-unlock with the lock ID."

**Technical Deep Dive:** Lock metadata (ID, operation, who, when) stored in blob metadata. -lock-timeout=5m to wait instead of failing. Azure DevOps Exclusive lock check + lockBehavior: sequential or runLatest.

**Commands:**

**BASH**

terraform plan -lock-timeout=5m -out=tfplan

terraform force-unlock \<LOCK_ID\>

az storage blob show --account-name \<sa\> -c tfstate -n payments/prod.tfstate --auth-mode login \\

--query "properties.lease"

**YAML**

\# Pipeline-level: serialize runs per environment

lockBehavior: sequential

**Step-by-Step (stuck lock):** Read lock info → confirm process is gone (agent/job/terminal) → force-unlock → plan to check consistency.

**Root Cause:** Manual concurrent applies.

**Prevention:** Pipeline-only applies; exclusive lock check; RBAC on state.

**Interviewer Follow-Up Questions:**

- *"Can you break the lease in the portal?"* — Yes ("Break lease"), but force-unlock is cleaner and same caution applies.

- *"State corrupted anyway?"* — Restore previous blob version, then reconcile with plan/import.

**Common Mistakes:** Force-unlocking while another apply is running.

**Key Points to Remember:** Blob lease lock · saved plans · exclusive lock · pipeline-only · force-unlock carefully.

## F3. Manually deleted resource managed by Terraform

**Question:** Someone manually deletes an Azure resource managed by Terraform. What happens during the next terraform plan?

**Scenario:** A subnet NSG association and a storage account were deleted in the portal.

**Interview Answer:**

"During plan, Terraform refreshes each resource in state by reading it from Azure. For deleted ones, the provider returns 'not found', Terraform drops them from the refreshed state and plans to create them again — they show as '+ create'. Dependent resources might show updates.

Applying will recreate them, but with caveats: the storage account comes back empty — data isn't restored by Terraform — so I'd try storage account recovery first if it was recently deleted and the name is still available, then let Terraform reconcile. For Key Vault, a soft-deleted vault with the same name blocks creation until recovered or purged — the azurerm provider can recover soft-deleted vaults automatically if configured.

Then I'd find out who did it from the Activity Log and prevent it: RBAC so humans don't have write in prod, resource locks on critical resources, and a nightly drift detection pipeline."

**Technical Deep Dive:** terraform plan -refresh-only shows drift without proposing config changes. Provider features { key_vault { recover_soft_deleted_key_vaults = true } }.

**Commands:**

**BASH**

terraform plan -refresh-only

terraform plan -detailed-exitcode \# 2 = changes present

**KQL:**

**KQL**

AzureActivity

\| where TimeGenerated \> ago(7d) and OperationNameValue endswith "/DELETE" and ActivityStatusValue == "Success"

\| project TimeGenerated, Caller, OperationNameValue, \_ResourceId

**Step-by-Step:** Plan → identify deletes → recover data if needed → apply → investigate who → prevent.

**Azure Portal Steps:** Storage accounts → **Restore deleted account** (from the list view); **Key vaults → Manage deleted vaults**; **Activity log**.

**Root Cause:** Human portal change with write permissions.

**Prevention:** Locks, PIM, drift detection, prevent_destroy on critical resources (protects against Terraform destroying, not portal deletes).

**Interviewer Follow-Up Questions:**

- *"What if someone modified a setting instead?"* — Plan shows update to revert, unless ignore_changes is set.

- *"Does \`prevent_destroy\` stop portal deletes?"* — No; only Terraform operations. Use resource locks for that.

**Common Mistakes:** Assuming Terraform restores data.

**Key Points to Remember:** Refresh → "+ create" · data not restored · soft-delete conflicts · locks/RBAC/drift detection.

## F4. Terraform modules for multiple teams

**Question:** How do you design and version Terraform modules for many teams?

**Scenario:** Ten teams copy-paste Terraform with inconsistent security settings.

**Interview Answer:**

"I'd build a small set of opinionated platform modules with secure defaults — for example app-service, aks-cluster, key-vault, storage, sql — that include diagnostics, private endpoints, tags and RBAC by default, and expose only the inputs teams really need.

Modules live in their own repositories or a mono-repo with semantic version tags, published to a private registry — Terraform Cloud/Enterprise, or simply Git tags referenced with ?ref=v1.4.0. Teams pin versions and upgrade deliberately. Breaking changes mean a major version with upgrade notes.

Each module has examples, input validation, automated tests — terraform test or Terratest — and a changelog. Where possible I'd build on Azure Verified Modules rather than starting from zero.

Composition: teams write a thin root module per environment that calls these modules, with separate state per environment."

**Terraform:**

**HCL**

module "orders_app" {

source = "git::https://dev.azure.com/org/Platform/\_git/tf-module-appservice?ref=v2.1.0"

name = "app-orders-prod"

resource_group_name = azurerm_resource_group.orders.name

location = "uksouth"

sku_name = "P1v3"

zone_redundant = true

log_analytics_workspace_id = data.azurerm_log_analytics_workspace.central.id

tags = local.tags

}

**HCL**

\# inside module: variables.tf

variable "sku_name" {

type = string

validation {

condition = contains(\["P0v3", "P1v3", "P2v3", "P3v3"\], var.sku_name)

error_message = "Only Premium v3 SKUs are allowed."

}

}

**Technical Deep Dive:** terraform test (native from 1.6) with .tftest.hcl; module structure (main/variables/outputs/versions); moved blocks for refactors without destroy.

**Step-by-Step:** Identify common patterns → build modules with defaults → tests → versioning → registry → migrate teams → deprecate old.

**Root Cause (inconsistency):** No shared modules.

**Prevention:** Policy as safety net; modules as paved road.

**Interviewer Follow-Up Questions:**

- *"Monorepo vs repo per module?"* — Repo per module gives independent versions; monorepo is easier to maintain — tag per module path.

- *"Refactor without recreating resources?"* — moved blocks.

**Common Mistakes:** Giant "do everything" modules; unpinned sources.

**Key Points to Remember:** Opinionated secure defaults · versioned & pinned · tests · AVM · thin root modules.

## F5. Terraform plan and apply workflow

**Question:** Explain what happens in terraform init, plan and apply, and how you review a plan.

**Scenario:** A junior engineer approved a plan that destroyed and recreated a production database.

**Interview Answer:**

"init downloads providers and modules according to version constraints and the lock file, and configures the backend. plan refreshes state from real infrastructure, compares it with the configuration, and shows actions: create, update in place, destroy, or replace — destroy then create. apply executes those actions, ideally from a saved plan file.

In review, the most dangerous lines are 'must be replaced' and destroys. Replacement happens when an immutable property changes — for example a resource name, location or some SKU settings. Terraform marks which attribute 'forces replacement'.

To protect against this: reviewers check the plan summary — '1 to destroy' on a database is a red flag; the pipeline can fail automatically if destroys appear in production plans unless explicitly allowed; lifecycle { prevent_destroy = true } on critical data resources; and resource locks in Azure."

**Commands:**

**BASH**

terraform init -input=false

terraform plan -out=tfplan

terraform show -json tfplan \| jq '\[.resource_changes\[\] \| select(.change.actions \| index("delete"))\] \| length'

**YAML**

\- script: \|

deletes=\$(terraform show -json tfplan \| jq '\[.resource_changes\[\] \| select(.change.actions \| index("delete"))\] \| length')

if \[ "\$deletes" -gt 0 \]; then echo "##vso\[task.logissue type=error\]Plan contains \$deletes deletions"; exit 1; fi

displayName: Block destructive plans

**HCL**

resource "azurerm_mssql_database" "orders" {

\# ...

lifecycle { prevent_destroy = true }

}

**Technical Deep Dive:** Plan symbols: + create, ~ update, - destroy, -/+ replace (destroy first), +/- replace with create_before_destroy.

**Step-by-Step (review):** Summary counts → replaces/destroys → reason ("forces replacement") → expected? → approve.

**Root Cause (the incident):** A rename forced replacement; reviewer didn't read the plan.

**Prevention:** Destructive-change gate; prevent_destroy; reviewer training.

**Interviewer Follow-Up Questions:**

- *"How do you rename without replacement?"* — For Terraform address renames use moved; Azure resource names usually can't change without replacement.

- *"create_before_destroy?"* — Creates new first; requires unique names.

**Common Mistakes:** Approving long plans without reading summary.

**Key Points to Remember:** init/plan/apply · "forces replacement" · gate destroys · prevent_destroy · locks.

## F6. Terraform import

**Question:** How do you bring existing manually-created Azure resources under Terraform?

**Scenario:** A production VNet and 12 subnets were created in the portal two years ago.

**Interview Answer:**

"Since Terraform 1.5, I use import blocks — declarative and reviewable in a PR. I write import blocks with the resource address and the Azure resource ID, then run terraform plan -generate-config-out=generated.tf to have Terraform generate the configuration. I clean the generated code — remove computed and default values, use variables — and run plan until it shows only imports and no changes.

Then apply, which only records the resources in state. After that, I remove the import blocks or leave them — they're no-ops once imported.

Before starting, I'd also check Azure Export for Terraform (aztfexport), which can generate config and import for a whole resource group — a good starting point for big estates.

The goal is a plan with zero changes after import; any changes mean the code doesn't match reality yet."

**Terraform:**

**HCL**

import {

to = azurerm_virtual_network.hub

id = "/subscriptions/\<sub-id\>/resourceGroups/rg-network-prod/providers/Microsoft.Network/virtualNetworks/vnet-hub-prod"

}

import {

to = azurerm_subnet.app

id = "/subscriptions/\<sub-id\>/resourceGroups/rg-network-prod/providers/Microsoft.Network/virtualNetworks/vnet-hub-prod/subnets/snet-app"

}

**BASH**

terraform plan -generate-config-out=generated.tf

terraform plan \# target: "Plan: 2 to import, 0 to add, 0 to change, 0 to destroy."

terraform apply

\# Legacy CLI alternative:

terraform import azurerm_virtual_network.hub "/subscriptions/\<sub-id\>/resourceGroups/rg-network-prod/providers/Microsoft.Network/virtualNetworks/vnet-hub-prod"

\# Bulk option:

aztfexport resource-group rg-network-prod

**Technical Deep Dive:** IDs are case-sensitive in some providers; subnets inline vs separate resources (don't mix inline subnet blocks and azurerm_subnet).

**Step-by-Step:** Inventory → import blocks → generate config → refine → zero-diff plan → apply → PR.

**Root Cause:** Click-ops history.

**Prevention:** Policy/RBAC so new prod resources come only from IaC.

**Interviewer Follow-Up Questions:**

- *"Import gives diff on tags?"* — Align code with reality or decide intentionally to change.

- *"Import into a module?"* — to = module.network.azurerm_virtual_network.this.

**Common Mistakes:** Applying a plan that "fixes" differences in production unintentionally.

**Key Points to Remember:** Import blocks · generate-config-out · zero-diff · aztfexport.

## F7. Infrastructure drift detection

**Question:** How do you detect and handle drift between Terraform and Azure?

**Scenario:** Firewall rules were changed in the portal during an incident and never added to code.

**Interview Answer:**

"I'd run a scheduled drift pipeline — nightly for production — that runs terraform plan -detailed-exitcode for each state. Exit code 2 means differences; the pipeline posts the summary to Teams and creates a work item.

Then a decision for each drift: if the manual change was right — like an emergency firewall rule — we codify it in Terraform through a PR. If it was wrong, we apply Terraform to revert it.

Prevention: production write access through PIM only, incident runbooks that say 'emergency change → PR within 24 hours', and Azure Policy for configuration that must never change regardless of tool."

**YAML:**

**YAML**

schedules:

\- cron: "0 2 \* \* \*"

displayName: Nightly drift check

branches: { include: \[ main \] }

always: true

steps:

\- task: AzureCLI@2

inputs:

azureSubscription: sc-platform-prod-readonly-wif

scriptType: bash

scriptLocation: inlineScript

addSpnToEnvironment: true

inlineScript: \|

export ARM_CLIENT_ID=\$servicePrincipalId ARM_TENANT_ID=\$tenantId ARM_OIDC_TOKEN=\$idToken ARM_USE_OIDC=true

export ARM_SUBSCRIPTION_ID=\$(az account show --query id -o tsv)

terraform init -input=false

set +e

terraform plan -detailed-exitcode -lock=false -input=false -no-color \> plan.txt

code=\$?

set -e

if \[ \$code -eq 2 \]; then echo "##vso\[task.logissue type=warning\]Drift detected"; echo "##vso\[task.complete result=SucceededWithIssues;\]"; fi

if \[ \$code -eq 1 \]; then exit 1; fi

> A read-only identity can run plan if it has Reader on resources and data access to the state container; -lock=false avoids needing write access for locks (acceptable for read-only drift checks only).

**Technical Deep Dive:** Exit codes 0/1/2; -refresh-only to accept drift into state without changes in Azure.

**Step-by-Step:** Schedule → notify → triage → codify or revert → prevent.

**Root Cause:** Manual emergency changes.

**Prevention:** PIM; runbook rule; drift pipeline.

**Interviewer Follow-Up Questions:**

- *"Drift on fields Azure changes itself?"* — Use ignore_changes for those specific attributes (e.g., tags added by policy).

- *"Drift outside Terraform-managed resources?"* — Azure Policy/Resource Graph for unmanaged resources.

**Common Mistakes:** Blindly reverting emergency fixes.

**Key Points to Remember:** Scheduled plan -detailed-exitcode · codify or revert · PIM · ignore_changes sparingly.

## F8. Terraform authentication to Azure

**Question:** What are the options for authenticating Terraform to Azure and which do you prefer?

**Scenario:** Pipelines use a client secret stored in a variable group.

**Interview Answer:**

"The azurerm provider supports Azure CLI auth — good for local development; managed identity — for self-hosted agents in Azure; service principal with client secret or certificate; and OIDC — workload identity federation — for CI systems like Azure DevOps and GitHub Actions.

My preference: OIDC in pipelines, managed identity for agents running in Azure, and Azure CLI for local non-production work. No client secrets. The backend uses the same identity with use_azuread_auth.

With azurerm 4.x, subscription_id must be set explicitly — via the provider block or ARM_SUBSCRIPTION_ID. For multiple subscriptions, I use provider aliases."

**Terraform:**

**HCL**

provider "azurerm" {

features {}

subscription_id = var.subscription_id

use_oidc = true \# or use_msi = true on self-hosted agents in Azure

}

provider "azurerm" {

alias = "connectivity"

features {}

subscription_id = var.connectivity_subscription_id

use_oidc = true

}

resource "azurerm_virtual_network_peering" "spoke_to_hub" {

provider = azurerm.connectivity

\# ...

}

**Environment variables:** ARM_CLIENT_ID, ARM_TENANT_ID, ARM_SUBSCRIPTION_ID, ARM_USE_OIDC, ARM_OIDC_TOKEN (or ARM_OIDC_REQUEST_URL/TOKEN and for Azure DevOps ARM_ADO_PIPELINE_SERVICE_CONNECTION_ID with SYSTEM_ACCESSTOKEN).

**Technical Deep Dive:** Recent azurerm versions support Azure DevOps OIDC natively with the service connection ID and refresh tokens automatically, avoiding short token expiry.

**Step-by-Step:** Choose method per context → configure identity → RBAC → provider config → remove secrets.

**Root Cause (risk):** Long-lived secret.

**Prevention:** OIDC/MI standard.

**Interviewer Follow-Up Questions:**

- *"Token expired during long apply?"* — Use provider's ADO OIDC support that refreshes tokens, or split state.

- *"Different identity for backend vs provider?"* — Possible via backend config; usually same identity.

**Common Mistakes:** Secrets in tfvars.

**Key Points to Remember:** OIDC in CI · MSI on Azure agents · CLI locally · subscription_id explicit · aliases.

## F9. Troubleshooting Terraform errors

**Question:** Walk me through troubleshooting common Terraform errors on Azure.

**Scenario:** An apply fails with "A resource with the ID ... already exists - to be managed via Terraform this resource needs to be imported into the State."

**Interview Answer:**

"That error means the resource exists in Azure but not in this state — maybe created manually, by another state file, or a previous apply timed out after creating it. I'd check which: if it belongs to this configuration, import it; if another state manages it, remove the duplicate code and use a data source instead.

Other common errors I see: 'state lock' — check and force-unlock carefully. 'AuthorizationFailed' — identity lacks permission at that scope. 'RequestDisallowedByPolicy' — Azure Policy denied it; read which policy. 'Provider produced inconsistent result' — often an eventual consistency issue, re-run or upgrade provider. Timeouts — increase resource timeouts blocks for slow resources like App Gateway or SQL. 'Cycle' errors — dependency loops in config.

For deeper debugging I set TF_LOG=DEBUG to see the API calls and responses, and check the Activity Log for the failed operation's details."

**Commands:**

**BASH**

export TF_LOG=DEBUG TF_LOG_PATH=./tf-debug.log

terraform apply tfplan

terraform state list \| grep \<name\>

terraform state show azurerm_storage_account.logs

terraform state rm azurerm_storage_account.old \# stop managing without deleting

**HCL**

resource "azurerm_application_gateway" "agw" {

\# ...

timeouts { create = "90m", update = "90m" }

}

**Technical Deep Dive:** state rm removes from state only; removed block (1.7+) declarative alternative with lifecycle { destroy = false }.

**Step-by-Step:** Read error class → check Azure (Activity Log) → check state → fix (import/rm/permissions/policy) → re-plan.

**Root Cause (this case):** Previous apply timed out after Azure created the resource.

**Prevention:** Appropriate timeouts; one owner per resource.

**Interviewer Follow-Up Questions:**

- *"Debug logs contain secrets?"* — They can; handle carefully and delete.

- *"Moving a resource between states?"* — removed in one, import in the other.

**Common Mistakes:** Deleting the Azure resource to "fix" the error.

**Key Points to Remember:** Classify error · already exists → import/data source · TF_LOG · Activity Log · state commands carefully.

## F10. Bicep vs Terraform

**Question:** Bicep or Terraform — how do you choose, and how do you use Bicep well?

**Scenario:** The company is Azure-only today; a new platform team must pick a standard.

**Interview Answer:**

"Bicep is Azure's native language. It compiles to ARM JSON, supports new resource types and API versions immediately, and has no state file — Azure is the source of truth. what-if previews changes, and deployment stacks manage resource lifecycles, including deleting resources removed from the template and deny settings to prevent manual changes.

Terraform has a state file to manage, but supports many providers — Entra ID, Azure DevOps, GitHub, monitoring tools — and has a mature ecosystem and plan workflow.

For an Azure-only company with mostly Azure resources and a small team, Bicep is a very reasonable default. If they also manage Entra objects, DevOps projects or other clouds and SaaS in the same workflow, Terraform fits better. What matters most is one standard per resource set, modules, CI/CD with previews, and policy.

For Bicep I'd use modules from a Bicep registry in ACR or Azure Verified Modules, parameter files per environment (.bicepparam), what-if in PRs, and deployment stacks for lifecycle."

**Bicep:**

**BICEP**

param location string = resourceGroup().location

param appName string

@allowed(\[ 'P1v3', 'P2v3' \])

param sku string = 'P1v3'

resource plan 'Microsoft.Web/serverfarms@2023-12-01' = {

name: 'plan-\${appName}'

location: location

sku: { name: sku, capacity: 3 }

properties: { zoneRedundant: true, reserved: true }

kind: 'linux'

}

**BASH**

az deployment group what-if -g rg-orders-prod -f main.bicep -p prod.bicepparam

az stack group create --name orders-prod -g rg-orders-prod -f main.bicep -p prod.bicepparam \\

--action-on-unmanage deleteResources --deny-settings-mode denyWriteAndDelete

**Technical Deep Dive:** Deployment stacks: --action-on-unmanage (detachAll/deleteResources/deleteAll), deny settings, scopes (RG/subscription/MG). Bicep Terraform provider/extensibility (Microsoft Graph Bicep extension for Entra objects).

**Step-by-Step (choose):** Inventory what's managed → team skills → ecosystem needs → decide → standards.

**Root Cause / Prevention:** Mixing tools on same resources causes fights — define boundaries.

**Interviewer Follow-Up Questions:**

- *"Can Bicep manage Entra groups?"* — Yes via the Microsoft Graph Bicep extension; maturity is lower than Terraform's azuread provider.

- *"Is what-if fully reliable?"* — Generally good but can show noise for some properties; review carefully.

**Common Mistakes:** Religious answers; mixing on the same resource.

**Key Points to Remember:** Bicep = native, no state, what-if, stacks · Terraform = multi-provider, state, plan · choose by context.

# Section 2G — Azure Security and Governance (10 Questions)

## G1. Azure Policy for guardrails

**Question:** How do you use Azure Policy to enforce security and governance standards?

**Scenario:** Teams create public storage accounts and deploy to random regions.

**Interview Answer:**

"Azure Policy evaluates resource configurations at deployment time and continuously afterwards. I assign policies at management group level so every subscription inherits them, grouped into initiatives — security baseline, tagging, monitoring.

I choose effects deliberately: Deny for things that must never happen — storage public access, non-approved regions, public IPs in Corp landing zones. Audit to measure before enforcing. Modify to fix tags or settings automatically. DeployIfNotExists to add diagnostics, Defender settings or private DNS records.

Rollout: start with audit, review compliance, communicate with teams, then switch to Deny. Exemptions are time-limited with a reason. All definitions and assignments are code in Git, deployed by pipeline — Enterprise Policy as Code or Terraform."

**Technical Deep Dive:** Effects order: Disabled → Append/Modify → Deny → Audit → AuditIfNotExists/DINE. Enforcement mode DoNotEnforce for testing. Remediation tasks for DINE/Modify need managed identity with roles. Microsoft Cloud Security Benchmark is the default Defender initiative.

**Policy definition (custom example — deny public network access on Key Vault):**

**JSON**

{

"mode": "Indexed",

"policyRule": {

"if": {

"allOf": \[

{ "field": "type", "equals": "Microsoft.KeyVault/vaults" },

{ "field": "Microsoft.KeyVault/vaults/publicNetworkAccess", "notEquals": "Disabled" }

\]

},

"then": { "effect": "\[parameters('effect')\]" }

},

"parameters": {

"effect": { "type": "String", "allowedValues": \[ "Audit", "Deny", "Disabled" \], "defaultValue": "Audit" }

}

}

> A built-in policy "Azure Key Vault should disable public network access" already exists — prefer built-ins.

**Commands:**

**BASH**

az policy assignment create --name allowed-locations --scope /providers/Microsoft.Management/managementGroups/\<mg\> \\

--policy e56962a6-4747-49cd-b67b-bf8b01975c4c \\

--params '{"listOfAllowedLocations":{"value":\["uksouth","ukwest"\]}}'

az policy state summarize --management-group \<mg\>

**Step-by-Step:** Requirements → built-in search → initiative → audit assign → review → enforce → exemptions process.

**Azure Portal Steps:** **Policy → Definitions / Assignments / Compliance / Remediation / Exemptions**.

**Root Cause:** No preventive controls.

**Prevention:** Policy-as-code; compliance dashboards; Defender for Cloud secure score.

**Interviewer Follow-Up Questions:**

- *"Policy vs RBAC?"* — RBAC = who can act; Policy = what configuration is allowed.

- *"How fast does compliance update?"* — On create/update immediately for Deny; compliance scans every ~24 hours or on-demand (az policy state trigger-scan).

**Common Mistakes:** Deny everywhere on day one; custom policies where built-ins exist.

**Key Points to Remember:** MG scope · initiatives · audit → deny · DINE/Modify + remediation · exemptions · as code.

## G2. Microsoft Defender for Cloud

**Question:** How do you use Microsoft Defender for Cloud in an enterprise?

**Scenario:** Secure score is 42%; leadership wants a plan.

**Interview Answer:**

"Defender for Cloud has two parts: CSPM — posture management with recommendations and secure score — and workload protection plans for servers, containers, SQL, storage, Key Vault, App Service and more.

For posture, I'd enable Defender CSPM on production, then prioritise recommendations by risk — attack paths and internet exposure first — not just by count. I'd assign owners and due dates using governance rules, and fix systematically through IaC and policy so issues don't come back.

For protection, I'd enable Defender plans on production workloads: Servers for vulnerability assessment and EDR, Containers for image scanning and runtime, Storage for malware scanning, Key Vault and Resource Manager for suspicious operations. Alerts go to Sentinel or the SOC via continuous export.

I'd report secure score trend monthly — the goal is steady improvement and no new critical findings."

**Technical Deep Dive:** Foundational CSPM (free) vs Defender CSPM (attack path analysis, cloud security explorer, agentless scanning). Governance rules assign owners. Continuous export to Log Analytics/Event Hubs. Regulatory compliance dashboard.

**Step-by-Step:** Enable plans (policy at MG) → baseline score → prioritise by risk → owners/SLA → remediation via IaC/policy → track.

**Azure Portal Steps:** **Microsoft Defender for Cloud → Environment settings → (subscription) → Defender plans**; **Recommendations**; **Attack path analysis**; **Regulatory compliance**; **Workflow automation / Continuous export**.

**Commands:**

**BASH**

az security pricing create -n VirtualMachines --tier Standard --subplan P2

az security pricing create -n Containers --tier Standard

az security pricing list -o table

**KQL (alerts in workspace via continuous export):**

**KQL**

SecurityAlert

\| where TimeGenerated \> ago(7d)

\| summarize count() by AlertSeverity, AlertName

\| order by AlertSeverity asc

**Root Cause (low score):** No ownership, many default insecure configs.

**Prevention:** Policy + modules with secure defaults; governance rules.

**Interviewer Follow-Up Questions:**

- *"Cost of Defender?"* — Per resource/hour; enable based on risk, consider plans for prod first.

- *"False positives?"* — Suppression rules with justification.

**Common Mistakes:** Chasing score points rather than risk.

**Key Points to Remember:** CSPM + workload plans · risk-based prioritisation · governance owners · export alerts.

## G3. Network Security Groups

**Question:** How do you design and troubleshoot NSGs?

**Scenario:** After a security hardening change, an app subnet can't reach SQL.

**Interview Answer:**

"NSGs are stateful layer 4 filters on subnets or NICs, evaluated by priority, lowest number first, with default rules at the bottom — allow VNet-to-VNet, allow load balancer, deny all else inbound.

I design with service tags — like Sql.UKSouth, AzureLoadBalancer, AzureMonitor — and application security groups to group VMs by role instead of IPs. I apply NSGs at subnet level for consistency, and keep rules in IaC.

To troubleshoot this case: IP flow verify in Network Watcher tells me which rule allows or denies a specific flow. Effective security rules on the NIC show combined subnet and NIC rules. VNet flow logs with Traffic Analytics show denied flows over time. Most likely the hardening added a deny-all outbound rule with a higher priority than the SQL allow, or the new rules used the wrong service tag region."

**Commands:**

**BASH**

az network watcher test-ip-flow -g \<rg\> --vm \<vm\> --direction Outbound --protocol TCP \\

--local 10.1.2.4:50000 --remote \<sql-private-ip\>:1433

az network nic list-effective-nsg -g \<rg\> -n \<nic\> -o json

az network nsg rule create -g \<rg\> --nsg-name nsg-app -n allow-sql-out --priority 200 --direction Outbound \\

--access Allow --protocol Tcp --destination-address-prefixes Sql.UKSouth --destination-port-ranges 1433

**KQL (VNet flow logs with Traffic Analytics):**

**KQL**

NTANetAnalytics

\| where TimeGenerated \> ago(1h) and FlowStatus == "Denied"

\| summarize count() by SrcIp, DestIp, DestPort, AclRule

**Technical Deep Dive:** Subnet NSG and NIC NSG both evaluated (inbound: subnet then NIC; outbound: NIC then subnet). Augmented rules (multiple prefixes). Private endpoint NSG support requires enabling network policies on the subnet.

**Step-by-Step:** IP flow verify → effective rules → flow logs → fix rule → retest.

**Azure Portal Steps:** **Network Watcher → IP flow verify / NSG diagnostics**; NIC → **Effective security rules**; **Traffic Analytics**.

**Root Cause:** Deny-all outbound at priority 100 above specific allows.

**Prevention:** NSG changes via PR; tests in pipeline; NSG diagnostics before rollout.

**Interviewer Follow-Up Questions:**

- *"NSG vs Azure Firewall?"* — NSG = L4 distributed filtering; Firewall = centralised L3–L7 with FQDN, TLS inspection, threat intel.

- *"NSG on private endpoint?"* — Supported when subnet privateEndpointNetworkPolicies is enabled.

**Common Mistakes:** IP-based rules everywhere; NIC and subnet NSGs conflicting.

**Key Points to Remember:** Priority order · service tags/ASGs · IP flow verify · effective rules · flow logs.

## G4. Private Endpoints and DNS

**Question:** Private Endpoint connections fail with name resolution issues. How do you troubleshoot?

**Scenario:** On-premises users can't reach a storage account after public access was disabled; Azure VMs can.

**Interview Answer:**

"If Azure VMs work but on-premises fails, the private endpoint is fine — it's on-prem DNS. On-premises DNS resolves mystorage.blob.core.windows.net through the public internet, so it gets the public IP, which is now blocked.

The fix is conditional forwarding: on-prem DNS servers forward blob.core.windows.net — the public zone, not the privatelink zone — to an Azure DNS Private Resolver inbound endpoint in the hub, or to DNS forwarders in Azure. Those query Azure DNS, which follows the CNAME to privatelink.blob.core.windows.net and the linked private zone returns the private IP.

I'd test with nslookup from an on-prem machine before and after. In general I centralise privatelink zones in the hub, link them to the hub VNet where the resolver lives, and automate A record creation with the private endpoint's DNS zone group — or Azure Policy DINE at scale."

**Commands:**

**BASH**

nslookup mystorage.blob.core.windows.net \# expect 10.x from Azure/on-prem after fix

az network private-endpoint dns-zone-group create -g \<rg\> --endpoint-name pe-mystorage-blob \\

-n default --private-dns-zone privatelink.blob.core.windows.net --zone-name blob

az network private-dns record-set a list -g rg-dns -z privatelink.blob.core.windows.net -o table

az dns-resolver inbound-endpoint list -g rg-hub --dns-resolver-name dnsr-hub -o table

**Technical Deep Dive:** Do not create a private zone named blob.core.windows.net (would break all other storage accounts). Private DNS zone must be linked to the VNet that does the resolution (resolver VNet). Private Resolver: inbound (on-prem → Azure), outbound + forwarding ruleset (Azure → on-prem).

**Step-by-Step:** Where does it fail (Azure vs on-prem)? → nslookup result → zone record exists? → zone linked? → forwarding path → firewall to PE IP.

**Azure Portal Steps:** Private endpoint → **DNS configuration**; Private DNS zone → **Virtual network links**, **Recordsets**; **DNS private resolvers**.

**Root Cause:** On-prem conditional forwarder missing.

**Prevention:** DNS design documented; checklist for disabling public access; Policy for DNS zone groups.

**Interviewer Follow-Up Questions:**

- *"Multiple private endpoints for same resource in different VNets?"* — One zone record per name; centralise or you'll get conflicts.

- *"Why forward the public zone?"* — Clients query the public name; Azure DNS handles the CNAME to privatelink.

**Common Mistakes:** Forwarding privatelink.\* only; creating zones per spoke.

**Key Points to Remember:** nslookup first · privatelink zone linked · conditional forwarding to Private Resolver · central zones.

## G5. Managed identities as a security control

**Question:** How do managed identities improve security, and how do you roll them out across an estate?

**Scenario:** 300 connection strings and keys exist across app settings.

**Interview Answer:**

"Managed identities remove secrets: nothing to leak, rotate or expire. Access is RBAC — auditable, least-privilege, and revocable centrally.

Rollout plan: inventory secrets — scan app settings, Key Vault and repos; categorise by target service — Storage, SQL, Service Bus, Key Vault, Cosmos DB, Event Hubs all support Entra ID auth. Then per service: enable identity, assign a data-plane role, change the SDK client to DefaultAzureCredential, deploy, verify, and finally disable local/key authentication on the target — that's the step that actually closes the risk.

I'd do it service type by service type with a template so teams follow the same pattern, and enforce with policies like 'Storage accounts should prevent shared key access', 'Service Bus should have local authentication disabled' and 'Azure SQL should have Entra-only authentication'."

**Technical Deep Dive:** Azure SQL: create contained user CREATE USER \[app-name\] FROM EXTERNAL PROVIDER; then roles. Local auth disable flags: disableLocalAuth on Service Bus/Event Hubs/Cosmos DB/App Insights.

**SQL:**

**SQL**

CREATE USER \[app-orders-prod\] FROM EXTERNAL PROVIDER;

ALTER ROLE db_datareader ADD MEMBER \[app-orders-prod\];

ALTER ROLE db_datawriter ADD MEMBER \[app-orders-prod\];

**TEXT**

Connection string: Server=tcp:sql-orders.database.windows.net;Database=orders;Authentication=Active Directory Default;

**Commands:**

**BASH**

az servicebus namespace update -g \<rg\> -n \<ns\> --disable-local-auth true

az sql server ad-only-auth enable -g \<rg\> -n \<sql-server\>

**Step-by-Step:** Inventory → per-service pattern → migrate → disable local auth → policy enforce.

**Root Cause (secret sprawl):** Legacy patterns.

**Prevention:** Policies + templates.

**Interviewer Follow-Up Questions:**

- *"Local development?"* — DefaultAzureCredential uses developer's Azure CLI/VS login with dev RBAC.

- *"Performance?"* — Tokens cached by SDK; negligible overhead.

**Common Mistakes:** Enabling identity but never disabling keys.

**Key Points to Remember:** No secrets · data roles · DefaultAzureCredential · disable local auth · policy.

## G6. Key Vault security hardening

**Question:** How do you secure Azure Key Vault in production?

**Scenario:** An audit finds Key Vaults with public access, access policies granting 'all' to many users, and no logs.

**Interview Answer:**

"I'd harden five areas. Access model: switch to Azure RBAC, with least-privilege data roles — Secrets User for apps, Secrets Officer for the pipeline that writes secrets — and admin roles only through PIM. Network: disable public access and use private endpoints; if needed, allow trusted Microsoft services only. Data protection: soft delete is always on; enable purge protection so even an admin can't permanently delete during retention. Separation: one vault per application per environment, so blast radius is small. Monitoring: diagnostic logs to Log Analytics, alerts on unusual access or failed requests, and Defender for Key Vault.

Plus lifecycle: expiry dates on secrets, rotation, and alerts on near-expiry."

**Commands:**

**BASH**

az keyvault update -n \<kv\> -g \<rg\> --enable-rbac-authorization true --public-network-access Disabled \\

--enable-purge-protection true --bypass AzureServices

**KQL (who read secrets):**

**KQL**

AzureDiagnostics

\| where ResourceProvider == "MICROSOFT.KEYVAULT" and OperationName == "SecretGet" and TimeGenerated \> ago(1d)

\| summarize Reads = count() by identity_claim_appid_g, identity_claim_upn_s, CallerIPAddress

\| order by Reads desc

**Technical Deep Dive:** Purge protection cannot be disabled once enabled. Managed HSM for FIPS 140-3 Level 3 needs. Key Vault limits (transactions per 10 seconds).

**Step-by-Step:** Migrate access model (map policies → roles) → network → purge protection → logs → per-app vaults → rotation.

**Azure Portal Steps:** Key Vault → **Access configuration**, **Networking**, **Properties**, **Diagnostic settings**.

**Root Cause:** Default/legacy setup.

**Prevention:** Built-in policies for Key Vault (RBAC model, public network disabled, purge protection, expiry dates).

**Interviewer Follow-Up Questions:**

- *"Why one vault per app/env?"* — Least privilege boundaries and throttling isolation.

- *"Pipeline needs to write secrets?"* — Secrets Officer on that vault only.

**Common Mistakes:** Shared vault for everything.

**Key Points to Remember:** RBAC model · private · purge protection · per-app vault · logs/Defender · rotation.

## G7. Azure Firewall and hub-spoke security

**Question:** How do you use Azure Firewall in a hub-and-spoke network?

**Scenario:** Spokes have direct internet egress and can talk to each other freely.

**Interview Answer:**

"In a hub-and-spoke design, the hub VNet holds shared services: Azure Firewall, VPN or ExpressRoute gateways, Bastion and DNS resolver. Spokes peer with the hub. Route tables in the spokes send 0.0.0.0/0 and other spoke ranges to the firewall's private IP, so all egress and spoke-to-spoke traffic is inspected.

The firewall uses a Firewall Policy with rule collection groups — DNAT, network and application rules. Application rules allow outbound by FQDN — for example only \*.ubuntu.com and our package registries — and FQDN tags for Azure services. Premium SKU adds TLS inspection, IDPS and URL filtering. Threat intelligence mode set to Alert and Deny.

Logs go to Log Analytics with resource-specific tables, and I use the Firewall workbook to analyse. For PaaS traffic, private endpoints keep traffic on private IPs; I decide whether that traffic also goes through the firewall based on inspection needs. Azure Virtual WAN with secured hubs is the managed alternative at large scale."

**Terraform (excerpt):**

**HCL**

resource "azurerm_route_table" "spoke" {

name = "rt-spoke-orders"

location = var.location

resource_group_name = var.rg

bgp_route_propagation_enabled = false

route {

name = "default-to-firewall"

address_prefix = "0.0.0.0/0"

next_hop_type = "VirtualAppliance"

next_hop_in_ip_address = var.firewall_private_ip

}

}

resource "azurerm_firewall_policy_rule_collection_group" "app" {

name = "rcg-apps"

firewall_policy_id = azurerm_firewall_policy.hub.id

priority = 300

application_rule_collection {

name = "allow-package-repos"

priority = 100

action = "Allow"

rule {

name = "nuget-npm"

source_addresses = \["10.10.0.0/16"\]

destination_fqdns = \["api.nuget.org", "registry.npmjs.org"\]

protocols { type = "Https" port = 443 }

}

}

}

**KQL:**

**KQL**

AZFWApplicationRule

\| where TimeGenerated \> ago(1h) and Action == "Deny"

\| summarize count() by SourceIp, Fqdn

\| order by count\_ desc

**Technical Deep Dive:** Default outbound access for VMs is being retired (new VNets after Sept 2025 default to private subnets) — explicit egress (Firewall/NAT Gateway) needed. Forced tunnelling. DNS proxy on firewall for FQDN network rules.

**Step-by-Step:** Hub design → firewall + policy → UDRs → rules → logs → test egress.

**Azure Portal Steps:** **Firewall Manager**; Firewall → **Logs / Workbooks**; route tables → **Associate subnet**.

**Root Cause (original risk):** Uncontrolled egress, lateral movement.

**Prevention:** Policy: deny public IPs in spokes, require route tables.

**Interviewer Follow-Up Questions:**

- *"Asymmetric routing with firewall?"* — Ensure return paths also via firewall; avoid UDR gaps.

- *"Cost?"* — Firewall has fixed hourly + data processing; Basic SKU for small environments.

**Common Mistakes:** Forgetting AKS required egress FQDNs.

**Key Points to Remember:** Hub-spoke · UDR to firewall · policy rule collections · FQDN rules · logs.

## G8. Zero Trust on Azure

**Question:** How do you apply Zero Trust principles to an Azure environment?

**Scenario:** The security team's strategy says "Zero Trust"; they ask how it maps to Azure.

**Interview Answer:**

"Zero Trust has three principles: verify explicitly, use least privilege, and assume breach. On Azure:

Verify explicitly: Entra ID for every human and workload, MFA and Conditional Access — device compliance, location, risk — phishing-resistant MFA for admins, and workload identities with federation.

Least privilege: RBAC at the smallest scope, PIM just-in-time access, data-plane roles, no shared keys, network access only where needed.

Assume breach: segment the network — hub-spoke, NSGs, firewall, private endpoints, no public management ports — Bastion for VM access; encrypt everywhere; monitor everything — Defender for Cloud, Sentinel, central logs — and have tested incident response.

In practice I translate this into concrete policies and patterns in our landing zones, so teams get Zero Trust by default rather than having to design it each time."

**Technical Deep Dive:** Conditional Access policies (require MFA for Azure management; block legacy auth), authentication strengths, Entra ID Protection risk policies. Azure Bastion, JIT VM access (Defender for Servers).

**Step-by-Step:** Identity foundation → privileged access → network segmentation → data protection → monitoring → continuous review.

**Azure Portal Steps:** **Entra ID → Conditional Access**; **PIM**; **Defender for Cloud → Just-in-time VM access**; **Bastion**.

**Commands:**

**BASH**

az network bastion create -g rg-hub -n bas-hub --public-ip-address pip-bastion --vnet-name vnet-hub --sku Standard -l uksouth

**Root Cause (typical gaps):** RDP/SSH exposed, standing admin, flat networks.

**Prevention:** Landing zone defaults; policies (deny public IPs on NICs, management ports closed).

**Interviewer Follow-Up Questions:**

- *"Is Zero Trust just network?"* — No; identity is the main control plane.

- *"How do you measure progress?"* — Secure score, % MFA coverage, standing privileged accounts count, public endpoints count.

**Common Mistakes:** Buzzwords without concrete controls.

**Key Points to Remember:** Verify explicitly · least privilege · assume breach → concrete Azure controls.

## G9. Compliance requirements

**Question:** How do you demonstrate compliance (e.g., ISO 27001, SOC 2, PCI DSS) on Azure?

**Scenario:** An auditor will review the payments platform in six weeks.

**Interview Answer:**

"Azure handles the physical and platform layers under the shared responsibility model — Microsoft's audit reports are in the Service Trust Portal. Our responsibility is how we configure and operate it.

I'd assign the relevant regulatory initiative in Defender for Cloud — for example PCI DSS v4 or ISO 27001 — which maps controls to Azure Policy assessments, and track the regulatory compliance dashboard. Not every control is automatable, so I'd also gather manual evidence: access reviews, change management records from pipelines, incident reports, and DR test results.

Evidence I'd prepare: RBAC and PIM configuration, access review results, encryption settings, network diagrams and NSG/firewall rules, logging retention, vulnerability management reports, and pipeline approval history. Policy-as-code and IaC make this much easier because the configuration is versioned and reviewable."

**Technical Deep Dive:** Regulatory compliance in Defender for Cloud; Microsoft Purview Compliance Manager; Service Trust Portal; data residency (UK regions); retention requirements (PCI: 1 year logs, 3 months immediately available).

**Step-by-Step:** Scope → initiative → gaps → remediate → evidence pack → mock audit.

**Azure Portal Steps:** **Defender for Cloud → Regulatory compliance → Manage compliance policies**; **Policy → Compliance**.

**Commands:**

**BASH**

az policy state list --management-group \<mg\> --filter "complianceState eq 'NonCompliant'" \\

--query "\[\].{policy:policyDefinitionName, resource:resourceId}" -o table

**Root Cause (failed audits):** Evidence scattered; manual config.

**Prevention:** Continuous compliance rather than audit-time effort.

**Interviewer Follow-Up Questions:**

- *"Shared responsibility for PaaS vs IaaS?"* — More responsibility shifts to Microsoft with PaaS (OS patching), but identity, data and access are always ours.

- *"Data residency?"* — Allowed locations policy; check service-specific data storage (some global services).

**Common Mistakes:** Assuming Azure certification = our compliance.

**Key Points to Remember:** Shared responsibility · regulatory initiatives · manual evidence · as code.

## G10. Security incident response on Azure

**Question:** Defender alerts on a suspicious sign-in and mass secret reads from Key Vault. How do you respond?

**Scenario:** At 22:30 UK time, alert: "Unusual application accessed a key vault" plus 400 SecretGet operations from an unknown IP.

**Interview Answer:**

"I'd follow the incident process with the security team: triage, contain, investigate, eradicate, recover, learn.

Triage: confirm the alert — which identity, IPs, what was read. Contain: disable the identity or revoke sessions; if it's a service principal, remove credentials; restrict Key Vault network access immediately; and treat every secret read as compromised — rotate them, starting with the most sensitive.

Investigate with logs: Key Vault AuditEvent for exact secrets, Entra sign-in logs for where the identity authenticated from, Activity Log for other changes, and how the credential leaked.

Eradicate and recover: remove persistence, fix the leak, restore normal service with new secrets. Communicate to stakeholders and, if customer data is involved, involve legal for notification obligations.

Afterwards: blameless review and controls — private endpoints, managed identities instead of secrets, Conditional Access for workload identities, and alerting on unusual secret access."

**KQL:**

**KQL**

AzureDiagnostics

\| where ResourceProvider == "MICROSOFT.KEYVAULT" and TimeGenerated \> ago(1d)

\| where OperationName == "SecretGet"

\| summarize Count = count(), Secrets = make_set(id_s, 100) by CallerIPAddress, identity_claim_appid_g

\| order by Count desc

**Commands:**

**BASH**

az keyvault update -n \<kv\> -g \<rg\> --public-network-access Disabled

az ad sp update --id \<app-id\> --set accountEnabled=false

az keyvault secret set --vault-name \<kv\> -n \<secret-name\> --value "\<new-value-from-provider\>"

**Technical Deep Dive:** Defender for Key Vault alerts; Sentinel incidents; Entra Workload ID Premium (risk-based CA for workloads).

**Step-by-Step:** Triage → contain → rotate → investigate → eradicate → recover → review.

**Azure Portal Steps:** **Defender for Cloud → Security alerts**; Key Vault → **Logs**; **Entra ID → Sign-in logs → Service principal sign-ins**.

**Root Cause (example):** Client secret committed to a public repo.

**Prevention:** Secret scanning/push protection, managed identities, private Key Vault, CA for workload identities.

**Interviewer Follow-Up Questions:**

- *"Rotate first or investigate first?"* — Contain and rotate quickly in parallel; preserve logs (they're already in the workspace).

- *"Who do you notify?"* — Security lead/CISO, service owner, legal/DPO if personal data.

**Common Mistakes:** Only rotating the leaked credential and not the secrets it read.

**Key Points to Remember:** Contain → rotate all exposed → logs → persistence → fix leak → review.

# Section 2H — Leadership and Architecture (5 Questions)

> For these questions, interviewers want **your real examples**. Use the structures below, but fill them with your own experience. If you don't have a direct example, say so and explain how you would approach it.

## H1. Mentoring engineers

**Question:** How do you mentor junior and mid-level engineers on a cloud platform team?

**Scenario:** Two junior engineers join; they know basic Azure but not production operations.

**Interview Answer:**

"I start by understanding where they are and what they want to grow into, then give them real work with support, not just training.

Practically: a 30-60-90 plan — first, shadowing on-call and pairing on pull requests; then owning small production changes with me reviewing; then leading something like a module or a runbook. I review their PRs explaining the 'why', and I ask them to review mine too, because reviewing teaches a lot.

I make it safe to ask questions and to make mistakes in non-production. For incidents, I let them drive the investigation while I support, then we review together.

I also scale it: short knowledge-sharing sessions — for example 'KQL in 30 minutes' — and good documentation and templates, so learning isn't dependent on me. I measure success by them becoming independent: handling on-call, making design proposals."

**Technical Deep Dive:** Tools: pairing, PR reviews, game days, runbooks, ADRs, brown-bag sessions, certification paths (AZ-104 → AZ-400/AZ-305).

**Step-by-Step:** Assess → plan → pair → own with review → lead → independent.

**Root Cause (failed mentoring):** Too much theory, no ownership, no feedback.

**Prevention:** Regular 1:1s and clear goals.

**Interviewer Follow-Up Questions:**

- *"A mentee keeps making the same mistake?"* — Private conversation, find why (knowledge vs process), add a guardrail or checklist.

- *"How do you balance mentoring with delivery?"* — Pairing on real work delivers and teaches at the same time.

**Common Mistakes:** Claiming you "trained 20 people" without specifics; doing the work for them.

**Key Points to Remember:** Real work + support · explain why · safe to fail · scale with docs/sessions · measure independence.

## H2. Architecture decision-making

**Question:** How do you make and communicate architecture decisions?

**Scenario:** Two teams disagree: AKS vs Azure Container Apps for new microservices.

**Interview Answer:**

"I make decisions explicit and evidence-based. First, define the requirements and constraints: scale, team skills, operational overhead, networking needs, cost, timeline. Then list options with trade-offs — for this case, AKS gives full Kubernetes control and ecosystem but more operational work; Container Apps is serverless containers with KEDA and Dapr built in, less control but much less to manage.

If the trade-off isn't clear, I run a short time-boxed proof of concept against the key criteria. Then I write an Architecture Decision Record: context, options, decision, consequences. I share it for review with both teams and stakeholders, and once decided, we commit — and we can revisit if the context changes.

Using the Azure Well-Architected Framework pillars — reliability, security, cost, operational excellence, performance — as the evaluation lens keeps the discussion objective rather than about preferences."

**ADR template:**

**TEXT**

\# ADR-012: Container hosting for new microservices

Status: Accepted (2026-11-05)

Context: 8 new stateless services, team of 5 with limited Kubernetes experience, need VNet integration...

Options: (1) AKS (2) Azure Container Apps (3) App Service for Containers

Decision: Azure Container Apps (workload profiles, VNet-integrated environment)

Consequences: + less ops, KEDA scaling; - limited custom controllers; revisit if we need service mesh features

**Step-by-Step:** Requirements → options → evaluation (WAF) → PoC if needed → ADR → review → decide → revisit trigger.

**Root Cause (bad decisions):** Opinion-based, undocumented.

**Prevention:** ADR practice; architecture review forum.

**Interviewer Follow-Up Questions:**

- *"What if leadership overrides you?"* — Make the risks explicit in writing, agree mitigations, then support the decision.

- *"How do you avoid analysis paralysis?"* — Time-box; most decisions are reversible — treat them as such.

**Common Mistakes:** "I always choose X."

**Key Points to Remember:** Requirements → trade-offs → PoC → ADR → commit → revisit.

## H3. Incident management leadership

**Question:** Describe how you run incident management and post-incident reviews.

**Scenario (illustrative):** A Sev 1 outage lasted 70 minutes; three teams were involved and communication was chaotic.

**Interview Answer:**

"During the incident: clear roles — incident commander, communications lead, subject-matter experts; one bridge and one incident channel; a running timeline; and the priority is mitigation, not root cause. Stakeholder updates on a fixed cadence.

After the incident: a blameless post-incident review within a few working days. We build the timeline from logs and chat, identify contributing factors — usually several, technical and process — and agree actions with owners and due dates. Good actions improve detection, mitigation speed or prevention: a missing alert, a rollback that took too long, a risky manual step.

I track the actions to completion, because a review without follow-through is just a meeting. And I look for patterns across incidents — for example, if most incidents follow config changes, we invest in config validation."

**Technical Deep Dive:** Severity definitions; metrics: MTTD, MTTA, MTTR; incident tooling integration with Azure Monitor action groups.

**Review template:**

**TEXT**

Summary · Impact (users, duration, SLO budget used) · Timeline (UTC/UK time) · Detection (how/when)

Contributing factors · What went well · What was hard · Actions (owner, due date, type: detect/mitigate/prevent)

**Step-by-Step:** Declare → roles → mitigate → communicate → resolve → review → track actions → trend analysis.

**Root Cause (chaos):** No roles, no cadence.

**Prevention:** Documented process; practice through game days.

**Interviewer Follow-Up Questions:**

- *"Someone caused the outage by mistake?"* — Focus on why the system allowed it; blame discourages honesty.

- *"How do you measure improvement?"* — MTTD/MTTR trend, repeat incidents, action completion rate.

**Common Mistakes:** Root-cause hunting during the outage; blame.

**Key Points to Remember:** Roles · mitigate first · cadence · blameless review · tracked actions · patterns.

## H4. Communicating with leadership

**Question:** How do you explain technical risks or proposals to non-technical leadership?

**Scenario:** You need budget to add a secondary region for DR (+\$8k/month).

**Interview Answer:**

"I translate technical points into business impact, options and a recommendation.

For the DR proposal: today, if UK South has a major outage, our recovery time could be over a day — and our order platform generates a known revenue per hour, so a 24-hour outage costs much more than a year of DR spend. I'd present three options: backup-only, cheapest, about 24 hours to recover; warm standby, plus about \$8k a month, about one hour; active-active, roughly double cost, minutes. Then my recommendation — warm standby — matches the business's stated RTO, with the main risks and next steps.

I keep it to one page, use numbers they care about — cost, revenue risk, customer impact — avoid jargon, and I'm honest about uncertainty. Then let them decide; it's a business risk decision."

**Structure:** Situation → Impact (business terms) → Options (cost/benefit/risk) → Recommendation → Ask/decision needed.

**Step-by-Step:** Know the audience → quantify → options → recommend → one page → follow up.

**Root Cause (proposals rejected):** Too technical, no business framing.

**Prevention:** Pre-brief key stakeholders.

**Interviewer Follow-Up Questions:**

- *"They say no?"* — Document the accepted risk, propose a cheaper interim mitigation, revisit next planning cycle.

- *"How do you report status?"* — Short, regular, RAG status with risks and decisions needed.

**Common Mistakes:** Jargon; only one option; exaggerating.

**Key Points to Remember:** Impact in business terms · options · recommendation · one page · they decide.

## H5. Prioritising reliability, security and cost

**Question:** How do you prioritise when reliability, security and cost conflict?

**Scenario:** The team has capacity for one quarter's initiative: zone redundancy (reliability), private endpoints everywhere (security), or a 25% cost reduction programme.

**Interview Answer:**

"I make the trade-offs explicit with risk and value, rather than defaulting to one pillar.

First, any non-negotiables: legal, regulatory or critical security exposures come first — for example, internet-exposed data with sensitive information. Then I score options by risk reduced and value: likelihood and impact of the risk each addresses, business value, effort, and dependencies.

For this example, I'd look at the data: how often have we had zone-related incidents, how exposed are our PaaS services today, and how much of the cost saving is quick wins. Often there's a blend — quick cost wins like rightsizing and log ingestion fund the reliability work, and the security work is prioritised for the most sensitive services first.

I'd bring the analysis to stakeholders with a recommendation, because these are business trade-offs, and document the decision and accepted risks. The Well-Architected Framework helps frame it: each pillar has trade-offs, and the goal is the right balance for this workload's requirements."

**Technical Deep Dive:** WAF pillars and trade-offs; risk register (likelihood × impact); SLOs as the reliability budget.

**Example scoring table:**

| **Initiative**                      | **Risk reduced**     | **Business value** | **Effort** | **Priority** |
|-------------------------------------|----------------------|--------------------|------------|--------------|
| Private endpoints for payments data | High (data exposure) | Compliance         | Medium     | 1            |
| Quick cost wins (rightsizing, logs) | Low                  | \$5k/month         | Low        | 2            |
| Zone redundancy for checkout        | Medium               | Availability SLO   | Medium     | 3            |
| Full private endpoints elsewhere    | Medium               | Defence in depth   | High       | Next quarter |

**Step-by-Step:** Non-negotiables → score → blend → stakeholder decision → document → revisit.

**Root Cause (bad prioritisation):** Loudest voice wins.

**Prevention:** Transparent scoring; risk register.

**Interviewer Follow-Up Questions:**

- *"Security team insists everything is critical?"* — Ask for risk rating with evidence; agree a common scale.

- *"How do you say no?"* — "Not now, here's why, and here's when" — with data.

**Common Mistakes:** "Security always wins" or "cost always wins" absolutism.

**Key Points to Remember:** Non-negotiables first · risk × value × effort · blend · stakeholders decide · document.

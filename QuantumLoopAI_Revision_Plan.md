# Top 30 Questions & Last-Minute Revision Plan

Read this first — highest-priority preparation for tomorrow

Senior Azure Cloud / DevOps Engineer — Interview Preparation Pack

All incidents and scenarios in this document are **illustrative examples** for interview practice. They are not claims about your personal work history. When you use them in the interview, frame them as "In a situation like this, I would…" or adapt them honestly to your own experience.

## Table of Contents

- [How to Use This Document Tonight](#how-to-use-this-document-tonight)
  - [The Answer Structure That Works for Every Question](#the-answer-structure-that-works-for-every-question)
- [Part A — Top 30 Most Likely Questions](#part-a-top-30-most-likely-questions)
  - [Q1 ★ TOP 10 — An engineer has Contributor access but cannot assign roles to another user. Why, and how do you resolve it?](#q1-top-10-an-engineer-has-contributor-access-but-cannot-assign-roles-to-another-user-why-and-how-do-you-resolve-it)
- [Check what roles a user has at a scope](#check-what-roles-a-user-has-at-a-scope)
- [Confirm Contributor's NotActions](#confirm-contributors-notactions)
  - [Q2 ★ TOP 10 — How would you design an Azure RBAC model that enforces least privilege across multiple teams and environments?](#q2-top-10-how-would-you-design-an-azure-rbac-model-that-enforces-least-privilege-across-multiple-teams-and-environments)
  - [Q3 ★ TOP 10 — An application on Azure App Service suddenly starts returning HTTP 500 errors. How do you investigate?](#q3-top-10-an-application-on-azure-app-service-suddenly-starts-returning-http-500-errors-how-do-you-investigate)
  - [Q4 ★ TOP 10 — How would you implement centralised logging and telemetry for 100+ Azure resources across multiple subscriptions?](#q4-top-10-how-would-you-implement-centralised-logging-and-telemetry-for-100-azure-resources-across-multiple-subscriptions)
  - [Q5 ★ TOP 10 — How do you configure proactive alerting, and how do you reduce alert noise?](#q5-top-10-how-do-you-configure-proactive-alerting-and-how-do-you-reduce-alert-noise)
  - [Q6 ★ TOP 10 — The Azure monthly bill suddenly increases from \$20,000 to \$35,000. How do you investigate and reduce it?](#q6-top-10-the-azure-monthly-bill-suddenly-increases-from-20000-to-35000-how-do-you-investigate-and-reduce-it)
- [Find unattached managed disks](#find-unattached-managed-disks)
- [Find deallocated vs running VMs](#find-deallocated-vs-running-vms)
  - [Q7 ★ TOP 10 — Walk me through a multi-stage YAML pipeline you would build for deploying to dev, test and production.](#q7-top-10-walk-me-through-a-multi-stage-yaml-pipeline-you-would-build-for-deploying-to-dev-test-and-production)
  - [Q8 ★ TOP 10 — A production deployment fails halfway through. How do you recover without impacting customers?](#q8-top-10-a-production-deployment-fails-halfway-through-how-do-you-recover-without-impacting-customers)
- [AKS rollback](#aks-rollback)
- [Helm rollback](#helm-rollback)
- [App Service: swap back](#app-service-swap-back)
  - [Q9 ★ TOP 10 — How do you manage Terraform state in a team, and how do you prevent two engineers corrupting it?](#q9-top-10-how-do-you-manage-terraform-state-in-a-team-and-how-do-you-prevent-two-engineers-corrupting-it)
  - [Q10 ★ TOP 10 — The application works with 1,000 users but becomes slow at 20,000 concurrent users. How do you investigate and scale it?](#q10-top-10-the-application-works-with-1000-users-but-becomes-slow-at-20000-concurrent-users-how-do-you-investigate-and-scale-it)
  - [Q11 — A production service principal credential has expired and the deployment pipeline is failing. What do you do?](#q11-a-production-service-principal-credential-has-expired-and-the-deployment-pipeline-is-failing-what-do-you-do)
- [Check credential expiry for an app registration](#check-credential-expiry-for-an-app-registration)
- [Create a new secret (short-term fix), output once — store securely](#create-a-new-secret-short-term-fix-output-once-store-securely)
  - [Q12 — What is the difference between a managed identity and a service principal, and when do you use each?](#q12-what-is-the-difference-between-a-managed-identity-and-a-service-principal-and-when-do-you-use-each)
  - [Q13 — How would you build a custom monitoring dashboard for a production service?](#q13-how-would-you-build-a-custom-monitoring-dashboard-for-a-production-service)
  - [Q14 — CPU utilisation is consistently above 90% on a production VM. How do you find the root cause?](#q14-cpu-utilisation-is-consistently-above-90-on-a-production-vm-how-do-you-find-the-root-cause)
- [Run a command inside a Linux VM without SSH](#run-a-command-inside-a-linux-vm-without-ssh)
  - [Q15 — Application Insights stopped receiving telemetry after a deployment. How do you troubleshoot?](#q15-application-insights-stopped-receiving-telemetry-after-a-deployment-how-do-you-troubleshoot)
  - [Q16 — Explain the difference between metrics, logs and traces, and how you use them together.](#q16-explain-the-difference-between-metrics-logs-and-traces-and-how-you-use-them-together)
  - [Q17 — An AKS application is experiencing pod restarts / CrashLoopBackOff and intermittent latency. How do you troubleshoot?](#q17-an-aks-application-is-experiencing-pod-restarts-crashloopbackoff-and-intermittent-latency-how-do-you-troubleshoot)
  - [Q18 — How do you manage secrets in CI/CD pipelines and applications securely?](#q18-how-do-you-manage-secrets-in-cicd-pipelines-and-applications-securely)
  - [Q19 — Explain blue-green and canary deployments and how you'd implement them on Azure.](#q19-explain-blue-green-and-canary-deployments-and-how-youd-implement-them-on-azure)
  - [Q20 — Someone manually deletes an Azure resource managed by Terraform. What happens during the next terraform plan?](#q20-someone-manually-deletes-an-azure-resource-managed-by-terraform-what-happens-during-the-next-terraform-plan)
- [Nightly drift detection: exit code 0 = no changes, 1 = error, 2 = changes (drift)](#nightly-drift-detection-exit-code-0-no-changes-1-error-2-changes-drift)
- [Bring an existing resource under management (Terraform 1.5+)](#bring-an-existing-resource-under-management-terraform-15)
  - [Q21 — Terraform vs Bicep: which would you choose and why?](#q21-terraform-vs-bicep-which-would-you-choose-and-why)
  - [Q22 — How do you design for high availability and disaster recovery on Azure?](#q22-how-do-you-design-for-high-availability-and-disaster-recovery-on-azure)
  - [Q23 — Azure Front Door vs Application Gateway vs Load Balancer vs Traffic Manager — when do you use each?](#q23-azure-front-door-vs-application-gateway-vs-load-balancer-vs-traffic-manager-when-do-you-use-each)
  - [Q24 — How do you use Azure Policy to enforce governance and security guardrails?](#q24-how-do-you-use-azure-policy-to-enforce-governance-and-security-guardrails)
  - [Q25 — Explain Private Endpoints and the DNS issues that commonly break them.](#q25-explain-private-endpoints-and-the-dns-issues-that-commonly-break-them)
- [Expected (from inside VNet):](#expected-from-inside-vnet)
- [kv-payments-prod.vault.azure.net canonical name = kv-payments-prod.privatelink.vaultcore.azure.net](#kv-payments-prodvaultazurenet-canonical-name-kv-payments-prodprivatelinkvaultcoreazurenet)
- [Address: 10.20.4.5](#address-102045)
  - [Q26 — How do you reduce Log Analytics ingestion costs without losing important visibility?](#q26-how-do-you-reduce-log-analytics-ingestion-costs-without-losing-important-visibility)
  - [Q27 — Reserved Instances vs Savings Plans — when would you use each?](#q27-reserved-instances-vs-savings-plans-when-would-you-use-each)
  - [Q28 — How do you build a Docker image in CI and push it securely to Azure Container Registry, and pull it from AKS?](#q28-how-do-you-build-a-docker-image-in-ci-and-push-it-securely-to-azure-container-registry-and-pull-it-from-aks)
  - [Q29 — As a senior engineer, how do you establish best practices and mentor other engineers?](#q29-as-a-senior-engineer-how-do-you-establish-best-practices-and-mentor-other-engineers)
  - [Q30 — How do you communicate a major production incident to leadership?](#q30-how-do-you-communicate-a-major-production-incident-to-leadership)
- [Part B — Last-Minute Revision Plan (3–4 Hours)](#part-b-last-minute-revision-plan-34-hours)
  - [Hour-by-Hour Plan](#hour-by-hour-plan)
  - [Study First — Highest-Value Topics](#study-first-highest-value-topics)
  - [Most Important Production Scenarios to Rehearse](#most-important-production-scenarios-to-rehearse)
  - [Essential Commands to Remember](#essential-commands-to-remember)
- [Context](#context)
- [RBAC](#rbac)
- [Monitoring](#monitoring)
- [App Service](#app-service)
- [AKS](#aks)
- [Terraform](#terraform)
  - [Five KQL Queries to Write from Memory](#five-kql-queries-to-write-from-memory)
  - [Critical Azure Concepts — One-Line Definitions](#critical-azure-concepts-one-line-definitions)
  - [Common Interviewer Traps](#common-interviewer-traps)
  - [Prepare Your Own Three Stories (STAR)](#prepare-your-own-three-stories-star)
  - [30-Minute Final Revision Checklist (Before the Interview)](#30-minute-final-revision-checklist-before-the-interview)
- [Part C — Interview Communication in Simple Professional English](#part-c-interview-communication-in-simple-professional-english)
  - [Principles](#principles)
  - [How to Start a Troubleshooting Answer](#how-to-start-a-troubleshooting-answer)
  - [How to Structure an Incident Response Answer](#how-to-structure-an-incident-response-answer)
  - [How to Explain a Production Deployment](#how-to-explain-a-production-deployment)
  - [How to Explain Azure Cost Optimisation](#how-to-explain-azure-cost-optimisation)
  - [How to Discuss Security and RBAC](#how-to-discuss-security-and-rbac)
  - [How to Answer When You Don't Know Something](#how-to-answer-when-you-dont-know-something)
  - [Communicating with UK-Based Engineering Teams](#communicating-with-uk-based-engineering-teams)
  - [Phrases to Avoid](#phrases-to-avoid)

# How to Use This Document Tonight

You have limited time. Use this document in this order:

**1.** Read **Part B — Last-Minute Revision Plan** first (10 minutes). It tells you exactly how to spend the next 3–4 hours.

**2.** Study the **10 highest-priority questions** (marked **★ TOP 10**) until you can speak each answer aloud without reading.

**3.** Skim the remaining 20 questions — focus on the three technical points for each.

**4.** Read **Part C — Interview Communication** just before you sleep and again one hour before the interview.

> **How to practise:** Read the spoken answer once, close the document, and say it out loud in your own words. Do not memorise word-for-word. Interviewers can hear a memorised script. They want structure and real reasoning.

**Time note for UK business hours:** UK is on GMT (UTC+0) from late October to late March, so a 09:00–17:30 UK day is 14:30–23:00 IST. From late March to late October (BST, UTC+1) it is 13:30–22:00 IST. Be ready to say you are comfortable working these overlap hours and joining on-call or incident bridges when needed.

## The Answer Structure That Works for Every Question

Use this five-step pattern. It makes you sound senior even when the question is unfamiliar.

| **Step**        | **What you say**                    | **Example phrase**                                                                                                    |
|-----------------|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| 1\. Clarify     | Restate the problem and assumptions | "So the app is on App Service, errors started after a deployment — I'll assume we have Application Insights enabled." |
| 2\. Stabilise   | Protect customers first             | "First I'd limit impact — check if a slot swap back or scale-out restores service."                                   |
| 3\. Investigate | Data-driven, top-down               | "Then I'd look at the signals: metrics first, then logs, then traces."                                                |
| 4\. Fix         | Root cause, not symptom             | "Once confirmed, the permanent fix is…"                                                                               |
| 5\. Prevent     | Monitoring, automation, process     | "To stop it happening again I'd add an alert, a pipeline gate and a runbook."                                         |

# Part A — Top 30 Most Likely Questions

These 30 questions are selected directly from the job description responsibilities: RBAC, monitoring and observability, scalability, cost governance, DevOps automation (Azure DevOps, Docker, Kubernetes, Terraform, Bicep), security and technical leadership.

| **\#** | **Question topic**                             | **Area**     | **Priority** |
|--------|------------------------------------------------|--------------|--------------|
| 1      | Contributor cannot assign roles                | RBAC         | ★ TOP 10     |
| 2      | Design an RBAC model with least privilege      | RBAC         | ★ TOP 10     |
| 3      | App Service returning HTTP 500 errors          | Monitoring   | ★ TOP 10     |
| 4      | Centralised logging and monitoring design      | Monitoring   | ★ TOP 10     |
| 5      | Proactive alerting and reducing alert noise    | Monitoring   | ★ TOP 10     |
| 6      | Azure bill jumps from \$20k to \$35k           | Cost         | ★ TOP 10     |
| 7      | Multi-stage YAML pipeline with approvals       | Azure DevOps | ★ TOP 10     |
| 8      | Production deployment fails halfway            | Azure DevOps | ★ TOP 10     |
| 9      | Terraform state, remote backend and locking    | Terraform    | ★ TOP 10     |
| 10     | App slow at 20,000 users — scale it            | Scalability  | ★ TOP 10     |
| 11     | Expired service principal breaks pipeline      | Identity     | Critical     |
| 12     | Managed identity vs service principal          | Identity     | Critical     |
| 13     | Building a custom monitoring dashboard         | Monitoring   | Critical     |
| 14     | VM CPU consistently above 90%                  | Monitoring   | Critical     |
| 15     | Application Insights telemetry missing         | Monitoring   | Critical     |
| 16     | Metrics vs logs vs traces                      | Monitoring   | High         |
| 17     | AKS pods restarting / CrashLoopBackOff         | Kubernetes   | Critical     |
| 18     | Secrets management in pipelines                | Security     | Critical     |
| 19     | Blue-green and canary deployments              | Azure DevOps | High         |
| 20     | Resource deleted manually — Terraform drift    | Terraform    | High         |
| 21     | Terraform vs Bicep                             | IaC          | High         |
| 22     | High availability and disaster recovery        | Architecture | High         |
| 23     | Front Door vs App Gateway vs Load Balancer     | Networking   | High         |
| 24     | Azure Policy and governance guardrails         | Governance   | High         |
| 25     | Private Endpoints and DNS                      | Security     | High         |
| 26     | Reducing Log Analytics ingestion cost          | Cost         | High         |
| 27     | Reserved Instances vs Savings Plans            | Cost         | Medium       |
| 28     | Docker image build and push to ACR in CI       | DevOps       | High         |
| 29     | Mentoring engineers and setting best practices | Leadership   | Critical     |
| 30     | Communicating a major incident to leadership   | Leadership   | High         |

## Q1 ★ TOP 10 — An engineer has Contributor access but cannot assign roles to another user. Why, and how do you resolve it?

**Spoken answer (60–90 seconds):**

"This is expected behaviour. The built-in Contributor role can manage all resources, but it explicitly excludes role assignment. In the role definition, Microsoft.Authorization/\*/Write is in the NotActions, so Contributor cannot create or delete role assignments.

To assign roles, a person needs Microsoft.Authorization/roleAssignments/write. That comes from Owner, User Access Administrator, or the newer Role Based Access Control Administrator role. My preferred option is Role Based Access Control Administrator with a condition, because I can restrict which roles they can assign — for example, only Reader and Storage Blob Data Reader — so they cannot give someone Owner.

I would first confirm the engineer's effective access at the right scope using Access control (IAM) → Check access, then confirm the business need. If it is a one-off, I would do the assignment myself. If it is a regular need, I would grant the constrained role through PIM as an eligible assignment with approval and a time limit. That keeps least privilege and gives us an audit trail."

**Three important technical points:**

- Contributor = full resource management **minus** access management (Microsoft.Authorization/\*/Write and /Delete are NotActions). It also cannot manage Azure Blueprints assignments or share image galleries.

- Role assignment requires Microsoft.Authorization/roleAssignments/write — Owner, User Access Administrator, or Role Based Access Control Administrator (supports **conditions** to limit which roles and principals can be assigned).

- RBAC is inherited downward: management group → subscription → resource group → resource. Check the scope where the assignment is attempted.

**Practical production example:** A team lead with Contributor on the rg-payments-prod resource group needs to give a new developer read access. Instead of making the team lead Owner, you grant them Role Based Access Control Administrator on that resource group with a condition allowing only Reader and Log Analytics Reader. They can self-serve safely.

```bash
# Check what roles a user has at a scope

az role assignment list --assignee <user-upn-or-objectid> --scope /subscriptions/<sub-id>/resourceGroups/<rg> -o table

# Confirm Contributor's NotActions

az role definition list --name "Contributor" --query "[].permissions[].notActions"
```

**Possible follow-up questions:**

- *"Why not just make them Owner?"* — Owner grants full access including the ability to assign Owner to others. That breaks least privilege and creates privilege-escalation risk. A constrained role is safer and auditable.

- *"The user now has the right role but still gets an error. What else?"* — Role assignment propagation can take a few minutes; the user should sign out and sign in again to refresh the token. Also check for a **deny assignment** (for example from a deployment stack or managed application), and check that the assignment was made at the correct scope.

## Q2 ★ TOP 10 — How would you design an Azure RBAC model that enforces least privilege across multiple teams and environments?

**Spoken answer:**

"I start with the hierarchy. I use management groups to separate platform, production and non-production landing zones, with one subscription per environment or per workload where possible. Subscriptions are a strong security and billing boundary.

Then I never assign roles to individual users. I create Microsoft Entra ID security groups per team and per function — for example grp-payments-prod-readers and grp-payments-prod-operators — and assign roles to those groups at the lowest sensible scope, usually the resource group.

In production, engineers get Reader by default. Elevated roles like Contributor are **eligible** through Privileged Identity Management, with approval, MFA and a time limit such as four hours. Deployments to production happen only through pipelines using a workload identity, not by people clicking in the portal.

For data planes, I use specific roles like Key Vault Secrets User or Storage Blob Data Reader rather than broad management roles. Finally, I run quarterly access reviews and alert on any new Owner assignment using Activity Log alerts."

**Three important technical points:**

- Assign to **groups**, at the **lowest scope**, using **built-in roles first**; create custom roles only when built-in roles are too broad.

- **PIM** (requires Microsoft Entra ID P2 or Entra ID Governance) gives just-in-time, time-bound, approval-based elevation with audit logs. **Access reviews** remove stale access.

- **Control plane vs data plane:** Contributor on a storage account does not automatically mean the user should read blobs with Entra ID auth — data access uses roles like Storage Blob Data Reader.

**Practical production example:**

| **Persona**       | **Non-prod**                | **Production**                                                    |
|-------------------|-----------------------------|-------------------------------------------------------------------|
| Developers        | Contributor on team RG      | Reader (eligible Contributor via PIM, 4h, approval)               |
| Platform/SRE      | Contributor on subscription | Reader + eligible Contributor; eligible User Access Administrator |
| Pipeline identity | Contributor on target RG    | Contributor on target RG only (no Owner)                          |
| Security team     | Security Reader             | Security Reader + Security Admin (eligible)                       |
| Finance           | Cost Management Reader      | Cost Management Reader                                            |

**Possible follow-up questions:**

- *"When would you create a custom role?"* — When a built-in role is too broad. Example: an operator who can restart VMs and read metrics but cannot delete them — Actions: Microsoft.Compute/virtualMachines/start/action, restart/action, read. I keep custom roles in Terraform or Bicep so they are version-controlled.

- *"How do you detect excessive permissions?"* — Microsoft Entra access reviews, Defender for Cloud recommendations (for example "subscriptions should have a maximum of 3 owners"), Activity Log alerts on role assignment writes, and periodic exports of az role assignment list --all.

## Q3 ★ TOP 10 — An application on Azure App Service suddenly starts returning HTTP 500 errors. How do you investigate?

**Spoken answer:**

"First I check impact and timing — is it all requests or some, and did it start after a deployment or configuration change? If it lines up with a release and we use deployment slots, the fastest mitigation is to swap back to the previous version. Customers first, root cause second.

Then I investigate top-down. In Application Insights, I open the Failures blade to see which operations fail and the exception types. I use Live Metrics to see if it is still happening right now. Then I drill into an end-to-end transaction to see if the 500 comes from our code or from a dependency like SQL, Key Vault or another API.

On the App Service side, I use 'Diagnose and solve problems' — it shows HTTP errors, platform events and memory or CPU pressure. I check application logs and the Activity Log for recent changes, such as an app setting or connection string change.

Common causes are a bad deployment, a missing app setting, a failing dependency, an expired secret, or the app running out of memory. Once fixed, I add an alert on failed request rate and add a health check endpoint so unhealthy instances are removed automatically."

**Three important technical points:**

- 500 = application or dependency failure; 502/503 = often platform, startup, or front-end/gateway issues. Distinguish them early.

- Application Insights: **Failures** blade, **end-to-end transaction details**, **Live Metrics**, dependency failures. Correlate by operation_Id.

- App Service: **Diagnose and solve problems**, **Log stream**, **Deployment slots**, **Health check**, **Activity Log** for configuration changes, Kudu (SCM) for process and file inspection.

**KQL (workspace-based Application Insights tables):**

```kusto
// Failed requests by operation and result code in the last hour

AppRequests

| where TimeGenerated > ago(1h) and Success == false

| summarize Failures = count() by OperationName, ResultCode, bin(TimeGenerated, 5m)

| order by TimeGenerated desc

// Exceptions linked to those failures

AppExceptions

| where TimeGenerated > ago(1h)

| summarize count() by ProblemId, ExceptionType, OuterMessage

| top 10 by count_
```

> In the Application Insights **Logs** blade the classic names also work: requests, exceptions, dependencies (columns timestamp, success, resultCode). In the Log Analytics workspace use AppRequests, AppExceptions, AppDependencies.

**Practical production example:** After a release, a new feature reads a secret from Key Vault using a Key Vault reference in app settings. The app's managed identity was never given the **Key Vault Secrets User** role in production, so the reference fails and every request to that feature returns 500. Mitigation: swap slots back. Fix: add the role assignment in Terraform. Prevention: a smoke test in the pipeline after deployment to the staging slot, before swap.

**Possible follow-up questions:**

- *"How do you know if it is the app or the platform?"* — Check Azure Service Health and Resource Health for platform events; check if errors are across all instances or one (use the instance filter in metrics). One bad instance suggests local issues; all instances suggest code or dependency.

- *"Errors are only on one instance."* — Use the Health check feature so App Service removes the unhealthy instance, or restart that specific instance via Diagnose and solve problems → Advanced Application Restart.

## Q4 ★ TOP 10 — How would you implement centralised logging and telemetry for 100+ Azure resources across multiple subscriptions?

**Spoken answer:**

"I would design a central observability platform owned by the platform team. Usually one Log Analytics workspace per environment in a dedicated management subscription — for example, one for production and one for non-production — unless data residency or access requirements force more.

To make sure every resource sends logs without relying on people, I use Azure Policy with DeployIfNotExists to apply diagnostic settings automatically. Azure has built-in policy initiatives for this. For VMs, I deploy the Azure Monitor Agent through policy and use Data Collection Rules to define which performance counters and logs to collect.

Applications use workspace-based Application Insights, linked to the same workspace, so we can join application and infrastructure data in one KQL query.

For access, I use resource-context permissions so teams only see logs for resources they have access to. On top of that, I build Workbooks and dashboards per service and set up alerts with action groups. I also control cost by choosing the right table plans and filtering noisy data with DCR transformations."

**Three important technical points:**

- **Diagnostic settings** route platform logs and metrics to Log Analytics, Storage (archive) or Event Hubs (SIEM/third party). Enforce with **Azure Policy DeployIfNotExists** at management group scope.

- **Azure Monitor Agent (AMA) + Data Collection Rules (DCRs)** replace the legacy Log Analytics agent (MMA), which was retired in August 2024. DCRs also support **ingestion-time transformations** to filter or trim data.

- **Workspace-based Application Insights** (classic Application Insights was retired in February 2024) stores telemetry in the Log Analytics workspace. Use **connection strings**, not instrumentation keys.

**Practical production example:** A company has 6 subscriptions and teams configure diagnostics manually, so half the resources send nothing. You assign the built-in "Enable allLogs category group resource logging for supported resources to Log Analytics" policy initiative at the production management group, run a remediation task for existing resources, and new resources are covered automatically.

**Possible follow-up questions:**

- *"One workspace or many?"* — Fewer workspaces make querying and correlation easier. Split only for data sovereignty, very different retention or access needs, or billing separation. Resource-context RBAC solves most access problems without extra workspaces.

- *"How do you send logs to a SIEM?"* — Microsoft Sentinel can run on the same workspace. For third-party SIEMs, use diagnostic settings to Event Hubs or Log Analytics data export rules.

## Q5 ★ TOP 10 — How do you configure proactive alerting, and how do you reduce alert noise?

**Spoken answer:**

"Proactive alerting means we know about a problem before customers report it. I build alerts around symptoms that affect users — error rate, latency, availability — plus a smaller number of cause-based alerts like disk full or certificate expiry.

I use three types: metric alerts for near-real-time thresholds such as CPU or HTTP 5xx; log search alerts for KQL-based conditions like 'more than 5% failed requests in 10 minutes'; and Activity Log alerts for Service Health and security events like role assignments. Application Insights availability tests check the site from multiple regions.

All alerts go to action groups, with different groups by severity — Sev 0 and 1 page the on-call engineer, Sev 3 goes to a Teams channel or creates a ticket.

To reduce noise, I use dynamic thresholds instead of fixed numbers where the pattern varies by time of day, require the condition to persist for several evaluation periods, use alert processing rules to suppress alerts during maintenance windows, and review alert data every month. Any alert that fires but needs no action gets tuned or deleted. Every alert should have a clear owner and a runbook link."

**Three important technical points:**

- Alert types: **metric**, **log search**, **Activity Log** (including **Service Health** and **Resource Health**), **smart detection**, **availability tests**. Severity levels Sev 0–4.

- **Action groups** define who and how (email, SMS, push, voice, webhook, Logic App, Azure Function, ITSM, Automation runbook). **Alert processing rules** add or suppress action groups at scale (maintenance windows).

- Noise reduction: **dynamic thresholds**, evaluation frequency and look-back window, "number of violations", stateful alerts that auto-resolve, and alerting on **SLO burn rate** rather than single spikes.

```kusto
// Log search alert: failure rate above 5% over 10 minutes

AppRequests

| where TimeGenerated > ago(10m)

| summarize Total = count(), Failed = countif(Success == false)

| extend FailureRate = todouble(Failed) / Total * 100

| where Total > 50 and FailureRate > 5
```

**Practical production example:** The on-call team receives 300 CPU alerts a week from a batch VM that runs at 95% every night by design. You change it to a dynamic threshold alert, add an alert processing rule to suppress it during the batch window, and replace it with a user-facing alert on API p95 latency. Pages drop by 80% and nobody ignores alerts any more.

**Possible follow-up questions:**

- *"Metric alert vs log alert — when?"* — Metric alerts are near real-time and cheaper; use them for numeric platform metrics. Log alerts allow complex KQL logic and joins but have more latency and cost per rule.

- *"How do you make alerts actionable?"* — Each alert has a severity, owner, description with a runbook link, and includes useful dimensions (resource, instance, operation) in the payload.

## Q6 ★ TOP 10 — The Azure monthly bill suddenly increases from \$20,000 to \$35,000. How do you investigate and reduce it?

**Spoken answer:**

"First I find where the increase came from before I change anything. In Cost Management → Cost analysis, I compare this month with last month and group by service, then by subscription, resource group and resource. I also use the daily view to find the exact day the cost started rising — that usually points to a deployment or change.

Typical causes are: a new environment left running, autoscale scaling out and not scaling back, a large VM or premium SKU chosen by mistake, a big rise in Log Analytics ingestion from debug logging, data egress, or reserved instances that expired and moved back to pay-as-you-go.

Once I know the cause, I fix it with the owner — rightsize, delete, scale down, or turn off verbose logging. Then I prevent it from happening again: budgets with alerts at 80%, 100% and forecasted 110%, cost anomaly alerts, mandatory tags like owner, environment and cost-centre enforced by Azure Policy, and a weekly cost review with Azure Advisor recommendations. I also check commitment discounts — reservations or savings plans for stable workloads."

**Three important technical points:**

- **Cost analysis**: group by Service name, Resource, Meter; use daily granularity and compare periods. Check **Reservations utilisation** for expired or unused commitments.

- **Prevention**: Budgets (actual and forecast alerts), **anomaly alerts**, tag policies (Require a tag / Inherit a tag from the resource group), Azure Advisor cost recommendations.

- Common hidden costs: Log Analytics ingestion, unattached managed disks, unused public IPs, idle App Service plans, premium storage snapshots, cross-region egress, NAT Gateway/Firewall data processing.

```bash
# Find unattached managed disks

az disk list --query "[?diskState=='Unattached'].{Name:name, RG:resourceGroup, SizeGB:diskSizeGb, Sku:sku.name}" -o table

# Find deallocated vs running VMs

az vm list -d --query "[].{Name:name, RG:resourceGroup, Size:hardwareProfile.vmSize, State:powerState}" -o table
```

```kusto
// Which tables are driving Log Analytics ingestion (GB) in the last 30 days

Usage

| where TimeGenerated > ago(30d) and IsBillable == true

| summarize IngestedGB = sum(Quantity) / 1000 by DataType

| order by IngestedGB desc
```

**Practical production example:** Cost analysis shows Log Analytics up \$9,000. The ContainerLogV2 table grew tenfold after a team enabled debug logging in AKS. You revert the log level, move that table to the Basic plan where appropriate, add a DCR transformation to drop health-probe logs, and set a workspace ingestion alert.

**Possible follow-up questions:**

- *"How do you make teams accountable?"* — Tags and showback reports by cost-centre, budgets per resource group with alerts to the team, and a monthly FinOps review.

- *"What would you not cut?"* — Anything that weakens reliability or security without discussion: backups, zone redundancy for critical services, security logs. Cost decisions are trade-offs I agree with the service owner.

## Q7 ★ TOP 10 — Walk me through a multi-stage YAML pipeline you would build for deploying to dev, test and production.

**Spoken answer:**

"I keep the pipeline in the same repository as the code, defined in YAML so it is version-controlled and reviewed through pull requests. It has a build stage and then one deployment stage per environment.

The build stage runs on every PR and main-branch commit: restore, build, unit tests, code quality, dependency and container scanning, and then it publishes a versioned artifact or pushes a Docker image to Azure Container Registry. The key principle is build once, deploy many — the same artifact goes to every environment.

Each deployment stage uses a deployment job targeting an Azure DevOps Environment. Production has approvals and checks configured on the environment — for example a manual approval from the service owner, a business-hours check, and a branch control check so only main can deploy.

Authentication uses an Azure Resource Manager service connection with workload identity federation, so there are no secrets to rotate. Variables come from variable groups linked to Key Vault. After deployment, I run smoke tests, and for App Service I deploy to a staging slot and swap only after tests pass."

**Three important technical points:**

- **Stages → jobs → steps.** Use deployment jobs with environment: to get approvals, checks, and deployment history.

- **Approvals and checks** are configured on the Environment (or service connection) in the Azure DevOps UI — not in YAML. Checks include approvals, branch control, business hours, required template, Azure Monitor alerts, and invoke Azure Function/REST API.

- **Templates** (template: and extends:) standardise pipelines across teams; extends with a required-template check enforces security steps.

```yaml
trigger:

branches:

include: [ main ]

variables:

\- group: app-common # variable group (can be linked to Key Vault)

\- name: imageTag

value: $(Build.BuildId)

stages:

\- stage: Build

jobs:

\- job: BuildAndTest

pool: { vmImage: ubuntu-latest }

steps:

\- script: dotnet test --configuration Release

displayName: Unit tests

\- task: Docker@2

displayName: Build and push image

inputs:

containerRegistry: sc-acr-prod # Docker registry service connection

repository: payments-api

command: buildAndPush

Dockerfile: src/Dockerfile

tags: $(imageTag)

\- stage: DeployTest

dependsOn: Build

jobs:

\- deployment: DeployToTest

environment: payments-test

pool: { vmImage: ubuntu-latest }

strategy:

runOnce:

deploy:

steps:

\- task: AzureWebAppContainer@1

inputs:

azureSubscription: sc-azure-test # workload identity federation

appName: app-payments-test

containers: <acr-name>.azurecr.io/payments-api:$(imageTag)

\- stage: DeployProd

dependsOn: DeployTest

condition: and(succeeded(), eq(variables['Build.SourceBranch'], 'refs/heads/main'))

jobs:

\- deployment: DeployToProd

environment: payments-prod # approvals & checks configured here

pool: { vmImage: ubuntu-latest }

strategy:

runOnce:

deploy:

steps:

\- task: AzureWebAppContainer@1

inputs:

azureSubscription: sc-azure-prod

appName: app-payments-prod

slotName: staging

containers: <acr-name>.azurecr.io/payments-api:$(imageTag)

\- script: curl --fail https://app-payments-prod-staging.azurewebsites.net/health

displayName: Smoke test staging slot

\- task: AzureAppServiceManage@0

inputs:

azureSubscription: sc-azure-prod

Action: Swap Slots

WebAppName: app-payments-prod

ResourceGroupName: rg-payments-prod

SourceSlot: staging
```

**Practical production example:** Different teams copied pipelines and some skipped security scans. You create a central template repository with an extends template that always runs secret scanning and image scanning, and add a "Required template" check on the production environment so pipelines that don't extend it cannot deploy.

**Possible follow-up questions:**

- *"Why workload identity federation?"* — It uses OpenID Connect tokens issued per pipeline run. No client secret is stored, so nothing expires or leaks. It is now the recommended option for Azure Resource Manager service connections.

- *"Where do approvals live?"* — On the Environment's Approvals and checks in Azure DevOps, so they can't be bypassed by editing the YAML.

## Q8 ★ TOP 10 — A production deployment fails halfway through. How do you recover without impacting customers?

**Spoken answer:**

"The first question is: are customers affected right now? I check health endpoints, error rates in Application Insights and availability tests. If customers are affected, I roll back immediately — I don't debug in production while users are failing.

How I roll back depends on the deployment strategy. With App Service slots, I swap back — the previous version is still warm in the staging slot. On AKS, I use kubectl rollout undo or redeploy the previous Helm release, or switch traffic back in a blue-green setup. If the failure involved infrastructure changes through Terraform, I re-apply the last known good commit rather than making manual changes.

Database changes are the hardest part. That's why I design migrations to be backward-compatible — expand and contract — so the old application version can still work with the new schema.

Then I communicate: post in the incident channel, update stakeholders, and after recovery do a blameless post-incident review. The long-term answer is to make deployments safer — slot swaps or canaries, automated smoke tests, health-based gates and smaller, more frequent releases."

**Three important technical points:**

- Design for rollback **before** deploying: immutable versioned artifacts, slot swap, blue-green or canary, Helm release history.

- **Database migrations**: expand/contract pattern, backward-compatible changes, never drop columns in the same release that stops using them.

- **Pipeline idempotency**: re-running a failed deployment should be safe; Terraform and Bicep are declarative and converge to desired state.

```bash
# AKS rollback

kubectl rollout history deployment/payments-api -n payments

kubectl rollout undo deployment/payments-api -n payments # previous revision

kubectl rollout undo deployment/payments-api -n payments --to-revision=12

kubectl rollout status deployment/payments-api -n payments

# Helm rollback

helm history payments-api -n payments

helm rollback payments-api 12 -n payments

# App Service: swap back

az webapp deployment slot swap -g rg-payments-prod -n app-payments-prod --slot staging --target-slot production
```

**Practical production example:** A rolling update on AKS gets halfway: 3 of 6 pods run the new version and they fail readiness probes because a new environment variable is missing. Because readiness probes failed, the new pods never received traffic and maxUnavailable kept old pods running — customers saw no errors. You run kubectl rollout undo, add the missing ConfigMap value through the pipeline, and redeploy.

**Possible follow-up questions:**

- *"Roll forward or roll back?"* — Roll back by default when customers are impacted. Roll forward only if the fix is small, well understood and faster than rollback, or rollback is impossible (for example a non-reversible data migration).

- *"How do you avoid half-deployed states?"* — Readiness probes, maxUnavailable: 0, deployment slots, and automated post-deployment health checks that fail the stage.

## Q9 ★ TOP 10 — How do you manage Terraform state in a team, and how do you prevent two engineers corrupting it?

**Spoken answer:**

"Terraform state must never live on a laptop or in Git. I use a remote backend in an Azure Storage account — a dedicated, locked-down storage account in a management subscription, with blob versioning and soft delete enabled so we can recover a previous state file.

The azurerm backend supports state locking automatically using a blob lease. When one person or pipeline runs plan or apply, the state blob is leased, and anyone else trying at the same time gets a lock error instead of corrupting the state.

But the real control is process: in production, nobody runs apply from their machine. All applies go through the pipeline, with plan on the pull request, a human approval, and apply of the saved plan file. I split state by environment and by component — for example networking, shared services and each application — so the blast radius is small and runs are fast.

Authentication uses OIDC or managed identity, and access to the state storage is restricted with RBAC because the state file can contain sensitive values."

**Three important technical points:**

- **azurerm backend**: resource_group_name, storage_account_name, container_name, key. Locking uses **blob leases**. Enable **versioning, soft delete, private endpoint or firewall**, and use Entra ID auth (use_azuread_auth = true) instead of access keys.

- **Stuck lock**: confirm no run is active, then terraform force-unlock \<LOCK_ID\>. Never break a lock while an apply is running.

- **State contains secrets** in plain text — restrict access, and mark outputs sensitive = true.

```hcl
terraform {

required_version = ">= 1.6.0"

required_providers {

azurerm = { source = "hashicorp/azurerm", version = "~> 4.0" }

}

backend "azurerm" {

resource_group_name = "rg-tfstate-prod"

storage_account_name = "sttfstateprod001"

container_name = "tfstate"

key = "payments/prod.terraform.tfstate"

use_azuread_auth = true

use_oidc = true # when running in a pipeline with workload identity federation

}

}

provider "azurerm" {

features {}

subscription_id = var.subscription_id # required in azurerm provider v4

}
```

**Practical production example:** A pipeline run was cancelled mid-apply and the next run fails with "Error acquiring the state lock". You check no agent is still running the job, read the lock ID from the error, run terraform force-unlock \<LOCK_ID\>, then run terraform plan to confirm the state matches reality before applying.

**Possible follow-up questions:**

- *"State file got corrupted or deleted — what now?"* — Restore the previous blob version from Storage versioning or soft delete. Then run terraform plan to check drift.

- *"How do you share outputs between states?"* — The terraform_remote_state data source, or better, data sources that look up resources directly (for example azurerm_virtual_network), which reduces coupling.

## Q10 ★ TOP 10 — The application works with 1,000 users but becomes slow at 20,000 concurrent users. How do you investigate and scale it?

**Spoken answer:**

"First I find the bottleneck with data — I don't just add servers. I run or reproduce a load test, for example with Azure Load Testing, and watch Application Insights and Azure Monitor at the same time. I look at where the time goes: application CPU and memory, dependency calls to the database, or something like connection limits or thread starvation.

Very often the bottleneck is the database, not the web tier. In Azure SQL, I check DTU or vCore utilisation, Query Performance Insight and Query Store for slow queries and missing indexes.

Then I scale the right layer. The web tier should be stateless so it can scale out horizontally with autoscale — on App Service, VM Scale Sets or AKS with the Horizontal Pod Autoscaler. I add caching with Azure Cache for Redis to take read load off the database, use a CDN or Front Door for static content, and move slow work to background processing with Service Bus queues.

Finally, I validate with another load test and set autoscale rules and alerts so it handles the next peak automatically."

**Three important technical points:**

- **Measure first**: Application Insights (dependency duration, Performance blade, Application Map), Azure Load Testing, SQL Query Store.

- **Scale out stateless tiers**; avoid in-memory sessions (use Redis or tokens); disable ARR affinity on App Service when not needed.

- **Protect the data tier**: caching, read replicas / geo-replicas for read scale-out, connection pooling, async processing with queues.

```kusto
// Which dependencies are slowest under load

AppDependencies

| where TimeGenerated > ago(1h)

| summarize Calls = count(), P95ms = percentile(DurationMs, 95), Failures = countif(Success == false)

by Target, DependencyType

| order by P95ms desc
```

**Practical production example:** During a sale, response time rises from 300 ms to 8 seconds. Application Insights shows 85% of request time is a single SQL query. Query Store shows a table scan on the Orders table. You add the missing index, add Redis caching for the product catalogue, and set App Service autoscale from 3 to 15 instances on CPU and HTTP queue length. The next load test at 25,000 users stays under 500 ms.

**Possible follow-up questions:**

- *"Scale up vs scale out?"* — Scale up for a quick fix or stateful components; scale out for resilience and elasticity. Scale-out needs a stateless design.

- *"Autoscale is configured but didn't help."* — Check if it hit the maximum instance count, subscription quota, or a slow start-up time; check if the bottleneck is downstream so more instances made the database worse.

## Q11 — A production service principal credential has expired and the deployment pipeline is failing. What do you do?

**Spoken answer:**

"The error in the pipeline will usually be something like AADSTS7000222 — the client secret has expired. First, I confirm which app registration the service connection uses, from the service connection details in Azure DevOps.

To restore deployments quickly, I create a new client secret on the app registration, update the service connection in Azure DevOps, and re-run the pipeline. I also check whether the same secret is used anywhere else — Key Vault, other pipelines or applications.

But the permanent fix is to remove the secret completely. I convert the service connection to workload identity federation, which uses short-lived OIDC tokens — there is nothing to expire. For workloads running in Azure, I use managed identities instead of service principals.

Finally, I'd add monitoring: a scheduled script or a Logic App that checks all app registrations for credentials expiring in the next 30 days and alerts the owners."

**Three important technical points:**

- Error codes: **AADSTS7000222** (expired secret), **AADSTS7000215** (invalid secret).

- **Workload identity federation** is the recommended authentication for Azure Resource Manager service connections; existing secret-based connections can be converted in the UI.

- Monitor expiry with Microsoft Graph / az ad app credential list.

```bash
# Check credential expiry for an app registration

az ad app credential list --id <app-id> --query "[].{Name:displayName, Ends:endDateTime}" -o table

# Create a new secret (short-term fix), output once — store securely

az ad app credential reset --id <app-id> --display-name "ado-sc-2026" --years 1 --append

**Production example:** At 9 a.m. all production deployments fail. The service principal secret expired overnight. You reset it with --append (so the old one isn't removed during transition), update the service connection, and the release proceeds. That afternoon you convert the connection to workload identity federation and raise a backlog item to convert all remaining connections.
```

**Follow-ups:**

- *"Why use --append?"* — Without it, credential reset replaces existing credentials, which can break other systems still using the old secret.

- *"Who should own app registrations?"* — Assign named owners (or groups), document them, and review them in access reviews.

## Q12 — What is the difference between a managed identity and a service principal, and when do you use each?

**Spoken answer:**

"Both are identities for applications in Microsoft Entra ID. A managed identity is actually a special type of service principal, but Azure manages its credentials for you — there's no secret or certificate to store or rotate.

There are two types. A system-assigned managed identity is tied to one resource, like an App Service or VM — when the resource is deleted, the identity is deleted. A user-assigned managed identity is a standalone resource that I can attach to multiple resources, which is useful for scale sets, AKS workloads or when I want the identity to exist before the resource.

I use managed identities whenever the code runs in Azure — for example an App Service reading from Key Vault or a Function writing to Storage. I use a service principal when something runs outside Azure and needs to access Azure — like a third-party tool. For Azure DevOps and GitHub, I use workload identity federation so even the service principal has no secret."

**Three important technical points:**

- Managed identity = no credentials in code, automatic rotation, Entra ID token via local endpoint (IMDS).

- **System-assigned** (lifecycle tied to resource) vs **user-assigned** (independent, reusable, pre-provisioned RBAC).

- **AKS workload identity** federates a Kubernetes service account with a user-assigned managed identity (replaces the deprecated pod-managed identity).

**Production example:** A Function App used a storage account connection string in app settings. You enable a system-assigned identity, grant it **Storage Blob Data Contributor** on the storage account, switch the code to DefaultAzureCredential, and then disable shared key access on the storage account.

**Follow-ups:**

- *"How does the app get a token?"* — The Azure SDK's DefaultAzureCredential calls the managed identity endpoint, which returns an Entra ID access token for the target resource.

- *"Can a managed identity access resources in another subscription?"* — Yes, if they're in the same Entra ID tenant and you assign RBAC at that scope.

## Q13 — How would you build a custom monitoring dashboard for a production service?

**Spoken answer:**

"I start from what the audience needs to decide. An operations dashboard needs the four golden signals — traffic, errors, latency and saturation — per service. A leadership view needs availability against SLO and maybe cost.

My preferred tool in Azure is Azure Monitor Workbooks, because they are interactive: I can add parameters for subscription, environment and time range, combine KQL queries, metrics and text, and drill down from one chart to details. For a wall screen or quick pinned view, I use Azure Dashboards. If the organisation uses Grafana, Azure Managed Grafana connects to Azure Monitor natively.

I keep dashboards as code — Workbooks and dashboards can be exported as ARM JSON and deployed with Terraform or Bicep — so they're consistent across environments and version-controlled."

**Three important technical points:**

- **Workbooks**: parameters, KQL + metrics, grids, drill-down, templates; stored as ARM resources (Microsoft.Insights/workbooks).

- **Azure Dashboards**: pin tiles from metrics/logs; shareable via RBAC; deployable as Microsoft.Portal/dashboards.

- **Azure Managed Grafana**: good for multi-cloud or teams already using Grafana; uses managed identity to read Azure Monitor.

```kusto
// Golden signals per operation (for a Workbook grid)

AppRequests

| where TimeGenerated {TimeRange}

| summarize Requests = count(),

ErrorRatePct = round(100.0 * countif(Success == false) / count(), 2),

P50ms = percentile(DurationMs, 50),

P95ms = percentile(DurationMs, 95)

by OperationName

| order by Requests desc
```

> {TimeRange} is a Workbook parameter placeholder. In a plain Logs query replace it with \> ago(1h).

**Production example:** You create a "Payments Service Health" workbook: top row shows availability test results and SLO; second row shows request rate, error rate and p95 latency; third row shows dependency health and AKS node/pod CPU. The on-call team uses it as the first screen in every incident.

**Follow-ups:**

- *"Workbook vs dashboard?"* — Workbooks for investigation and rich reports; dashboards for at-a-glance pinned tiles.

- *"How do you avoid dashboards nobody uses?"* — Build them with the users, link them from alerts and runbooks, and review usage.

## Q14 — CPU utilisation is consistently above 90% on a production VM. How do you find the root cause?

**Spoken answer:**

"First I confirm it's real and whether it's affecting users — check the Percentage CPU metric over a week to see if it's a sudden change or a gradual trend, and correlate with response times.

Then I find which process is using the CPU. With the Azure Monitor Agent and VM insights, I can see performance counters, and on the VM I use Task Manager or Performance Monitor on Windows, or top and pidstat on Linux. I also check the Activity Log and change tracking for recent deployments, patches or new scheduled tasks.

I also check the VM type — on B-series burstable VMs, when CPU credits run out, performance is throttled, which looks like high CPU.

Then the fix depends on the cause: fix the code or query if it's an application issue, stop a runaway process, scale up to a bigger size, or better, scale out behind a load balancer with a VM Scale Set if the load is legitimate."

**Three important technical points:**

- Platform metric **Percentage CPU** (host view) vs guest counters via **Azure Monitor Agent** (process-level detail).

- **B-series** credits: metric CPU Credits Remaining.

- Tools: **Diagnose and solve problems**, **Run Command** (no RDP/SSH needed), **Performance Diagnostics** extension.

```kusto
// Guest CPU from Perf table (AMA with DCR collecting processor counters)

Perf

| where TimeGenerated > ago(24h)

| where ObjectName == "Processor" and CounterName == "% Processor Time" and InstanceName == "_Total"

| summarize AvgCPU = avg(CounterValue), MaxCPU = max(CounterValue) by Computer, bin(TimeGenerated, 15m)

| order by TimeGenerated desc
```

```bash
# Run a command inside a Linux VM without SSH

az vm run-command invoke -g <rg> -n <vm> --command-id RunShellScript \

--scripts "top -b -n1 | head -20"

**Production example:** A VM running an API sits at 95% CPU since Tuesday. Change tracking shows a new antivirus full-scan schedule deployed by policy at the same time. You add exclusions for the application folders and move the scan window — CPU drops to 40%.
```

**Follow-ups:**

- *"How would you prevent it?"* — Alert on CPU with dynamic thresholds, capacity planning reviews, and autoscale with VMSS.

- *"Scale up or scale out?"* — Scale up is quick but needs a restart; scale out gives resilience but needs a stateless app behind a load balancer.

## Q15 — Application Insights stopped receiving telemetry after a deployment. How do you troubleshoot?

**Spoken answer:**

"Because it started after a deployment, the first thing I compare is configuration. The most common cause is that the connection string app setting was removed or changed — for example a slot setting that didn't swap, or a new deployment template that overwrote app settings.

I check the APPLICATIONINSIGHTS_CONNECTION_STRING setting on the app, and confirm it points to the right Application Insights resource and region. If the app still uses only an instrumentation key, that needs to move to a connection string, since instrumentation key ingestion is no longer supported.

Then I check the network: if Application Insights uses Azure Monitor Private Link Scope or the app has outbound restrictions, the new deployment might not reach the ingestion endpoint. I check the SDK or agent: was the SDK removed, or was the auto-instrumentation agent turned off?

I also check whether the daily cap on the workspace was reached and whether sampling was set too aggressively. Live Metrics is a quick test — if Live Metrics shows data but the logs don't, it's ingestion; if nothing shows, the app isn't sending."

**Three important technical points:**

- APPLICATIONINSIGHTS_CONNECTION_STRING — connection strings are required; instrumentation-key-only ingestion ended in March 2025.

- Network: ingestion endpoints, **Azure Monitor Private Link Scope (AMPLS)**, NSG/firewall egress, local auth disabled requires Entra ID-authenticated ingestion.

- Data limits: **daily cap**, **sampling** settings, ingestion delay (normally a few minutes).

**Production example:** A Bicep template was rewritten to set app settings and accidentally replaced the full appSettings list, removing the connection string. Telemetry stopped for two days. Fix: add the setting to the template. Prevention: an availability test plus a log alert "no requests received in 15 minutes".

```kusto
// Alert: no telemetry received in the last 15 minutes

AppRequests

| where TimeGenerated > ago(15m)

| count

| where Count == 0
```

**Follow-ups:**

- *"How do you check if the daily cap was hit?"* — Workspace → Usage and estimated costs → Daily cap, and query the \_LogOperation function / Operation table for cap events.

- *"Codeless vs SDK?"* — Auto-instrumentation is quick; SDK or OpenTelemetry distro gives custom telemetry and more control.

## Q16 — Explain the difference between metrics, logs and traces, and how you use them together.

**Spoken answer:**

"Metrics are numbers measured over time — CPU, request count, latency. They're lightweight, near real-time and good for alerting and dashboards. Logs are detailed event records with context — an error message, a request with its properties. They're richer but slower and more expensive to store and query. Traces follow a single request across services — they show that a request went from the front end to the API to SQL and where the time was spent.

I use them together. A metric alert tells me error rate jumped. Logs tell me which operation and what exception. A distributed trace shows me which downstream dependency caused it. In Azure, platform metrics live in the Azure Monitor metrics store, logs in Log Analytics, and Application Insights provides distributed tracing using correlation IDs — now based on W3C Trace Context and OpenTelemetry."

**Three important technical points:**

- Metrics: numeric, pre-aggregated, 93-day retention for platform metrics, fast alerting.

- Logs: KQL in Log Analytics; flexible but costed by ingestion and retention.

- Traces: operation_Id / W3C traceparent correlation; **Application Map** and **end-to-end transaction** view.

**Production example:** p95 latency metric alert fires. The end-to-end transaction shows 4 seconds spent calling a payment provider API. Dependency logs show timeouts started at 14:05. You enable a circuit breaker and contact the provider.

**Follow-ups:**

- *"What is OpenTelemetry's role?"* — It is the vendor-neutral standard; Azure Monitor provides an OpenTelemetry distro that sends to Application Insights.

- *"How do you trace across a queue?"* — Propagate correlation headers in message properties; the SDKs do this for Service Bus and Event Hubs.

## Q17 — An AKS application is experiencing pod restarts / CrashLoopBackOff and intermittent latency. How do you troubleshoot?

**Spoken answer:**

"I start with kubectl get pods to see the status and restart count, then kubectl describe pod to read the events and the last state — the exit code tells a lot. Exit code 137 with reason OOMKilled means the container exceeded its memory limit. Then I run kubectl logs --previous to see the logs from the container that crashed, not the new one.

Common causes are: the app crashing on start-up because of a missing config or secret, memory limits too low, a liveness probe that is too aggressive and kills a slow-starting app, or a failing dependency.

For intermittent latency, I check CPU throttling — if the CPU limit is too low the container is throttled even if the node has spare capacity. I check node pressure with kubectl top nodes and Container Insights, and whether pods are being evicted.

Fixes are things like setting correct requests and limits, adding a startup probe for slow apps, fixing configuration, and using the Horizontal Pod Autoscaler and cluster autoscaler so we have capacity."

**Three important technical points:**

- describe → **Events** and **Last State** (exit code 137 = SIGKILL/OOMKilled; 1 = application error).

- **Probes**: liveness (restart), readiness (remove from traffic), startup (protect slow start).

- **Requests/limits**: HPA needs CPU/memory **requests** set; CPU limits cause throttling; memory limits cause OOMKill.

```bash
kubectl get pods -n payments -o wide

kubectl describe pod <pod-name> -n payments

kubectl logs <pod-name> -n payments --previous

kubectl get events -n payments --sort-by=.lastTimestamp

kubectl top pods -n payments

kubectl top nodes
```

```kusto
// Container Insights: pods with restarts

KubePodInventory

| where TimeGenerated > ago(1h) and Namespace == "payments"

| summarize Restarts = max(ContainerRestartCount) by Name, ContainerStatusReason

| where Restarts > 0

| order by Restarts desc

**Production example:** After a release, pods restart every 2 minutes. describe shows OOMKilled. The new version loads a larger cache at start-up. You raise the memory limit from 512Mi to 1Gi, tune the cache size, and add a startup probe.
```

**Follow-ups:**

- *"Liveness vs readiness?"* — Liveness restarts a stuck container; readiness only stops sending traffic. A liveness probe that checks dependencies can cause cascading restarts — avoid that.

- *"How do you debug a container that dies too fast to exec into?"* — kubectl logs --previous, kubectl debug with an ephemeral container, or temporarily override the command.

## Q18 — How do you manage secrets in CI/CD pipelines and applications securely?

**Spoken answer:**

"My principle is: the best secret is no secret. Wherever possible I use managed identities for apps and workload identity federation for pipelines, so there are no passwords at all.

Where secrets are unavoidable — like a third-party API key — they live in Azure Key Vault. Applications read them at runtime using a managed identity, for example with App Service Key Vault references or the Secrets Store CSI driver on AKS. Pipelines get them through a variable group linked to Key Vault or the AzureKeyVault task, and they're automatically masked in logs.

I use Key Vault's RBAC permission model with least privilege — for example Key Vault Secrets User for apps — enable soft delete and purge protection, restrict network access with a private endpoint, and send Key Vault diagnostic logs to Log Analytics to audit who accessed what.

And I prevent secrets from getting into code with secret scanning in the repository and pull-request checks."

**Three important technical points:**

- **Key Vault**: RBAC model (recommended over access policies), soft delete + purge protection, private endpoint, diagnostic logs (AuditEvent).

- **Pipelines**: variable groups linked to Key Vault, AzureKeyVault@2 task, secret variables are masked, never echo secrets.

- **Apps**: Key Vault references in App Service (@Microsoft.KeyVault(SecretUri=...)), Secrets Store CSI driver on AKS, rotation with Event Grid notifications.

```yaml
steps:

\- task: AzureKeyVault@2

inputs:

azureSubscription: sc-azure-prod

KeyVaultName: kv-payments-prod

SecretsFilter: 'PaymentProviderApiKey'

RunAsPreJob: false

\- script: ./deploy.sh

env:

PROVIDER_KEY: $(PaymentProviderApiKey) # secrets must be mapped explicitly into env

**Production example:** A secret was committed to Git in a config file. You rotate it immediately (treat it as compromised), remove it from history, move it to Key Vault, enable secret scanning (GitHub Advanced Security for Azure DevOps) and add a pre-commit hook.
```

**Follow-ups:**

- *"Is deleting the commit enough?"* — No. Assume it's compromised; rotate first, then clean up.

- *"Access policies vs RBAC?"* — RBAC is the recommended model: consistent with Azure RBAC, supports PIM and per-secret scope.

## Q19 — Explain blue-green and canary deployments and how you'd implement them on Azure.

**Spoken answer:**

"Both reduce deployment risk. In blue-green, I have two identical environments — blue is live, green gets the new version. I test green, then switch all traffic at once. Rollback is just switching back. On App Service, deployment slots give this pattern out of the box — deploy to the staging slot, warm up, test, then swap.

Canary is gradual. I send a small percentage of traffic — say 5% — to the new version, watch error rate and latency, and increase step by step if it's healthy. On App Service I can use slot traffic routing. On AKS, I can use the canary strategy in Azure DevOps deployment jobs, or a service mesh or ingress controller that supports weighted routing. Front Door or Traffic Manager can split traffic between whole environments.

The key to canary is automated health checks — Azure DevOps can use an Azure Monitor alerts check as a gate, so if alerts fire, the rollout stops."

**Three important technical points:**

- **Blue-green**: instant switch, easy rollback, double resources during release.

- **Canary**: gradual exposure, needs good metrics and automated gates; strategy: canary with increments: \[10, 20\] in deployment jobs.

- **Feature flags** (Azure App Configuration) separate deployment from release.

**Production example:** A pricing service change goes to 10% of traffic via slot routing. Application Insights shows error rate 3% on the new version vs 0.1% on the old. You route 0% to the slot, fix and redeploy — 90% of users never saw the issue.

**Follow-ups:**

- *"Problem with blue-green and databases?"* — Both versions share the database, so schema changes must be backward-compatible.

- *"Sticky sessions with slots?"* — App Service routing uses a cookie (x-ms-routing-name) so a user stays on the same version.

## Q20 — Someone manually deletes an Azure resource managed by Terraform. What happens during the next terraform plan?

**Spoken answer:**

"Terraform refreshes state against Azure during plan. It sees that the resource in state no longer exists, removes it from the in-memory state and plans to create it again. So the plan will show it as '+ create'. If other resources depend on it, they may also show changes.

So Terraform will restore it — but there are traps. For data resources like a database or storage account, recreating gives you an empty resource, not your data, so you'd restore from backup or soft delete first. Some resources like Key Vault have soft delete, so re-creating with the same name might conflict with the soft-deleted one — you'd need to recover or purge it.

The more important conversation is why someone could delete it manually. I'd prevent it with RBAC — no Contributor in production for people — resource locks on critical resources, and scheduled drift detection, where a pipeline runs terraform plan -detailed-exitcode every night and alerts if there's drift."

**Three important technical points:**

- terraform plan refreshes by default; missing resource → planned **create**. Use terraform plan -refresh-only to see drift without changing anything.

- If someone modified (not deleted) a resource, plan shows **update in-place** or **replace** to return it to the code.

- If a resource exists in Azure but not in state, use an **import block** (Terraform 1.5+) or terraform import.

```bash
# Nightly drift detection: exit code 0 = no changes, 1 = error, 2 = changes (drift)

terraform plan -detailed-exitcode -lock-timeout=5m -out=drift.tfplan
```

```hcl
# Bring an existing resource under management (Terraform 1.5+)

import {

to = azurerm_resource_group.payments

id = "/subscriptions/<sub-id>/resourceGroups/rg-payments-prod"

}

**Production example:** An engineer deletes an NSG rule in the portal to "test something". The nightly drift pipeline returns exit code 2 and posts to Teams. The team re-applies, and the engineer's Contributor access is moved to PIM eligibility.
```

**Follow-ups:**

- *"How do you protect critical resources from deletion?"* — CanNotDelete resource locks, lifecycle { prevent_destroy = true } in Terraform, and RBAC.

- *"Someone changed a tag manually and you want Terraform to ignore it?"* — lifecycle { ignore_changes = \[tags\] } — use carefully.

## Q21 — Terraform vs Bicep: which would you choose and why?

**Spoken answer:**

"Both are good declarative IaC tools. Bicep is Azure-native — it compiles to ARM, supports new Azure features on day one, and has no state file, because Azure itself is the state. It's a great choice for Azure-only teams. Features like what-if and deployment stacks help with previews and managing deletions.

Terraform is multi-cloud and multi-provider — I can manage Azure, Entra ID, Azure DevOps, GitHub, Datadog and more in one workflow. It has a large module ecosystem and a strong plan workflow, but I must manage the state file securely.

My choice depends on the organisation. If they already use Terraform, or they're multi-cloud, or they manage many non-Azure things, I choose Terraform. If they are Azure-only and want simplicity with no state management, Bicep is excellent. The worst outcome is mixing both for the same resources. The job description mentions both, so I'm comfortable working in either and keeping a clear boundary between them."

| **Aspect**                    | **Terraform**                                   | **Bicep**                                         |
|-------------------------------|-------------------------------------------------|---------------------------------------------------|
| Scope                         | Multi-cloud, many providers                     | Azure only                                        |
| State                         | State file (secure remote backend needed)       | No state file — Azure is the source of truth      |
| New Azure features            | Depends on provider release (or azapi provider) | Day-one support                                   |
| Preview                       | terraform plan                                  | az deployment group what-if                       |
| Deletion of removed resources | Yes, by default                                 | Via deployment stacks or complete mode            |
| Modules                       | Terraform Registry, private registries          | Bicep modules, Azure Verified Modules, registries |

**Follow-ups:**

- *"How do you handle a new Azure feature not in the azurerm provider?"* — Use the azapi provider, which calls the ARM REST API directly.

- *"What are Azure Verified Modules?"* — Microsoft-supported, standardised modules for both Bicep and Terraform.

## Q22 — How do you design for high availability and disaster recovery on Azure?

**Spoken answer:**

"I start with business requirements — RTO, how long we can be down, and RPO, how much data we can lose. Those numbers decide the design and cost.

For high availability inside a region, I use availability zones — zone-redundant App Service plans, zone-redundant Azure SQL, AKS node pools across zones, zone-redundant storage, and a zone-redundant Application Gateway or Load Balancer. That protects against a datacenter failure.

For disaster recovery across regions, options range from backup and restore — cheapest but slowest — to warm standby or active-active. Azure SQL failover groups give a single listener endpoint and geo-replication. Storage can use GRS or GZRS. Front Door routes traffic globally and fails over automatically based on health probes. For VMs, Azure Site Recovery replicates to another region.

Infrastructure as code is a big part of DR — I can rebuild a region from Terraform. And most importantly, we test failover regularly. An untested DR plan is just a document."

**Three important technical points:**

- **RTO / RPO** drive the pattern: backup-restore → pilot light → warm standby → active-active.

- **Zones** for in-region HA; **paired / secondary region** for regional DR. Not every region has zones — check.

- Services: **Front Door / Traffic Manager**, **SQL failover groups**, **GZRS/RA-GZRS**, **Azure Site Recovery**, **Azure Backup** (cross-region restore).

**Production example:** A payments platform needs RTO 1 hour, RPO 5 minutes. Design: active-passive across UK South and UK West; Front Door with priority routing; Azure SQL auto-failover group; container images geo-replicated in ACR Premium; Terraform pipeline that can deploy the secondary stack; quarterly failover drills.

**Follow-ups:**

- *"Active-active challenges?"* — Data consistency, write conflicts, cost doubling, and session handling.

- *"How do you test DR without impacting production?"* — Planned failover in a maintenance window, ASR test failover into an isolated VNet, and chaos testing with Azure Chaos Studio.

## Q23 — Azure Front Door vs Application Gateway vs Load Balancer vs Traffic Manager — when do you use each?

**Spoken answer:**

"I separate them on two questions: is it global or regional, and is it layer 7 HTTP or layer 4 TCP/UDP.

Azure Front Door is global and layer 7. It gives global HTTP load balancing, CDN caching, WAF at the edge, SSL offload and fast failover between regions — for public web apps across regions.

Application Gateway is regional and layer 7 — path-based routing, WAF, SSL termination and end-to-end TLS inside a VNet. It's also the ingress option for AKS with Application Gateway for Containers.

Azure Load Balancer is regional and layer 4 — very high performance for TCP/UDP traffic, for VMs and scale sets, internal or public.

Traffic Manager is global DNS-based routing — it only answers DNS queries, so it works for any protocol but failover depends on DNS TTL.

A common enterprise pattern is Front Door in front of Application Gateway or App Service, with private origins using Private Link in the Premium tier."

| **Service**         | **Scope** | **Layer** | **Key features**                                          |
|---------------------|-----------|-----------|-----------------------------------------------------------|
| Front Door          | Global    | L7        | CDN, WAF, global failover, Private Link origins (Premium) |
| Application Gateway | Regional  | L7        | WAF, path routing, end-to-end TLS, VNet integrated        |
| Load Balancer       | Regional  | L4        | TCP/UDP, HA ports, internal/public                        |
| Traffic Manager     | Global    | DNS       | Any protocol, DNS-based, priority/weighted/geographic     |

**Follow-ups:**

- *"Application Gateway returns 502 — first check?"* — Backend health blade; NSG on the App Gateway subnet, probe path, backend certificate trust and timeouts.

- *"Why not just Traffic Manager?"* — DNS caching makes failover slower, and there's no WAF or caching.

## Q24 — How do you use Azure Policy to enforce governance and security guardrails?

**Spoken answer:**

"Azure Policy evaluates resources against rules and enforces standards at scale. I assign policies at management group level so every subscription inherits them.

I group them into initiatives — for example a security baseline and a tagging initiative. Effects matter: Deny blocks non-compliant deployments, like public IPs on production or unapproved regions. Audit reports without blocking — I use that first to measure impact before switching to Deny. Modify can add tags automatically, and DeployIfNotExists can deploy things like diagnostic settings or Defender agents.

I always roll out carefully: start in audit mode, check the compliance dashboard, communicate with teams, then enforce. Exemptions are documented with an expiry date. And I manage policy as code — definitions and assignments in Terraform or Bicep through a pipeline."

**Three important technical points:**

- Effects: **Deny, Audit, AuditIfNotExists, DeployIfNotExists, Modify, Append, DenyAction, Disabled**.

- **Remediation tasks** fix existing resources for DINE/Modify; the assignment needs a **managed identity** with the right roles.

- Built-in initiatives: **Microsoft Cloud Security Benchmark** (default in Defender for Cloud), ISO 27001, NIST, CIS.

**Production example:** You assign "Allowed locations" (UK South, UK West) with Deny, "Require a tag on resource groups" (owner, cost-centre) with Deny, and "Inherit a tag from the resource group" with Modify. Untagged costs fall from 40% to under 5% in a month.

**Follow-ups:**

- *"Policy vs RBAC?"* — RBAC controls **who** can do actions; Policy controls **what** resources and configurations are allowed regardless of who.

- *"Policy blocked a legitimate deployment urgently?"* — Create a time-limited exemption with justification, not delete the assignment.

## Q25 — Explain Private Endpoints and the DNS issues that commonly break them.

**Spoken answer:**

"A private endpoint gives a PaaS service, like Key Vault, SQL or Storage, a private IP address inside my VNet. Then I disable public network access, so the service is only reachable privately.

The common problem is DNS. The service name, like kv-prod.vault.azure.net, must resolve to the private IP, not the public one. Azure does this through a CNAME to a privatelink zone, for example privatelink.vaultcore.azure.net. I create a private DNS zone with that name, link it to the VNets that need it, and the private endpoint registers an A record.

Issues happen when the zone isn't linked to the VNet, when VNets use custom DNS servers that don't forward to Azure DNS at 168.63.129.16, or when on-premises clients resolve the public IP. For hybrid, I use Azure DNS Private Resolver with an inbound endpoint and conditional forwarders from on-prem DNS. In large estates, I centralise the private DNS zones in the hub and use Azure Policy to create the DNS records automatically."

**Three important technical points:**

- Test with nslookup \<name\> from inside the VNet: should return a **10.x private IP** and show the privatelink alias.

- Private DNS zone names per service: privatelink.vaultcore.azure.net, privatelink.blob.core.windows.net, privatelink.database.windows.net, privatelink.azurecr.io.

- **168.63.129.16** is Azure's DNS/virtual public IP; custom DNS servers must forward to it (or to Private Resolver).

```bash
nslookup kv-payments-prod.vault.azure.net

# Expected (from inside VNet):

# kv-payments-prod.vault.azure.net canonical name = kv-payments-prod.privatelink.vaultcore.azure.net

# Address: 10.20.4.5

az network private-dns link vnet list -g rg-dns-hub -z privatelink.vaultcore.azure.net -o table

**Production example:** After disabling public access on Key Vault, the App Service fails to read secrets. The App Service uses VNet integration, but the spoke VNet isn't linked to the private DNS zone — it resolved the public IP and was blocked. Linking the zone fixes it.
```

**Follow-ups:**

- *"Private endpoint vs service endpoint?"* — Private endpoint gives a private IP and works from on-prem and peered VNets; service endpoint keeps the public IP but restricts access to a subnet. Private endpoint is preferred for data exfiltration protection.

- *"App Service outbound to a private endpoint?"* — Requires regional VNet integration and DNS resolution via the linked zone.

## Q26 — How do you reduce Log Analytics ingestion costs without losing important visibility?

**Spoken answer:**

"First I measure — the Usage table shows which tables and which resources ingest the most. Usually a few sources cause most of the cost: verbose container logs, debug application logs, or diagnostic settings sending every category.

Then I reduce at the source: lower application log levels in production, enable sampling in Application Insights, and in diagnostic settings only send the categories we actually use.

Then I reduce at ingestion using Data Collection Rule transformations — for example dropping health-check requests or unneeded columns before they're stored.

I choose the right table plan: Analytics for data we alert and query often; Basic or Auxiliary logs for high-volume data used mainly for troubleshooting, which is much cheaper to ingest. For long-term compliance, I keep data in long-term retention instead of interactive retention.

If daily volume is stable and high, a commitment tier gives a discount. And I set a data volume alert so we see spikes early."

**Three important technical points:**

- **Usage** table and **Workspace Insights** to find top tables and sources.

- **Table plans**: Analytics vs Basic vs Auxiliary; **long-term retention** (up to 12 years); **commitment tiers** from 100 GB/day.

- **DCR transformations** (KQL filter at ingestion), **sampling** in App Insights, **daily cap** as a safety net (not a cost strategy for production).

```kusto
// Top resources sending billable data in the last 7 days

find where TimeGenerated > ago(7d) project _ResourceId, _BilledSize, _IsBillable

| where _IsBillable == true

| summarize BillableGB = sum(_BilledSize) / 1e9 by _ResourceId

| top 10 by BillableGB
```

**Follow-ups:**

- *"Why not just set a daily cap?"* — Once the cap is reached, data collection stops, so you can lose security and incident data at the worst time.

- *"Can you alert on Basic logs?"* — Basic logs have limited query capability and are not the right choice for data you alert on frequently.

## Q27 — Reserved Instances vs Savings Plans — when would you use each?

**Spoken answer:**

"Both are commitments for one or three years in exchange for a discount compared with pay-as-you-go.

Reservations commit to a specific resource type and region — for example a particular VM size family in UK South. They usually give the highest discount and also exist for services like Azure SQL, Cosmos DB, App Service and storage.

The Azure savings plan for compute commits to an hourly spend amount across compute services — VMs, App Service, Functions Premium, container instances — in any region and size. It's more flexible but usually a slightly smaller discount than a reservation.

My approach: use reservations for very stable, predictable workloads like a database or core VMs that won't change; use a savings plan for the compute base that changes size or region; leave spiky workloads on pay-as-you-go or use spot VMs for interruptible work. I always rightsize first — buying a reservation for an oversized VM locks in waste. I check Azure Advisor's recommendations and monitor utilisation."

**Follow-ups:**

- *"What happens if you don't use the reservation?"* — You still pay; unused hours are wasted. Monitor reservation utilisation and use exchanges where allowed.

- *"Spot VMs?"* — Up to large discounts but can be evicted — good for batch, CI agents, and AKS spot node pools for fault-tolerant workloads.

## Q28 — How do you build a Docker image in CI and push it securely to Azure Container Registry, and pull it from AKS?

**Spoken answer:**

"In the pipeline, I use the Docker task with a service connection to ACR — ideally using workload identity federation. I build with a multi-stage Dockerfile so the final image is small and doesn't include build tools. I tag images with an immutable version, like the build ID or Git commit SHA — never just 'latest' for production.

Before pushing or before deploying, I scan the image for vulnerabilities — Defender for Containers scans images in ACR — and the pipeline can fail on critical findings.

For AKS to pull, I attach ACR to AKS, which gives the kubelet managed identity the AcrPull role. No image pull secrets are needed. For security, I disable the ACR admin user, use a private endpoint on ACR Premium, and if possible restrict AKS to pull only from our registry using Azure Policy."

**Three important technical points:**

- Immutable tags (commit SHA / build ID); multi-stage builds; non-root user in the image.

- az aks update --attach-acr \<acr\> grants **AcrPull** to the kubelet identity; az aks check-acr validates it.

- **Defender for Containers** vulnerability scanning; disable **admin user**; Premium SKU for private link and geo-replication.

**DOCKERFILE**

\# Multi-stage build

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

COPY . .

RUN dotnet publish -c Release -o /app

FROM mcr.microsoft.com/dotnet/aspnet:8.0

WORKDIR /app

COPY --from=build /app .

USER app

ENTRYPOINT \["dotnet", "Payments.Api.dll"\]

```bash
az aks update -g <rg> -n <aks> --attach-acr <acr-name>

az aks check-acr -g <rg> -n <aks> --acr <acr-name>.azurecr.io
```

**Follow-ups:**

- *"Pods show ImagePullBackOff."* — Check kubectl describe pod events: wrong image name/tag, missing AcrPull role (401 unauthorized), or network/DNS to the ACR private endpoint.

- *"Why not the admin user?"* — It's a shared credential with full push/pull, no per-identity audit.

## Q29 — As a senior engineer, how do you establish best practices and mentor other engineers?

**Spoken answer:**

"I try to make the right way the easy way. Instead of writing long documents that people don't read, I build reusable things: Terraform modules with secure defaults, pipeline templates with built-in security scans, and policies that catch mistakes automatically.

I document decisions using short Architecture Decision Records, so people understand why we chose something, not only what. I run code reviews as a teaching opportunity — I explain the reason behind a comment and link to the standard.

For mentoring, I pair with engineers on real work — for example, letting a junior engineer lead an incident investigation while I support them, then reviewing it together. I run short knowledge-sharing sessions, like a KQL lunch-and-learn. I also make sure people can grow — I give them ownership of a component and increase scope as they gain confidence.

And I keep standards alive — reviewing them with the team every few months, because cloud services change quickly."

**Three key points:** paved roads (modules, templates, policy) · ADRs and blameless reviews · mentoring through ownership and pairing.

**Production example (illustrative):** Each team built its own AKS pipeline and only some had security scanning. You create a shared template, pair with two engineers to migrate their pipelines, and they then help the other teams — adoption grows without forcing it.

**Follow-ups:**

- *"A senior colleague disagrees with your design."* — Discuss with data and trade-offs, document options in an ADR, agree on criteria, and if needed run a small proof of concept. Disagree and commit once decided.

- *"Someone keeps making the same mistake."* — Private, supportive conversation; check if the process or tooling makes the mistake easy; automate a guardrail.

## Q30 — How do you communicate a major production incident to leadership?

**Spoken answer:**

"Leadership needs clear, short, regular updates — not technical detail. I separate roles: an incident commander coordinates and communicates, and engineers focus on fixing.

My updates follow a simple structure: what is happening, who is affected, what we're doing, and when the next update will be. For example: 'Since 10:15 UK time, around 30% of customers cannot complete payments. We have identified a database issue and are failing over to the secondary. Next update at 10:45.' I give updates on a fixed schedule even when there's no news, because silence creates anxiety.

I avoid guessing at the root cause too early. After resolution, I share a short summary, then a blameless post-incident review within a few days, with timeline, root cause, impact and action items with owners and dates."

**Three key points:** fixed update cadence · business impact first · blameless post-incident review with tracked actions.

**Follow-ups:**

- *"Leadership asks for an ETA you don't know."* — Be honest: "I can't give a reliable ETA yet; we're testing a fix now and I'll update you by 11:00." Never invent a time.

- *"Who decides to roll back?"* — The incident commander with the service owner, based on customer impact — pre-agreed in the incident process.

# Part B — Last-Minute Revision Plan (3–4 Hours)

## Hour-by-Hour Plan

| **Time block** | **What to do**                                                                            | **Goal**                                        |
|----------------|-------------------------------------------------------------------------------------------|-------------------------------------------------|
| 0:00 – 0:15    | Read this plan + the answer structure (Clarify → Stabilise → Investigate → Fix → Prevent) | Know the framework for every answer             |
| 0:15 – 1:15    | ★ TOP 10 questions (Q1–Q10). Speak each answer aloud twice.                               | Fluency on the most likely questions            |
| 1:15 – 1:30    | Break. Water, walk.                                                                       | Memory consolidation                            |
| 1:30 – 2:15    | Q11–Q20: read spoken answer once, memorise the 3 technical points                         | Breadth on identity, monitoring, AKS, Terraform |
| 2:15 – 2:45    | Q21–Q30: technical points only + leadership answers                                       | Architecture, cost, leadership                  |
| 2:45 – 3:15    | Essential commands and KQL (below). Write 5 KQL queries from memory.                      | Hands-on credibility                            |
| 3:15 – 3:30    | Common traps (below) and Part C phrases                                                   | Avoid weak answers                              |
| 3:30 – 4:00    | Prepare your own 3 stories (STAR) and your questions for the interviewer                  | Personal and behavioural round                  |

> **Sleep matters more than one extra hour of study.** If it is late, cut the 2:15–2:45 block, not your sleep.

## Study First — Highest-Value Topics

**1. RBAC**: Contributor vs Owner vs User Access Administrator vs RBAC Administrator; scopes and inheritance; groups; PIM; managed identity vs service principal; workload identity federation.

**2. Monitoring**: Azure Monitor architecture (metrics, logs, Log Analytics, Application Insights), diagnostic settings, AMA + DCR, alert types, action groups, alert processing rules, Workbooks.

**3. Azure DevOps**: multi-stage YAML, environments with approvals and checks, service connections, variable groups + Key Vault, templates, slot swap, rollback.

**4. Terraform**: remote state in Azure Storage, blob lease locking, force-unlock, drift, import blocks, modules, plan in PR/apply in pipeline.

**5. Cost**: Cost analysis approach, budgets + anomaly alerts, tags + policy, Advisor, rightsizing, reservations vs savings plan, Log Analytics cost.

**6. Scalability**: scale up vs out, autoscale, AKS HPA + cluster autoscaler, caching, Front Door vs App Gateway vs Load Balancer, zones and DR.

## Most Important Production Scenarios to Rehearse

| **Scenario**                | **First three moves**                                                                                          |
|-----------------------------|----------------------------------------------------------------------------------------------------------------|
| App Service HTTP 500        | Check recent change → swap slot back if needed → App Insights Failures + end-to-end transaction                |
| VM CPU \> 90%               | Trend over 7 days → identify process (AMA/Run Command) → check recent changes/B-series credits                 |
| App Insights no data        | Connection string setting → network/AMPLS/egress → daily cap & sampling                                        |
| Cost spike                  | Cost analysis by service/resource, daily view → find change date → owner + fix + budget/anomaly alert          |
| Pipeline fails in prod only | Compare service connection & permissions → variables/Key Vault/secrets → network (private endpoints, firewall) |
| Expired SP secret           | AADSTS7000222 → new secret with --append, update connection → convert to workload identity federation          |
| Terraform lock              | Confirm no active run → terraform force-unlock \<ID\> → plan to verify                                         |
| AKS CrashLoopBackOff        | describe pod (exit code, events) → logs --previous → fix config/limits/probes                                  |
| AKS ImagePullBackOff        | Events: 401 vs not found → az aks check-acr → attach ACR / fix tag / DNS                                       |
| Private endpoint failure    | nslookup returns private IP? → zone linked to VNet? → custom DNS forwards to 168.63.129.16                     |
| App Gateway 502             | Backend health blade → NSG/UDR on AppGW subnet → probe path, certificate, timeout                              |

## Essential Commands to Remember

```bash
# Context

az login

az account set --subscription <sub-id>

az account show -o table

# RBAC

az role assignment list --assignee <upn-or-objectid> --all -o table

az role assignment create --assignee <object-id> --role "Reader" --scope /subscriptions/<sub-id>/resourceGroups/<rg>

# Monitoring

az monitor metrics list --resource <resource-id> --metric "Percentage CPU" --interval PT5M -o table

az monitor activity-log list --resource-group <rg> --offset 24h -o table

# App Service

az webapp log tail -g <rg> -n <app>

az webapp deployment slot swap -g <rg> -n <app> --slot staging --target-slot production

# AKS

az aks get-credentials -g <rg> -n <aks>

kubectl get pods -A

kubectl describe pod <pod> -n <ns>

kubectl logs <pod> -n <ns> --previous

kubectl rollout undo deployment/<name> -n <ns>

# Terraform

terraform init

terraform plan -out=tfplan

terraform apply tfplan

terraform force-unlock <LOCK_ID>

terraform state list
```

## Five KQL Queries to Write from Memory

```kusto
// 1. Failed requests by result code

AppRequests | where TimeGenerated > ago(1h) and Success == false

| summarize count() by ResultCode, OperationName

// 2. Latency percentiles over time

AppRequests | where TimeGenerated > ago(24h)

| summarize P95 = percentile(DurationMs, 95) by bin(TimeGenerated, 15m) | render timechart

// 3. Slow or failing dependencies

AppDependencies | where TimeGenerated > ago(1h)

| summarize P95 = percentile(DurationMs, 95), Failed = countif(Success == false) by Target

// 4. Who changed what (Activity Log in the workspace)

AzureActivity | where TimeGenerated > ago(24h) and ActivityStatusValue == "Success"

| where OperationNameValue endswith "/write" or OperationNameValue endswith "/delete"

| project TimeGenerated, Caller, OperationNameValue, ResourceGroup, _ResourceId

// 5. Billable ingestion by table

Usage | where TimeGenerated > ago(30d) and IsBillable

| summarize GB = sum(Quantity) / 1000 by DataType | order by GB desc
```

## Critical Azure Concepts — One-Line Definitions

| **Concept**                  | **One line**                                                                    |
|------------------------------|---------------------------------------------------------------------------------|
| Management group             | Container above subscriptions for policy and RBAC inheritance                   |
| Scope inheritance            | Roles assigned higher apply to everything below                                 |
| Deny assignment              | Blocks actions even if RBAC allows them (e.g., deployment stacks)               |
| PIM                          | Just-in-time, time-bound, approval-based role activation                        |
| Managed identity             | Azure-managed identity with no secrets; system- or user-assigned                |
| Workload identity federation | OIDC trust so pipelines/pods get tokens without secrets                         |
| Diagnostic setting           | Routes a resource's logs/metrics to Log Analytics, Storage or Event Hubs        |
| DCR                          | Data Collection Rule: what AMA collects and where; supports transformations     |
| Action group                 | Reusable list of notifications and automated actions for alerts                 |
| Alert processing rule        | Suppresses or adds action groups at scale (e.g., maintenance)                   |
| Workbook                     | Interactive parameterised report using KQL + metrics                            |
| Deployment slot              | Separate live app instance for staging and zero-downtime swap                   |
| HPA / cluster autoscaler     | Scales pods by metrics / scales nodes when pods can't be scheduled              |
| Availability zone            | Separate datacenter(s) in a region with independent power/cooling/network       |
| Private endpoint             | Private IP for a PaaS service in your VNet                                      |
| Azure Policy                 | Rules for what resources/configurations are allowed (Deny, Audit, Modify, DINE) |
| Terraform state lock         | Blob lease on the state file preventing concurrent applies                      |

## Common Interviewer Traps

| **Trap**                          | **Weak answer**                 | **Strong answer**                                                                                                |
|-----------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------|
| "Just give them Owner"            | "Yes, Owner fixes it."          | Use the least-privilege role — RBAC Administrator with conditions, or PIM.                                       |
| "Check the logs"                  | Generic "I'll check the logs."  | Name the exact blade, table and query: "Application Insights Failures, then AppExceptions grouped by ProblemId." |
| Daily cap as cost control         | "I'll set a daily cap."         | Cap stops collection — use sampling, DCR filtering, table plans; cap only as a safety net.                       |
| Debug first, mitigate later       | Investigate while users fail.   | Mitigate first (rollback/swap/scale), then root cause.                                                           |
| "Increase VM size" for everything | Scale up immediately.           | Find the bottleneck first; often it's the database or a dependency.                                              |
| Terraform state in Git            | "We commit state."              | Remote backend with locking, versioning, restricted access — state can contain secrets.                          |
| Secrets in pipeline variables     | "Stored as pipeline variables." | Managed identity / workload identity federation first; Key Vault for unavoidable secrets.                        |
| Claiming certainty                | Inventing a number or feature.  | "I'd confirm in the documentation, but my understanding is…"                                                     |
| Inventing experience              | Detailed fake story.            | Use "In a scenario like this, I would…" or a real smaller example you did.                                       |

## Prepare Your Own Three Stories (STAR)

Write short notes from **your real experience** for:

**1. A production incident** you helped resolve (Situation, Task, Action, Result — include a number: minutes of downtime, % errors).

**2. An improvement you drove** (automation, cost saving, pipeline, monitoring).

**3. A time you helped or mentored someone**, or disagreed and reached agreement.

Questions to ask the interviewer:

- "What does the current monitoring and alerting setup look like, and what's the biggest gap?"

- "How are Terraform and Bicep split today — is there a direction you're moving towards?"

- "What does on-call and incident management look like for the team?"

- "What would success look like for this role in the first 90 days?"

## 30-Minute Final Revision Checklist (Before the Interview)

- [ ] Re-read the answer framework: Clarify → Stabilise → Investigate → Fix → Prevent

- [ ] Say Q1 (Contributor can't assign roles) aloud in under 90 seconds

- [ ] Say Q3 (App Service 500s) aloud

- [ ] Say Q6 (cost spike) aloud

- [ ] Say Q8 (failed deployment rollback) aloud

- [ ] Recall: Owner / Contributor / Reader / User Access Administrator / RBAC Administrator

- [ ] Recall: alert types and action groups; dynamic thresholds; alert processing rules

- [ ] Recall: azurerm backend + blob lease locking + force-unlock

- [ ] Recall: AMA + DCR replaced MMA; workspace-based App Insights; connection string

- [ ] Recall: workload identity federation for service connections

- [ ] Recall: OOMKilled = exit 137; kubectl logs --previous

- [ ] Read your three STAR stories

- [ ] Have water, a notepad, and camera/microphone tested

- [ ] Remember: it's fine to pause and say "Let me think about that for a second."

# Part C — Interview Communication in Simple Professional English

## Principles

- **Short sentences.** One idea per sentence.

- **Signpost.** Tell them the structure: "I'd approach this in three steps."

- **Say "I", not "we", for your actions** — interviewers want to know what *you* did.

- **Use numbers** where you honestly can: "reduced alerts by about half", "within 15 minutes".

- **Pause, don't fill.** A two-second pause sounds confident; "umm, basically, actually" does not.

## How to Start a Troubleshooting Answer

- "Good question. I'd approach it in three stages: limit the impact, find the cause, then prevent it happening again."

- "Before I jump in, can I check one assumption — is this affecting all users or only some?"

- "The first thing I'd want to know is what changed. Most incidents follow a change."

## How to Structure an Incident Response Answer

> "First, I'd confirm the impact — how many users, which services. Second, I'd mitigate — for example roll back the deployment or fail over. Third, I'd communicate — an update in the incident channel and to stakeholders every 30 minutes. Fourth, once stable, I'd find the root cause using Application Insights and the Activity Log. Finally, I'd run a blameless post-incident review and track the actions."

## How to Explain a Production Deployment

> "Our deployments go through a multi-stage YAML pipeline. We build once and deploy the same artifact to each environment. Production uses an Azure DevOps environment with an approval and a branch check. We deploy to a staging slot, run smoke tests, then swap. If something goes wrong, we swap back — which takes less than a minute."

## How to Explain Azure Cost Optimisation

> "I treat cost like any other metric — I make it visible, I find the biggest drivers, and I fix them with the owners. Visible means tags and budgets. Drivers means Cost analysis grouped by service and resource. Fixing means rightsizing, removing idle resources, lifecycle policies, and commitment discounts for steady workloads. And I don't cut anything that hurts reliability or security without agreeing it with the service owner."

## How to Discuss Security and RBAC

> "My default is least privilege and no standing access in production. People get Reader, and they activate higher roles through PIM when they need them, with approval and a time limit. Applications and pipelines use managed identities or workload identity federation, so we don't store secrets. And Azure Policy enforces the guardrails, so mistakes are blocked automatically."

## How to Answer When You Don't Know Something

Never invent. Use one of these honest, still-useful patterns:

- "I haven't used that specific feature in production. How I would approach it is…"

- "I'm not 100% sure of the exact setting name, but the concept is… and I'd confirm it in the Microsoft documentation."

- "I haven't had that exact scenario, but I've handled something similar with… and I'd apply the same thinking."

- "I don't know, but I'd like to learn — could you tell me how your team uses it?" (Use rarely, for genuinely niche questions.)

## Communicating with UK-Based Engineering Teams

- **Be direct but polite.** UK colleagues often soften language: "That's an interesting idea" can mean "I have doubts". If unsure, ask: "Do you have any concerns with this approach?"

- **Confirm understanding in writing.** After a call: "Just to summarise what we agreed: …"

- **Time zones.** Always state times with the zone: "10:00 UK time / 15:30 IST" (GMT in winter, BST in summer).

- **Raise problems early.** "Quick heads-up — this might slip by a day because…" is valued more than late surprises.

- **Useful phrases:**

  - "Shall we take this offline?" — let's discuss separately.

  - "I'll pick this up." — I'll take ownership.

  - "Can I just check my understanding?"

  - "That's a fair point. My concern is…"

  - "I'll come back to you by end of day."

- **Async communication:** Clear Teams/Slack messages with context, the ask, and the deadline. Avoid sending only "Hi" and waiting.

## Phrases to Avoid

| **Avoid**                       | **Say instead**                                 |
|---------------------------------|-------------------------------------------------|
| "Basically…" at every sentence  | Start directly with the point                   |
| "We just give Owner access"     | "We grant the least-privilege role needed"      |
| "I will do the needful"         | "I'll take care of it"                          |
| "Revert back"                   | "Reply" or "get back to you"                    |
| "It's not my fault"             | "Here's what happened and how we'll prevent it" |
| "I know everything about Azure" | "I'm strong in X and Y, and I keep learning Z"  |

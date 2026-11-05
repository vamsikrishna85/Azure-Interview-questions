**Incidents, Cheat Sheet, Architecture & Mock Interview**

Sections 4–7: 20 production incidents, command reference, 10 architecture designs with diagrams, full mock interview

Senior Azure Cloud / DevOps Engineer — Interview Preparation Pack

All incidents and scenarios in this document are **illustrative examples** for interview practice. They are not claims about your personal work history. When you use them in the interview, frame them as "In a situation like this, I would…" or adapt them honestly to your own experience.

**Table of Contents**

*Click any entry to jump to that section.*

[**How to Use This Document**](#how-to-use-this-document)

[**Section 4 — 20 Advanced Production Incidents**](#section-4-20-advanced-production-incidents)

> [Incident 1 — Azure App Service Outage](#incident-1-azure-app-service-outage)
>
> [Incident 2 — Azure VM High CPU](#incident-2-azure-vm-high-cpu)
>
> [Incident 3 — Azure SQL Database Latency](#incident-3-azure-sql-database-latency)
>
> [Incident 4 — AKS CrashLoopBackOff](#incident-4-aks-crashloopbackoff)
>
> [Incident 5 — AKS ImagePullBackOff](#incident-5-aks-imagepullbackoff)
>
> [Incident 6 — Terraform State Locking](#incident-6-terraform-state-locking)
>
> [Incident 7 — Azure DevOps Pipeline Failure](#incident-7-azure-devops-pipeline-failure)
>
> [Incident 8 — Expired Service Principal Credentials](#incident-8-expired-service-principal-credentials)
>
> [Incident 9 — Azure RBAC Access Denied](#incident-9-azure-rbac-access-denied)
>
> [Incident 10 — Azure Key Vault Connectivity Failure](#incident-10-azure-key-vault-connectivity-failure)
>
> [Incident 11 — Application Insights Telemetry Missing](#incident-11-application-insights-telemetry-missing)
>
> [Incident 12 — Log Analytics Ingestion Failure](#incident-12-log-analytics-ingestion-failure)
>
> [Incident 13 — Azure Unexpected Cost Spike](#incident-13-azure-unexpected-cost-spike)
>
> [Incident 14 — Application Gateway 502 Errors](#incident-14-application-gateway-502-errors)
>
> [Incident 15 — Private Endpoint DNS Issues](#incident-15-private-endpoint-dns-issues)
>
> [Incident 16 — Autoscaling Failure](#incident-16-autoscaling-failure)
>
> [Incident 17 — Azure Container Registry Authentication Failure](#incident-17-azure-container-registry-authentication-failure)
>
> [Incident 18 — Production Deployment Rollback](#incident-18-production-deployment-rollback)
>
> [Incident 19 — Azure Networking Connectivity Failure](#incident-19-azure-networking-connectivity-failure)
>
> [Incident 20 — Azure Regional Outage and Disaster Recovery](#incident-20-azure-regional-outage-and-disaster-recovery)

[**Section 5 — Hands-On Commands Cheat Sheet**](#section-5-hands-on-commands-cheat-sheet)

> [Azure CLI](#azure-cli)
>
> [PowerShell (Az module)](#powershell-az-module)
>
> [kubectl](#kubectl)
>
> [Docker](#docker)
>
> [Terraform](#terraform)
>
> [KQL (Log Analytics / Application Insights)](#kql-log-analytics-application-insights)
>
> [Azure DevOps YAML — Reference Snippets](#azure-devops-yaml-reference-snippets)

[**Section 6 — Azure Architecture Design Questions**](#section-6-azure-architecture-design-questions)

> [Design 1 — Highly Available Web Application on Azure](#design-1-highly-available-web-application-on-azure)
>
> [Design 2 — Secure Azure Infrastructure for Multiple Environments](#design-2-secure-azure-infrastructure-for-multiple-environments)
>
> [Design 3 — Centralised Monitoring for 100+ Azure Resources](#design-3-centralised-monitoring-for-100-azure-resources)
>
> [Design 4 — Scalable AKS-Based Microservices Platform](#design-4-scalable-aks-based-microservices-platform)
>
> [Design 5 — Secure CI/CD Deployment Architecture](#design-5-secure-cicd-deployment-architecture)
>
> [Design 6 — Enterprise RBAC Model](#design-6-enterprise-rbac-model)
>
> [Design 7 — Cost-Efficient Infrastructure for Growing Workloads](#design-7-cost-efficient-infrastructure-for-growing-workloads)
>
> [Design 8 — Disaster Recovery Across Azure Regions](#design-8-disaster-recovery-across-azure-regions)
>
> [Design 9 — Terraform Module Architecture for Multiple Teams](#design-9-terraform-module-architecture-for-multiple-teams)
>
> [Design 10 — Secure Private Networking for Azure PaaS Services](#design-10-secure-private-networking-for-azure-paas-services)

[**Section 7 — Mock Interview: Senior Azure Cloud / DevOps Engineer**](#section-7-mock-interview-senior-azure-cloud-devops-engineer)

> [Part 1 — Technical Questions (15)](#part-1-technical-questions-15)
>
> [Part 2 — Troubleshooting Questions (10)](#part-2-troubleshooting-questions-10)
>
> [Part 3 — Architecture Questions (5)](#part-3-architecture-questions-5)
>
> [Part 4 — Behavioural and Leadership Questions (5)](#part-4-behavioural-and-leadership-questions-5)
>
> [Mock Interview Self-Scoring](#mock-interview-self-scoring)

# How to Use This Document

This document covers Sections 4–7: 20 production incident case studies, a hands-on command cheat sheet, 10 architecture design scenarios with diagrams, and a full mock interview.

> **All incidents below are hypothetical examples** created for interview practice. They are not your personal work history. In the interview, say "A typical case is…" or "If I saw this, I would…", or adapt honestly from your own experience.

**How to tell an incident story in an interview (STAR + Prevent):** Situation (what broke, impact) → Task (your role) → Action (first steps, tools, decisions) → Result (time to mitigate, numbers) → Prevention (what changed afterwards). Keep it to about 2 minutes.

# Section 4 — 20 Advanced Production Incidents

## Incident 1 — Azure App Service Outage

**Symptoms and alerts:** Availability test "orders-home" fails from 5/5 locations; metric alert Http5xx \> 50 in 5 min (Sev 1); App Service Requests drop and Http503 rises.

**Business impact:** Online ordering unavailable for UK customers; estimated revenue loss per minute; customer support calls increase.

**First five troubleshooting actions:**

**1.** Check **Azure Service Health** and **Resource Health** for the App Service — is it a platform incident?

**2.** Check recent changes: Deployment Center history, Activity Log (app settings, scale, restarts).

**3.** Open **Diagnose and solve problems → Availability and Performance** (shows 503 cause, crashes, memory).

**4. Log stream** / container logs — app failing to start? (e.g., port mismatch for containers, missing setting).

**5.** If a deployment caused it: **swap slots back** or redeploy the previous artifact.

**Azure tools and commands:**

**BASH**

az webapp show -g \<rg\> -n \<app\> --query "{state:state, hostNames:defaultHostName}"

az webapp log tail -g \<rg\> -n \<app\>

az monitor activity-log list -g \<rg\> --offset 2h --query "\[\].{time:eventTimestamp, op:operationName.value, who:caller}" -o table

az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --target-slot production

**Root cause investigation:** Container logs show Container didn't respond to HTTP pings on port: 80. The new image listens on 8080 (the .NET 8 default) but WEBSITES_PORT was not set.

**Immediate mitigation:** Swap back to the previous slot (service restored in ~2 minutes).

**Permanent resolution:** Set WEBSITES_PORT=8080 in IaC; redeploy via pipeline through the staging slot.

**Preventative monitoring:** Smoke test on staging slot before swap; Health check path enabled; alert on availability test failures (≥3 locations); deployment checklist for base image changes.

**How to explain in an interview:** "A typical example: a release upgraded the base image and the app started listening on a different port. App Service returned 503 because the container never answered the warm-up ping. We swapped back within two minutes, fixed the port setting in Terraform, and added a smoke test on the staging slot so the swap can't happen unless the app responds."

## Incident 2 — Azure VM High CPU

**Symptoms and alerts:** Dynamic threshold alert on Percentage CPU (Sev 2) for vm-api-01; API p95 latency rises from 300 ms to 2.5 s.

**Business impact:** Slow internal API affects order processing; no full outage.

**First five troubleshooting actions:**

**1.** Check CPU trend (7 days) — sudden or gradual?

**2.** Identify top process via **Run Command** or VM insights.

**3.** Check Activity Log / Update Manager / Change Analysis for recent changes.

**4.** Check request volume in App Insights — is load higher?

**5.** Check VM size family (B-series credits).

**Azure tools and commands:**

**BASH**

az vm run-command invoke -g \<rg\> -n vm-api-01 --command-id RunPowerShellScript \\

--scripts "Get-Process \| Sort CPU -Desc \| Select -First 5 Name,Id,CPU"

az monitor metrics list --resource \<vm-id\> --metric "Percentage CPU" --interval PT1H --offset 7d -o table

**KQL**

Perf

\| where Computer == "vm-api-01" and CounterName == "% Processor Time" and TimeGenerated \> ago(7d)

\| summarize avg(CounterValue) by bin(TimeGenerated, 1h), InstanceName

**Root cause investigation:** w3wp.exe at 85%. App Insights Profiler shows a regex in a new validation function with catastrophic backtracking for certain inputs.

**Immediate mitigation:** Add a second VM to the load balancer pool; recycle the app pool; disable the new validation via feature flag.

**Permanent resolution:** Fix the regex (with timeout), add unit tests with malicious inputs; move API to a VM Scale Set with autoscale.

**Preventative monitoring:** CPU dynamic threshold + latency SLO alert; profiler enabled; performance tests in pipeline.

**How to explain:** "I'd show the method: trend, process, change correlation, then code-level profiling. In this example the CPU came from one inefficient regex, so scaling up would only have hidden it."

## Incident 3 — Azure SQL Database Latency

**Symptoms and alerts:** Log alert: AppDependencies SQL p95 \> 1 s; DTU consumption 100% for 20 minutes.

**Business impact:** Checkout slow; 8% of orders time out.

**First five troubleshooting actions:**

**1.** SQL metrics: CPU, Data IO, Log IO, workers, sessions.

**2. Query Performance Insight** / Query Store: top queries now vs yesterday.

**3.** Check for plan regressions (multiple plans for same query).

**4.** Check blocking (sys.dm_exec_requests).

**5.** Check recent deployments or data loads (Activity Log, release notes).

**Azure tools and commands:**

**SQL**

SELECT TOP 5 qs.query_id, p.plan_id, rs.avg_duration/1000 AS avg_ms, rs.count_executions

FROM sys.query_store_runtime_stats rs

JOIN sys.query_store_plan p ON p.plan_id = rs.plan_id

JOIN sys.query_store_query qs ON qs.query_id = p.query_id

ORDER BY rs.avg_duration DESC;

**BASH**

az sql db show -g \<rg\> -s \<server\> -n orders --query "{sku:currentSku.name, cap:currentSku.capacity}"

az sql db update -g \<rg\> -s \<server\> -n orders --service-objective S6 \# temporary scale

**Root cause investigation:** Query Store shows query 4711 switched to a new plan with a clustered index scan after statistics auto-update; parameter sniffing on a customer with few rows created a bad plan for large customers.

**Immediate mitigation:** Force the previous good plan (sp_query_store_force_plan); temporarily scale up.

**Permanent resolution:** Add a covering index; enable automatic tuning FORCE_LAST_GOOD_PLAN; review query parameterisation.

**Preventative monitoring:** Alerts on DTU/CPU \> 80% for 10 min; dependency latency SLO; Query Store regression reviews.

**How to explain:** "Sudden SQL slowness without a release is often a plan regression. Query Store lets you prove it and force the good plan in minutes, then fix properly with an index."

## Incident 4 — AKS CrashLoopBackOff

**Symptoms and alerts:** Prometheus alert KubePodCrashLooping for payments-api; readiness failing; error rate up.

**Business impact:** Payments degraded — half the replicas unavailable.

**First five troubleshooting actions:**

**1.** kubectl get pods -n payments — restarts, status.

**2.** kubectl describe pod — Last State, exit code, Events.

**3.** kubectl logs --previous — crash output.

**4.** Check recent rollout (kubectl rollout history) and config changes (ConfigMap/Secret).

**5.** Check node resource pressure and OOM events.

**Azure tools and commands:**

**BASH**

kubectl get pods -n payments

kubectl describe pod payments-api-7d9f-abcde -n payments

kubectl logs payments-api-7d9f-abcde -n payments --previous

kubectl rollout history deployment/payments-api -n payments

kubectl get events -n payments --sort-by=.lastTimestamp \| tail -20

**Root cause investigation:** Exit code 1; logs: Unhandled exception: Value cannot be null (Parameter 'connectionString'). A new SecretProviderClass object name typo meant the secret wasn't mounted.

**Immediate mitigation:** kubectl rollout undo deployment/payments-api -n payments.

**Permanent resolution:** Fix SecretProviderClass name; add startup validation that logs clearly which configuration is missing; Helm chart test.

**Preventative monitoring:** Alert on restarts \> 3 in 15 min; deploy with helm --atomic; config validation in CI (kubeconform, policy checks).

**How to explain:** "Describe for the exit code, logs --previous for the reason, rollback for mitigation. Exit 137 points to memory; exit 1 points to the app — here, missing configuration."

## Incident 5 — AKS ImagePullBackOff

**Symptoms and alerts:** New deployment stuck; pods ImagePullBackOff; KubeDeploymentReplicasMismatch alert.

**Business impact:** Release blocked; existing pods still serving (rolling update protected users).

**First five troubleshooting actions:**

**1.** kubectl describe pod → Events error text.

**2.** Classify: 401 unauthorized / not found / timeout / DNS.

**3.** az aks check-acr.

**4.** Verify image tag exists: az acr repository show-tags.

**5.** Check ACR networking/DNS from cluster.

**Azure tools and commands:**

**BASH**

kubectl describe pod \<pod\> -n orders \| grep -A3 "Failed"

az acr repository show-tags -n \<acr\> --repository orders-api --orderby time_desc --top 5 -o table

az aks check-acr -g \<rg\> -n \<aks\> --acr \<acr\>.azurecr.io

az role assignment list --assignee \$(az aks show -g \<rg\> -n \<aks\> --query identityProfile.kubeletidentity.objectId -o tsv) --all -o table

**Root cause investigation:** Error: 401 Unauthorized. The cluster was recreated by Terraform last week with a new kubelet identity; the AcrPull role assignment referenced the old identity.

**Immediate mitigation:** az aks update --attach-acr \<acr\>.

**Permanent resolution:** Terraform role assignment references azurerm_kubernetes_cluster.this.kubelet_identity\[0\].object_id so it follows recreation.

**Preventative monitoring:** Post-provision test that runs check-acr; alert on ImagePullBackOff events.

**How to explain:** "The error text decides the path: 401 is identity, not found is tag, timeout is network. Here it was identity after cluster recreation."

## Incident 6 — Terraform State Locking

**Symptoms and alerts:** Pipeline fails: Error acquiring the state lock … state blob is already locked.

**Business impact:** Infra changes blocked, including an urgent firewall rule.

**First five troubleshooting actions:**

**1.** Read lock info (ID, Who, Operation, Created).

**2.** Check whether that run/agent/person is still active.

**3.** Check pipeline history for cancelled/timed-out runs.

**4.** Confirm no apply is running (Activity Log for in-progress writes by pipeline identity).

**5.** If safe, terraform force-unlock \<ID\>; then plan.

**Azure tools and commands:**

**BASH**

terraform force-unlock 6a7c1e2f-0000-1111-2222-333344445555

az storage blob show --account-name \<sa\> -c tfstate -n network/prod.tfstate --auth-mode login --query properties.lease

terraform plan -out=tfplan

**Root cause investigation:** A previous run was cancelled during apply when the agent timed out at 60 minutes (App Gateway update took longer).

**Immediate mitigation:** Force-unlock after confirming; plan shows App Gateway partially updated; re-apply.

**Permanent resolution:** Increase job timeout; split App Gateway into separate state; -lock-timeout=10m.

**Preventative monitoring:** Pipeline exclusive lock check; alert on failed infra pipelines.

**How to explain:** "Locks protect state, so never force-unlock blindly. Confirm the holder is dead, unlock, then plan to see the true state before applying."

## Incident 7 — Azure DevOps Pipeline Failure

**Symptoms and alerts:** All builds failing since 10:00 at the restore step: NU1301: Unable to load the service index for source https://pkgs.dev.azure.com/org/\_packaging/internal/nuget/v3/index.json (401). Service hook posts repeated failures to Teams.

**Business impact:** No builds or releases; hotfix delayed.

**First five troubleshooting actions:**

**1.** Is it all pipelines or one? Same step?

**2.** Check Azure DevOps status page and Service Health.

**3.** Compare last successful run: agent image version, task versions, changes.

**4.** Check feed permissions for the build service identity.

**5.** Re-run with system.debug=true.

**Azure tools and commands:**

**YAML**

variables:

system.debug: true

steps:

\- task: NuGetAuthenticate@1

\- script: dotnet restore --verbosity detailed

**Root cause investigation:** The feed was moved to a different project; the project build service identity lacked Feed Reader on the new feed.

**Immediate mitigation:** Grant Project Collection Build Service / project build service **Feed and Upstream Reader (Collaborator)** on the feed.

**Permanent resolution:** Document feed permissions; feed changes through change process.

**Preventative monitoring:** Alert on consecutive pipeline failures (Azure DevOps service hooks → Teams).

**How to explain:** "Widespread failure at the same step after a change outside the code — permissions or platform. Debug logs plus last-good comparison find it quickly."

## Incident 8 — Expired Service Principal Credentials

**Symptoms and alerts:** Deploy stage fails: AADSTS7000222: The provided client secret keys are expired. A scheduled Logic App also stops syncing data.

**Business impact:** Releases blocked; nightly data sync failed.

**First five troubleshooting actions:**

**1.** Identify app ID from the error/service connection.

**2.** Check credential expiry (az ad app credential list).

**3.** Find all consumers of that SP (service connections, Key Vault, app settings).

**4.** Create new secret with --append; update consumers.

**5.** Re-run failed jobs.

**Azure tools and commands:**

**BASH**

az ad app credential list --id \<app-id\> -o table

az ad app credential reset --id \<app-id\> --append --display-name "rotation-2026-11" --years 1

az keyvault secret set --vault-name \<kv\> -n sp-sync-secret --value "\<new-secret\>"

**Root cause investigation:** Secret created 2 years ago with 24-month expiry; no owner; no monitoring.

**Immediate mitigation:** New secret, update service connection and Key Vault; restart Logic App runs.

**Permanent resolution:** Convert service connection to workload identity federation; Logic App to managed identity.

**Preventative monitoring:** Weekly Graph script alerting on credentials expiring within 30 days; app owners assigned.

**How to explain:** "Fix fast with an appended secret, then remove the secret entirely with federation or managed identity."

## Incident 9 — Azure RBAC Access Denied

**Symptoms and alerts:** On-call engineer can't restart a production App Service during an incident: AuthorizationFailed … does not have authorization to perform action 'Microsoft.Web/sites/restart/action'.

**Business impact:** Mitigation delayed during an active incident.

**First five troubleshooting actions:**

**1.** Read the exact error (action, scope).

**2.** Check access (portal) for the user at that scope.

**3.** Is the role eligible in PIM but not activated?

**4.** Check deny assignments / locks (ScopeLocked is different).

**5.** Use the break-glass or on-call operator path if urgent.

**Azure tools and commands:**

**BASH**

az role assignment list --assignee \<upn\> --all --include-inherited -o table

az lock list -g \<rg\> -o table

**Root cause investigation:** PIM role activation required approval; the approver was asleep (UK night).

**Immediate mitigation:** Second approver from on-call rota approved; restart performed.

**Permanent resolution:** On-call group gets an "Operator" custom role (restart/scale only) eligible **without approval** but with MFA and justification; Owner still requires approval.

**Preventative monitoring:** PIM activation dashboards; quarterly review of on-call access paths; game day testing access.

**How to explain:** "Least privilege must still let on-call act fast. I separated low-risk operational actions from high-risk ones in PIM."

## Incident 10 — Azure Key Vault Connectivity Failure

**Symptoms and alerts:** App Service Key Vault references show error status; app throws Azure.RequestFailedException: … 403 ForbiddenByFirewall.

**Business impact:** Login service down (can't read signing key).

**First five troubleshooting actions:**

**1.** App Service → Configuration → Key Vault reference status message.

**2.** Key Vault → Networking: public access / firewall changes? (Activity Log)

**3.** nslookup vault name from Kudu — private or public IP?

**4.** Check private DNS zone links and records.

**5.** Check the identity's RBAC (if error is Forbidden, not firewall).

**Azure tools and commands:**

**BASH**

az keyvault show -n \<kv\> --query "properties.{public:publicNetworkAccess, acls:networkAcls}"

\# Kudu console:

nameresolver kv-login-prod.vault.azure.net

az network private-dns link vnet list -g rg-dns -z privatelink.vaultcore.azure.net -o table

**Root cause investigation:** Security disabled public access on the vault (correct change), but the App Service's VNet integration subnet's VNet wasn't linked to privatelink.vaultcore.azure.net, so it resolved the public IP.

**Immediate mitigation:** Link the private DNS zone to the spoke VNet (or re-enable firewall allow temporarily with approval).

**Permanent resolution:** Central DNS zones linked via policy; network change checklist includes DNS validation; WEBSITE_DNS_SERVER / route-all configuration reviewed.

**Preventative monitoring:** Alert on Key Vault 403s; synthetic test reading a canary secret from each app.

**How to explain:** "Private endpoint problems are DNS problems until proven otherwise. nslookup told us immediately the app was still resolving the public IP."

## Incident 11 — Application Insights Telemetry Missing

**Symptoms and alerts:** Workbook panels empty; log alert "No requests in 15 minutes" fires, but synthetic tests pass.

**Business impact:** Blind monitoring — no customer impact yet, but high risk.

**First five troubleshooting actions:**

**1.** Live Metrics — is the app sending?

**2.** Check APPLICATIONINSIGHTS_CONNECTION_STRING setting.

**3.** Check App Insights resource local auth / ingestion settings.

**4.** Check workspace daily cap and \_LogOperation.

**5.** Check network (AMPLS mode, outbound firewall).

**Azure tools and commands:**

**BASH**

az webapp config appsettings list -g \<rg\> -n \<app\> --query "\[?contains(name,'APPLICATIONINSIGHTS')\]"

az monitor app-insights component show -g \<rg\> -a \<appi\> --query "{disableLocalAuth:disableLocalAuth}"

**KQL**

\_LogOperation \| where TimeGenerated \> ago(1d) \| where Category == "Ingestion" \| take 20

**Root cause investigation:** Security enabled DisableLocalAuth on App Insights (policy); the app's SDK wasn't configured for Entra ID authentication, so ingestion was rejected.

**Immediate mitigation:** Temporarily allow local auth (with security approval) while app config updated.

**Permanent resolution:** Configure SDK/OTel credential (DefaultAzureCredential with managed identity) and grant **Monitoring Metrics Publisher** to the app identity; re-disable local auth.

**Preventative monitoring:** "No telemetry" alert per app; policy rollout process includes app teams.

**How to explain:** "Telemetry loss is an incident too. Live Metrics separated 'app not sending' from 'ingestion rejected'."

## Incident 12 — Log Analytics Ingestion Failure

**Symptoms and alerts:** Several alert rules stop firing; Heartbeat gaps across all VMs from 13:00.

**Business impact:** Monitoring blind spot across production.

**First five troubleshooting actions:**

**1.** Scope: all sources or some? (Heartbeat, AzureDiagnostics, AppRequests)

**2.** Service Health for Azure Monitor in the region.

**3.** \_LogOperation for daily cap / ingestion errors.

**4.** Workspace settings changes (Activity Log).

**5.** DCR changes (transformations) for affected sources.

**Azure tools and commands:**

**KQL**

union Heartbeat, AzureDiagnostics, AppRequests

\| where TimeGenerated \> ago(6h)

\| summarize count() by Type, bin(TimeGenerated, 15m)

\| render timechart

\_LogOperation \| where TimeGenerated \> ago(1d) and Detail has "cap"

**BASH**

az monitor log-analytics workspace show -g \<rg\> -n \<law\> --query "workspaceCapping"

**Root cause investigation:** A cost-saving change set the daily cap to 50 GB; cap reached at 13:00.

**Immediate mitigation:** Raise/remove the cap (data during the gap is lost).

**Permanent resolution:** Remove cap for production workspace; implement real cost controls (DCR filters, table plans); cap only on non-prod.

**Preventative monitoring:** Alert at 80% of daily cap; Activity Log alert on workspace setting changes.

**How to explain:** "Daily cap is a safety net that drops data. I'd explain why it's the wrong cost tool for production."

## Incident 13 — Azure Unexpected Cost Spike

**Symptoms and alerts:** Cost anomaly alert: daily cost +\$1,900 on sub-data-prod; forecast budget alert 140%.

**Business impact:** ~\$57k/month projected overspend.

**First five troubleshooting actions:**

**1.** Cost analysis daily view → service → resource → meter.

**2.** Activity Log for creation/scaling on that date.

**3.** Check reservations expiry/utilisation.

**4.** Contact owner (tags).

**5.** Decide immediate action (stop/scale down) with owner.

**Azure tools and commands:**

**BASH**

az consumption usage list --start-date 2026-11-01 --end-date 2026-11-05 \\

--query "sort_by(\[\], &pretaxCost)\[-10:\].{res:instanceName, cost:pretaxCost, meter:meterDetails.meterName}" -o table

**Root cause investigation:** Cost analysis shows "Bandwidth – Inter-Region" meter. A new data pipeline copies 30 TB/day from UK South storage to a Databricks workspace in West Europe.

**Immediate mitigation:** Pause the pipeline schedule (owner approved).

**Permanent resolution:** Move compute to the same region as data; policy "allowed locations"; architecture review for cross-region data flows.

**Preventative monitoring:** Anomaly alerts per subscription; budgets per RG; egress metric alerts on storage.

**How to explain:** "Group by meter, not just service — egress hides inside 'Bandwidth'. Then fix architecture, not just the bill."

## Incident 14 — Application Gateway 502 Errors

**Symptoms and alerts:** Metric UnhealthyHostCount \> 0; 100% 502s from App Gateway WAF v2.

**Business impact:** Customer portal down.

**First five troubleshooting actions:**

**1. Backend health** blade — reason text.

**2.** Access logs: serverStatus, serverRouted, timeTaken.

**3.** Probe settings vs backend (path, host, status code).

**4.** Certificates (backend cert CN/SAN, expiry).

**5.** NSG/UDR on AppGW subnet (recent changes).

**Azure tools and commands:**

**BASH**

az network application-gateway show-backend-health -g \<rg\> -n \<agw\> -o json \| jq '..\|.healthProbeLog? // empty'

**KQL**

AGWAccessLogs

\| where TimeGenerated \> ago(30m)

\| summarize count() by HttpStatus, ServerStatus, ServerRouted

**Root cause investigation:** Backend health: "The Common Name (CN) of the backend server certificate does not match the host header". The backend App Service got a new custom domain certificate; App Gateway backend setting overrides the host name to the old domain.

**Immediate mitigation:** Enable "Pick host name from backend target" / correct host name override.

**Permanent resolution:** Backend settings in IaC aligned with app custom domains; certificate changes include App Gateway review.

**Preventative monitoring:** Alert on UnhealthyHostCount; synthetic test through App Gateway.

**How to explain:** "502 at App Gateway: backend health tells you why. Most often probe, host header or certificate."

## Incident 15 — Private Endpoint DNS Issues

**Symptoms and alerts:** After migration to private endpoints, a Function App fails storage triggers: No such host is known / timeouts.

**Business impact:** File processing pipeline stopped.

**First five troubleshooting actions:**

**1.** nameresolver \<account\>.blob.core.windows.net from Kudu.

**2.** Check private endpoints exist for **all** required sub-resources (blob, queue, table, file).

**3.** Check DNS zone records exist for each.

**4.** Check zone links to the Function's integration VNet (or hub with custom DNS forwarding).

**5.** Check Function app setting WEBSITE_CONTENTOVERVNET/route-all and storage firewall.

**Azure tools and commands:**

**BASH**

az network private-endpoint list -g \<rg\> --query "\[\].{name:name, groups:privateLinkServiceConnections\[0\].groupIds}" -o table

az network private-dns record-set a list -g rg-dns -z privatelink.queue.core.windows.net -o table

**Root cause investigation:** Only a blob private endpoint was created; Functions storage triggers and runtime also need queue and table (and file for content share on some plans).

**Immediate mitigation:** Create queue/table/file private endpoints and DNS records.

**Permanent resolution:** Storage module creates all required sub-resource endpoints when private = true; documentation for Functions networking.

**Preventative monitoring:** Function host health alerts; synthetic file drop test.

**How to explain:** "A private endpoint covers one sub-resource. Functions needs more than blob — and DNS for each."

## Incident 16 — Autoscaling Failure

**Symptoms and alerts:** Black Friday morning: App Service CPU 95%, instances stuck at 10 (the max), queue length rising; latency SLO alert.

**Business impact:** Slow checkout during peak sales.

**First five troubleshooting actions:**

**1.** Autoscale **run history** — evaluated? "at max"?

**2.** Check plan's maximum instances for the SKU.

**3.** Check metric used vs actual bottleneck.

**4.** Check downstream (SQL DTU) — will more instances help?

**5.** Manually scale if safe.

**Azure tools and commands:**

**BASH**

az monitor autoscale show -g \<rg\> -n \<autoscale\> --query "profiles\[\].capacity"

az monitor autoscale update -g \<rg\> -n \<autoscale\> --max-count 25

az appservice plan update -g \<rg\> -n \<plan\> --number-of-workers 20

**Root cause investigation:** Autoscale max was 10 (set a year earlier); SQL had headroom.

**Immediate mitigation:** Raise max to 25 and scale out to 20 manually.

**Permanent resolution:** Capacity plan before peak events; scheduled profile pre-scaling; alert when autoscale reaches max.

**Preventative monitoring:** Activity Log alert / autoscale notification on "reached maximum"; annual peak load test.

**How to explain:** "Autoscale was working — it hit its limit. The fix was capacity planning and alerting on 'at max'."

## Incident 17 — Azure Container Registry Authentication Failure

**Symptoms and alerts:** CI pipeline push fails: unauthorized: authentication required; also pulls in a GitHub Actions workflow fail.

**Business impact:** No new images; releases blocked.

**First five troubleshooting actions:**

**1.** Which identity is pushing? (service connection / workflow identity)

**2.** Check its role on ACR (AcrPush).

**3.** Check ACR network rules (public access disabled? agent IPs?).

**4.** Check ACR changes in Activity Log (admin user disabled? token deleted?).

**5.** Test az acr login from the agent.

**Azure tools and commands:**

**BASH**

az acr login -n \<acr\> \# uses current Azure CLI identity

az acr show -n \<acr\> --query "{admin:adminUserEnabled, public:publicNetworkAccess}"

az role assignment list --scope \$(az acr show -n \<acr\> --query id -o tsv) -o table

**Root cause investigation:** Security disabled the ACR admin user (correct). The Docker registry service connection used admin credentials.

**Immediate mitigation:** Create new Docker Registry service connection using Azure Resource Manager + workload identity federation; grant AcrPush to it.

**Permanent resolution:** Remove all admin-credential usage; GitHub Actions use OIDC with AcrPush.

**Preventative monitoring:** Policy "Container registries should have local admin account disabled" in audit first; inventory consumers before enforcing.

**How to explain:** "The security change was right; we hadn't inventoried who used the credential. Identity-based auth fixed it permanently."

## Incident 18 — Production Deployment Rollback

**Symptoms and alerts:** 10 minutes after release, error rate 6% on /api/basket; canary analysis flagged but promotion was manual and approved anyway.

**Business impact:** ~6% of basket operations failed for 25 minutes.

**First five troubleshooting actions:**

**1.** Confirm correlation with release (App Insights by app version).

**2.** Decide rollback (impact ongoing).

**3.** Execute rollback (Helm rollback / slot swap).

**4.** Verify recovery with same metrics.

**5.** Communicate; preserve logs.

**Azure tools and commands:**

**BASH**

helm history basket -n shop

helm rollback basket 0 -n shop --wait

kubectl rollout status deployment/basket -n shop

**KQL**

AppRequests

\| where TimeGenerated \> ago(1h) and Name has "basket"

\| summarize FailPct = 100.0 \* countif(Success == false) / count() by tostring(Properties.AppVersion), bin(TimeGenerated, 5m)

**Root cause investigation:** New version serialised dates differently; older mobile clients sent a format the new API rejected.

**Immediate mitigation:** Rollback (recovered in 4 minutes).

**Permanent resolution:** Contract tests for API compatibility with older client versions; tolerant parsing.

**Preventative monitoring:** Automated canary analysis that blocks promotion (no manual override without incident commander approval).

**How to explain:** "We had a signal but a human overrode it. The improvement was automating the decision and adding contract tests."

## Incident 19 — Azure Networking Connectivity Failure

**Symptoms and alerts:** Multiple apps in spoke VNets can't reach on-premises APIs; VPN gateway metric TunnelIngressBytes drops to zero.

**Business impact:** Integrations with on-prem ERP fail; orders queue up.

**First five troubleshooting actions:**

**1.** Check VPN connection status and Resource Health.

**2.** Check on-prem device changes (with network team).

**3.** Check BGP peers/learned routes on gateway.

**4.** Check effective routes in a spoke (are on-prem prefixes present?).

**5.** Network Watcher **VPN troubleshoot** / connection troubleshoot.

**Azure tools and commands:**

**BASH**

az network vpn-connection show -g rg-hub -n cn-onprem --query "{status:connectionStatus, in:ingressBytesTransferred}"

az network vnet-gateway list-bgp-peer-status -g rg-hub -n vpngw-hub -o table

az network vnet-gateway list-learned-routes -g rg-hub -n vpngw-hub -o table

az network nic show-effective-route-table -g \<spoke-rg\> -n \<nic\> -o table

az network watcher troubleshooting start -g rg-hub --resource vpngw-hub --resource-type vnetGateway \\

--storage-account \<sa-id\> --storage-path https://\<sa\>.blob.core.windows.net/vpntroubleshoot

**Root cause investigation:** On-prem firewall team rotated the pre-shared key during maintenance; Azure side not updated. Tunnel down.

**Immediate mitigation:** Update shared key on the Azure connection (coordinated).

**Permanent resolution:** Change process with joint approval; second tunnel/active-active gateway; ExpressRoute with VPN as backup.

**Preventative monitoring:** Alert on TunnelIngressBytes == 0 for 5 min and connection status; BGP peer status alert.

**How to explain:** "Work layer by layer: tunnel → BGP routes → effective routes → NSG/firewall. Here it failed at the tunnel because of an uncoordinated change."

## Incident 20 — Azure Regional Outage and Disaster Recovery

**Symptoms and alerts:** Service Health: major incident affecting multiple services in UK South; Front Door health probes fail for primary origins; SQL failover group primary unreachable.

**Business impact:** Full outage of order platform in primary region.

**First five troubleshooting actions:**

**1.** Confirm via Service Health scope and expected duration.

**2.** Declare DR per runbook (incident commander + business owner decision).

**3.** Fail over SQL failover group to secondary.

**4.** Ensure Front Door routes to secondary origins (automatic on probes) and scale secondary.

**5.** Validate end-to-end, communicate status.

**Azure tools and commands:**

**BASH**

az sql failover-group set-primary -g rg-orders-ukw -s sql-orders-ukw -n fog-orders --allow-data-loss \# forced, only if primary is down

az appservice plan update -g rg-orders-ukw -n plan-orders-ukw --number-of-workers 10

az afd origin show -g rg-edge --profile-name afd-shop --origin-group-name og-web --origin-name ukw --query enabledState

az storage account failover -n \<sa\> -g \<rg\> \# customer-managed failover, only if needed

**Root cause investigation:** Platform incident (Microsoft's RCA via Service Health). Our analysis: RTO achieved 48 minutes vs target 60; RPO ~10 seconds of SQL transactions.

**Immediate mitigation:** DR failover.

**Permanent resolution:** Failback after primary recovery in a planned window; review runbook gaps (e.g., one service had secrets only in primary Key Vault).

**Preventative monitoring:** Service Health alerts for our regions; quarterly DR drills; secondary region health dashboards.

**How to explain:** "The value was preparation: tested runbook, IaC for both regions, and clear decision rights. The review found one secret not replicated, which we fixed."

# Section 5 — Hands-On Commands Cheat Sheet

Placeholders: \<sub-id\>, \<rg\>, \<app\>, \<vm\>, \<aks\>, \<acr\>, \<kv\>, \<law\> etc. Replace before use. Never paste real secrets into commands that are logged.

## Azure CLI

| **Command**                                                                                  | **What it does**                  | **When to use**                               | **Expected output**                  |
|----------------------------------------------------------------------------------------------|-----------------------------------|-----------------------------------------------|--------------------------------------|
| az login / az login --identity                                                               | Sign in (user / managed identity) | Start of session; on Azure VMs/agents with MI | List of subscriptions (JSON)         |
| az account set --subscription \<sub-id\>                                                     | Select subscription               | Before any resource command                   | No output on success                 |
| az account show -o table                                                                     | Show current context              | Confirm you're in the right subscription      | Name, ID, tenant                     |
| az group list -o table                                                                       | List resource groups              | Orientation                                   | Table of RGs and locations           |
| az resource list -g \<rg\> -o table                                                          | List resources in RG              | Inventory                                     | Name, type, location                 |
| az role assignment list --assignee \<upn\> --all --include-inherited -o table                | Show a user's roles everywhere    | RBAC troubleshooting                          | Principal, role, scope               |
| az role assignment create --assignee \<id\> --role "Reader" --scope \<scope\>                | Assign a role                     | Grant access (prefer groups)                  | JSON of assignment                   |
| az role definition list --name "Contributor"                                                 | Show role definition              | Explain Actions/NotActions                    | JSON with permissions                |
| az ad app credential list --id \<app-id\> -o table                                           | List SP secrets/certs and expiry  | Expired credential issues                     | Display name, end date               |
| az monitor metrics list --resource \<id\> --metric "Percentage CPU" --interval PT5M          | Read platform metrics             | Quick performance checks                      | Time series values                   |
| az monitor activity-log list -g \<rg\> --offset 24h -o table                                 | Recent control-plane operations   | "What changed?"                               | Operation, caller, status            |
| az monitor diagnostic-settings list --resource \<id\> -o table                               | Show diagnostic settings          | Missing logs                                  | Setting name, destinations           |
| az monitor log-analytics query -w \<workspace-guid\> --analytics-query "\<KQL\>"             | Run KQL from CLI                  | Scripts/automation                            | JSON rows                            |
| az webapp log tail -g \<rg\> -n \<app\>                                                      | Stream App Service logs           | Live debugging                                | Log lines                            |
| az webapp config appsettings list -g \<rg\> -n \<app\> -o table                              | Show app settings                 | Config drift / missing settings               | Name/value (values may be sensitive) |
| az webapp deployment slot swap -g \<rg\> -n \<app\> --slot staging --target-slot production  | Swap slots                        | Release or rollback                           | No output; swap completes            |
| az vm run-command invoke -g \<rg\> -n \<vm\> --command-id RunShellScript --scripts "\<cmd\>" | Run a command inside VM           | No SSH/RDP access                             | stdout/stderr in JSON                |
| az vm list -d -o table                                                                       | VMs with power state              | Find running/idle VMs                         | Name, state, IPs                     |
| az aks get-credentials -g \<rg\> -n \<aks\>                                                  | Merge kubeconfig                  | Before kubectl                                | "Merged ... as current context"      |
| az aks check-acr -g \<rg\> -n \<aks\> --acr \<acr\>.azurecr.io                               | Validate ACR pull from AKS        | ImagePullBackOff                              | Checks pass/fail summary             |
| az aks update -g \<rg\> -n \<aks\> --attach-acr \<acr\>                                      | Grant AcrPull to kubelet          | Set up/fix pulls                              | JSON of cluster                      |
| az acr repository show-tags -n \<acr\> --repository \<repo\> -o table                        | List image tags                   | Verify image exists                           | Tag list                             |
| az keyvault secret show --vault-name \<kv\> -n \<name\> --query id                           | Show secret metadata/id           | Verify existence (avoid printing value)       | Secret ID URL                        |
| az network watcher test-ip-flow ...                                                          | Check NSG allow/deny for a flow   | Connectivity issues                           | Access: Allow/Deny + rule name       |
| az network nic show-effective-route-table -g \<rg\> -n \<nic\> -o table                      | Effective routes                  | Routing problems                              | Prefix, next hop                     |
| az network private-dns link vnet list -g \<rg\> -z \<zone\> -o table                         | Private DNS zone links            | Private endpoint DNS                          | Linked VNets                         |
| az policy state summarize --subscription \<sub-id\>                                          | Policy compliance summary         | Governance checks                             | Non-compliant counts                 |
| az advisor recommendation list --category Cost -o table                                      | Cost recommendations              | Cost reviews                                  | Impact, problem, resource            |
| az graph query -q "\<ARG query\>"                                                            | Resource Graph query              | Estate-wide inventory                         | JSON rows                            |

## PowerShell (Az module)

| **Command**                                                                                                                                                    | **What it does**        | **When to use**         | **Expected output**       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|-------------------------|---------------------------|
| Connect-AzAccount / Connect-AzAccount -Identity                                                                                                                | Sign in                 | Start of script         | Account/tenant context    |
| Set-AzContext -Subscription \<sub-id\>                                                                                                                         | Select subscription     | Before work             | Context object            |
| Get-AzRoleAssignment -SignInName \<upn\>                                                                                                                       | User's role assignments | RBAC checks             | RoleDefinitionName, Scope |
| New-AzRoleAssignment -ObjectId \<id\> -RoleDefinitionName Reader -Scope \<scope\>                                                                              | Assign role             | Grant access            | Assignment object         |
| Get-AzVM -Status \| Select Name, PowerState                                                                                                                    | VMs and power state     | Idle VM review          | Table                     |
| Invoke-AzVMRunCommand -ResourceGroupName \<rg\> -VMName \<vm\> -CommandId RunPowerShellScript -ScriptString 'Get-Process \| Sort CPU -Desc \| Select -First 5' | Run script in VM        | CPU investigation       | Output text               |
| Get-AzWebApp -ResourceGroupName \<rg\> -Name \<app\>                                                                                                           | App Service details     | Config checks           | WebApp object             |
| Switch-AzWebAppSlot -ResourceGroupName \<rg\> -Name \<app\> -SourceSlotName staging -DestinationSlotName production                                            | Swap slots              | Release/rollback        | Completion                |
| Invoke-AzOperationalInsightsQuery -WorkspaceId \<guid\> -Query '\<KQL\>'                                                                                       | Run KQL                 | Automation/reports      | .Results rows             |
| Get-AzConsumptionUsageDetail -StartDate 2026-11-01 -EndDate 2026-11-05                                                                                         | Usage/cost detail       | Cost investigation      | Usage records             |
| Get-AzPolicyState -Filter "ComplianceState eq 'NonCompliant'"                                                                                                  | Non-compliant resources | Governance              | Policy states             |
| Get-AzKeyVaultSecret -VaultName \<kv\>                                                                                                                         | List secrets (metadata) | Inventory/expiry checks | Name, Expires, Enabled    |

**Script — secrets expiring in Key Vaults within 30 days:**

**POWERSHELL**

\$limit = (Get-Date).AddDays(30)

Get-AzKeyVault \| ForEach-Object {

Get-AzKeyVaultSecret -VaultName \$\_.VaultName \| Where-Object { \$\_.Expires -and \$\_.Expires -lt \$limit } \|

Select-Object @{n='Vault';e={\$\_.VaultName}}, Name, Expires

}

## kubectl

| **Command**                                                                                 | **What it does**          | **When to use**               | **Expected output**                        |
|---------------------------------------------------------------------------------------------|---------------------------|-------------------------------|--------------------------------------------|
| kubectl get pods -n \<ns\> -o wide                                                          | Pods with node/IP         | First look                    | Status, restarts, node                     |
| kubectl describe pod \<pod\> -n \<ns\>                                                      | Pod details + events      | CrashLoop, Pending, ImagePull | Last State, exit code, Events              |
| kubectl logs \<pod\> -n \<ns\> --previous                                                   | Logs of crashed container | CrashLoopBackOff              | Last container's stdout                    |
| kubectl logs -l app=\<label\> -n \<ns\> --tail=100 -f                                       | Follow logs by label      | Live debugging                | Log stream                                 |
| kubectl get events -n \<ns\> --sort-by=.lastTimestamp                                       | Recent events             | Scheduling, probes, OOM       | Event list                                 |
| kubectl top pods -n \<ns\> / kubectl top nodes                                              | CPU/memory usage          | Resource pressure             | Usage values                               |
| kubectl get hpa -n \<ns\> / kubectl describe hpa \<name\> -n \<ns\>                         | Autoscaler state          | Scaling issues                | Targets, replicas, conditions              |
| kubectl rollout status deployment/\<name\> -n \<ns\>                                        | Watch rollout             | Deployments                   | "successfully rolled out"                  |
| kubectl rollout history deployment/\<name\> -n \<ns\>                                       | Revisions                 | Before rollback               | Revision list                              |
| kubectl rollout undo deployment/\<name\> -n \<ns\>                                          | Roll back                 | Bad release                   | "rolled back"                              |
| kubectl exec -it \<pod\> -n \<ns\> -- sh                                                    | Shell in container        | Debug (if shell exists)       | Interactive shell                          |
| kubectl debug -it \<pod\> -n \<ns\> --image=busybox --target=\<container\>                  | Ephemeral debug container | Distroless/chiseled images    | Interactive shell                          |
| kubectl get svc,ingress -n \<ns\>                                                           | Services/ingress          | Routing issues                | IPs, ports, hosts                          |
| kubectl get endpoints \<svc\> -n \<ns\>                                                     | Pods behind a service     | 502/503 from ingress          | Pod IPs (empty = selector/readiness issue) |
| kubectl auth can-i create deployments -n \<ns\> --as \<user\>                               | RBAC check                | Permission issues             | yes/no                                     |
| kubectl cordon \<node\> / kubectl drain \<node\> --ignore-daemonsets --delete-emptydir-data | Take node out             | Node maintenance              | Node SchedulingDisabled / evicted pods     |

## Docker

| **Command**                                                             | **What it does**                 | **When to use**           | **Expected output**         |
|-------------------------------------------------------------------------|----------------------------------|---------------------------|-----------------------------|
| docker build -t \<acr\>.azurecr.io/app:\<sha\> .                        | Build image                      | Local/CI build            | Image ID                    |
| docker run --rm -p 8080:8080 \<image\>                                  | Run locally                      | Test image                | App logs                    |
| docker images / docker image ls                                         | List images                      | Housekeeping              | Repo, tag, size             |
| docker history \<image\>                                                | Layers and sizes                 | Image size optimisation   | Layer list                  |
| docker inspect \<image\>                                                | Metadata (user, env, entrypoint) | Verify non-root, ports    | JSON                        |
| az acr login -n \<acr\> then docker push \<acr\>.azurecr.io/app:\<sha\> | Push to ACR                      | Publish image             | Layer push progress, digest |
| docker logs -f \<container\>                                            | Container logs                   | Local debugging           | Log stream                  |
| docker system prune -af                                                 | Remove unused data               | Free disk on build agents | Reclaimed space             |
| az acr build -r \<acr\> -t app:\<sha\> .                                | Build in Azure (ACR Tasks)       | No local Docker / agent   | Build log, digest           |

## Terraform

| **Command**                                                            | **What it does**                  | **When to use**            | **Expected output**                               |
|------------------------------------------------------------------------|-----------------------------------|----------------------------|---------------------------------------------------|
| terraform init                                                         | Providers, modules, backend       | First run / backend change | "Terraform has been successfully initialized!"    |
| terraform fmt -check -recursive                                        | Format check                      | CI                         | Non-zero exit if unformatted                      |
| terraform validate                                                     | Syntax/semantic check             | CI                         | "Success! The configuration is valid."            |
| terraform plan -out=tfplan                                             | Preview and save plan             | Before apply               | Plan summary (add/change/destroy)                 |
| terraform plan -detailed-exitcode                                      | Plan with exit code 0/1/2         | Drift detection            | Exit 2 when changes                               |
| terraform plan -refresh-only                                           | Show drift only                   | Drift review               | Changes outside Terraform                         |
| terraform apply tfplan                                                 | Apply saved plan                  | Pipeline apply             | "Apply complete!"                                 |
| terraform state list / terraform state show \<addr\>                   | Inspect state                     | Troubleshooting            | Resource addresses / attributes                   |
| terraform state rm \<addr\>                                            | Forget resource (no delete)       | Hand-off between states    | "Removed ..."                                     |
| terraform import \<addr\> \<id\>                                       | Legacy import                     | Single resources           | "Import successful!"                              |
| terraform plan -generate-config-out=gen.tf                             | Generate config for import blocks | Bulk import                | gen.tf created                                    |
| terraform force-unlock \<LOCK_ID\>                                     | Remove stuck lock                 | After confirming no run    | "Terraform state has been successfully unlocked!" |
| terraform output -json                                                 | Outputs                           | Pass values to scripts     | JSON                                              |
| terraform providers lock -platform=linux_amd64 -platform=windows_amd64 | Update lock file for platforms    | Mixed OS teams/agents      | Lock file updated                                 |
| TF_LOG=DEBUG terraform plan                                            | Verbose logs                      | Provider/API errors        | Detailed HTTP logs                                |

## KQL (Log Analytics / Application Insights)

**KQL**

// Failed requests by operation (5xx)

AppRequests \| where TimeGenerated \> ago(1h) and toint(ResultCode) \>= 500

\| summarize count() by OperationName, ResultCode

// Latency percentiles trend

AppRequests \| where TimeGenerated \> ago(24h)

\| summarize P50=percentile(DurationMs,50), P95=percentile(DurationMs,95) by bin(TimeGenerated, 15m) \| render timechart

// Top exceptions

AppExceptions \| where TimeGenerated \> ago(24h) \| summarize count() by ProblemId \| top 10 by count\_

// Dependency failures

AppDependencies \| where TimeGenerated \> ago(1h) and Success == false

\| summarize count() by Target, ResultCode

// VM CPU (AMA)

Perf \| where CounterName == "% Processor Time" and InstanceName == "\_Total" and TimeGenerated \> ago(6h)

\| summarize avg(CounterValue) by Computer, bin(TimeGenerated, 5m)

// Agents not reporting

Heartbeat \| summarize LastSeen = max(TimeGenerated) by Computer \| where LastSeen \< ago(15m)

// Who changed / deleted resources

AzureActivity \| where TimeGenerated \> ago(24h) and ActivityStatusValue == "Success"

\| where OperationNameValue endswith "/write" or OperationNameValue endswith "/delete"

\| project TimeGenerated, Caller, OperationNameValue, ResourceGroup

// Role assignments created

AzureActivity \| where OperationNameValue =~ "MICROSOFT.AUTHORIZATION/ROLEASSIGNMENTS/WRITE" and TimeGenerated \> ago(7d)

\| project TimeGenerated, Caller, \_ResourceId

// AKS: pods with restarts / failing reasons

KubePodInventory \| where TimeGenerated \> ago(1h) and ContainerRestartCount \> 0

\| summarize max(ContainerRestartCount) by Namespace, Name, ContainerStatusReason

// AKS container logs with errors

ContainerLogV2 \| where TimeGenerated \> ago(30m) and LogMessage has "error"

\| project TimeGenerated, PodNamespace, PodName, LogMessage \| take 50

// Billable ingestion by table

Usage \| where TimeGenerated \> ago(30d) and IsBillable \| summarize GB=sum(Quantity)/1000 by DataType \| top 10 by GB

// Key Vault failed access

AzureDiagnostics \| where ResourceProvider == "MICROSOFT.KEYVAULT" and httpStatusCode_d \>= 400 and TimeGenerated \> ago(1h)

\| summarize count() by OperationName, httpStatusCode_d, CallerIPAddress

// App Gateway backend errors

AGWAccessLogs \| where TimeGenerated \> ago(1h) and HttpStatus \>= 500

\| summarize count() by HttpStatus, ServerRouted, ServerStatus

> When to use: during incidents (top three), capacity reviews (CPU), governance (role assignments), cost reviews (Usage). Expected output: tables or time charts; empty result means no matches — verify the time range and table name.

## Azure DevOps YAML — Reference Snippets

**YAML**

\# Trigger, PR validation and path filters

trigger:

branches: { include: \[ main \] }

paths: { include: \[ src/\*, deploy/\* \] }

pr:

branches: { include: \[ main \] }

\# Variables: group (Key Vault-linked), template expressions, runtime

variables:

\- group: app-prod-kv

\- name: tag

value: \$(Build.SourceVersion)

\# Conditions

\- stage: Prod

condition: and(succeeded(), eq(variables\['Build.SourceBranch'\], 'refs/heads/main'))

\# Deployment job with environment (approvals configured on the environment)

\- deployment: Deploy

environment: orders-prod

strategy:

runOnce:

deploy:

steps:

\- script: echo deploying \$(tag)

\# Azure CLI with workload identity federation service connection

\- task: AzureCLI@2

inputs:

azureSubscription: sc-prod-wif

scriptType: bash

scriptLocation: inlineScript

inlineScript: az webapp show -g \<rg\> -n \<app\> --query state

\# Key Vault secrets into a step

\- task: AzureKeyVault@2

inputs: { azureSubscription: sc-prod-wif, KeyVaultName: \<kv\>, SecretsFilter: 'ApiKey' }

\- script: ./run.sh

env: { API_KEY: \$(ApiKey) }

\# Template reuse

\- template: steps/build.yml@templates

parameters: { configuration: Release }

\# Publish and download artifacts

\- publish: \$(Build.ArtifactStagingDirectory)

artifact: drop

\- download: current

artifact: drop

\# Caching

\- task: Cache@2

inputs:

key: 'nuget \| "\$(Agent.OS)" \| \*\*/packages.lock.json'

path: \$(Pipeline.Workspace)/.nuget/packages

| **Snippet**              | **What it does**                                     | **When to use**                | **Expected result**              |
|--------------------------|------------------------------------------------------|--------------------------------|----------------------------------|
| trigger / pr             | Defines CI and PR triggers                           | Every pipeline                 | Runs on main commits and PRs     |
| variables: - group:      | Imports variable group (optionally Key Vault-backed) | Secrets/config per environment | Variables available as \$(name)  |
| condition:               | Runs stage/job only when expression is true          | Prod only from main            | Stage skipped otherwise          |
| deployment + environment | Deployment job with history, approvals, checks       | Any deployment                 | Waits for checks, then deploys   |
| AzureCLI@2               | Runs az commands with service connection identity    | Azure operations               | Script output                    |
| AzureKeyVault@2          | Fetches secrets as masked variables                  | Runtime secrets                | Secrets masked as \*\*\* in logs |
| template: / extends:     | Reuse and enforce standard steps                     | Many pipelines                 | Expanded at compile time         |
| Cache@2                  | Restores dependency cache                            | Speed up builds                | "Cache restored" on hit          |

# Section 6 — Azure Architecture Design Questions

**How to answer any design question (5-step framework):**

**1. Clarify requirements** — users, traffic, availability (SLO, RTO/RPO), data sensitivity, compliance, budget, team skills.

**2. High-level design** — draw the main components and data flow.

**3. Deep dive** — identity, networking, data, scaling, monitoring, CI/CD.

**4. Trade-offs** — what you chose not to do and why (cost vs resilience, managed vs control).

**5. Operate** — how it's monitored, secured, cost-controlled and evolved.

Say your assumptions out loud: "I'll assume about 10,000 concurrent users, 99.95% availability, UK data residency."

## Design 1 — Highly Available Web Application on Azure

**Requirements (assumed):** Public web app + API, 99.95% availability, UK users mainly, peak 20k concurrent users, RTO 1h / RPO 15 min.

![Architecture diagram](assets/925fc6b439ee1a44642e8719eb4edd516bca7035.png)

**Components:**

- **Front Door Premium:** global entry, WAF, caching, health-probe failover, Private Link to origins.

- **App Service (zone-redundant):** stateless web/API tier, autoscale, deployment slots.

- **Azure SQL (zone-redundant) + failover group:** HA in-region; DR to UK West.

- **Redis:** cache and session state.

- **Service Bus + Functions:** async work (emails, integrations).

- **Key Vault, managed identities:** no secrets in config.

- **App Insights + Log Analytics:** telemetry, alerts, workbooks.

**Design trade-offs:** Warm standby instead of active-active (lower cost, RTO ~1h acceptable). App Service over AKS (less ops; team skills). Front Door Premium cost vs security of Private Link origins.

**Security:** WAF managed rules; private endpoints for SQL/KV/Storage; App Service access restricted to Front Door; Entra ID auth; TLS 1.2+; Defender for Cloud.

**Cost:** Reservations/savings plan for base App Service and SQL; secondary region minimal until failover; Front Door caching reduces origin load.

**Scalability:** Autoscale web tier; Redis offloads reads; SQL read scale-out or Hyperscale for growth; async processing.

**Likely follow-up questions:**

- *"Why not active-active?"* — Requirements don't need it; it adds data consistency complexity and roughly doubles cost.

- *"How do you handle sessions during failover?"* — Stateless tokens or Redis with geo-replication (Enterprise tier); otherwise users re-authenticate.

- *"What's the composite SLA?"* — Multiply component SLAs; zone redundancy and multi-region raise the effective availability.

## Design 2 — Secure Azure Infrastructure for Multiple Environments

**Requirements:** Dev, test, prod for 8 teams; strong isolation for prod; shared platform services; consistent security.

![Architecture diagram](assets/4862a756434ddac15e85f799731a157173bb6737.png)

**Components:** Management group hierarchy (Azure landing zone pattern); subscription per workload per environment class; hub-spoke networking in Connectivity; central logging in Management; subscription vending via Terraform.

**Design trade-offs:** More subscriptions = better isolation and quotas but more management (mitigated by vending automation). Separate prod/non-prod MGs allow stricter prod policies.

**Security:** Policies at MG level (allowed regions, no public IPs in prod, diagnostics, Defender plans); RBAC via groups + PIM in prod; separate service connections per environment; private endpoints; firewall egress.

**Cost:** Budgets per subscription; non-prod auto-shutdown; dev/test pricing where eligible.

**Scalability:** New teams onboard via vending module in hours; policies apply automatically.

**Likely follow-up questions:**

- *"Why not one subscription with RGs per environment?"* — Weaker isolation, shared quotas, harder RBAC/policy boundaries.

- *"How do non-prod environments mirror prod?"* — Same IaC modules with different parameters; pre-prod with prod-like controls.

## Design 3 — Centralised Monitoring for 100+ Azure Resources

**Requirements:** 6 subscriptions, mixed PaaS/VMs/AKS; single pane of glass; team-scoped access; controlled cost.

![Architecture diagram](assets/1c5d9db2428d90ee34fb3450db64390a4d991485.png)

**Components:** Central workspace per environment; Azure Policy DINE for diagnostics and AMA; workspace-based App Insights; Managed Prometheus + Grafana for AKS; Workbooks; alerts → action groups; Sentinel on the same workspace (or linked).

**Design trade-offs:** One workspace (easy correlation) vs many (isolation/cost attribution) — use resource-context RBAC instead of many workspaces. Basic/Auxiliary plans for verbose logs trade query features for cost.

**Security:** Resource-context and table-level RBAC; private link (AMPLS) for ingestion where required; log immutability via retention and restricted delete rights.

**Cost:** DCR transformations; table plans; per-table retention; commitment tier; ingestion alerts.

**Scalability:** Policy ensures new resources onboard automatically; baseline alerts deployed by policy (Azure Monitor Baseline Alerts).

**Likely follow-up questions:**

- *"How do you know coverage is complete?"* — Policy compliance dashboard + Resource Graph query of resources without diagnostic settings.

- *"How would teams build their own alerts?"* — Alert modules in IaC with standard action groups and severity model.

## Design 4 — Scalable AKS-Based Microservices Platform

**Requirements:** 20 microservices, multiple teams, autoscaling, secure by default, GitOps-friendly.

![Architecture diagram](assets/d989a1fae81c28b61eca0582a60a4358acf5afcc.png)

**Components:** Private AKS cluster with Entra ID + Azure RBAC; system/user/spot node pools across zones; cluster autoscaler + HPA/KEDA; Workload Identity; Key Vault CSI driver; ACR Premium with private endpoint; ingress via Application Gateway for Containers or managed NGINX (app routing add-on); GitOps with Flux extension; Azure Policy for Kubernetes; Defender for Containers.

**Design trade-offs:** Shared multi-tenant cluster (cost, efficiency) vs cluster per team (isolation, overhead). Choose shared with namespaces, quotas, network policies; separate clusters for prod/non-prod. AKS vs Container Apps — AKS for control and ecosystem.

**Security:** No local accounts; namespace RBAC; network policies (Cilium); image allow-list policy; pod security standards; egress via firewall; private API server.

**Cost:** Right-sized requests; autoscaler; spot for batch; stop non-prod at night; cost analysis add-on per namespace.

**Scalability:** HPA/KEDA for pods; cluster autoscaler/node auto-provisioning for nodes; quotas sized for peak.

**Likely follow-up questions:**

- *"How do you upgrade AKS safely?"* — Auto-upgrade channel (patch) + planned maintenance windows; upgrade non-prod first; surge settings; PDBs; or blue-green clusters for major changes.

- *"How do teams deploy?"* — GitOps: team repo → Flux reconciles namespace manifests; platform manages cluster config.

## Design 5 — Secure CI/CD Deployment Architecture

**Requirements:** Azure DevOps for 15 repos; deployments to private Azure resources; strong controls for prod.

![Architecture diagram](assets/fa6c30c3c90401cd1b935993e406fc50490e7314.png)

**Components:** Branch policies; required extends template; separate service connections per environment with WIF; Managed DevOps Pools with VNet injection for private targets; environments with checks; Key Vault-linked variable groups; artifact signing and scanning; audit streaming.

**Design trade-offs:** Managed DevOps Pools (cost, maintenance-free) vs self-managed VMSS agents (more control). Strict approvals vs speed — use automated checks for lower environments, human approval only for prod.

**Security:** No secrets (WIF); least privilege per connection; pipeline permissions restricted; ephemeral agents; image signing; deployment only from ACR.

**Cost:** Pools scale to zero; caching to reduce build minutes.

**Scalability:** Templates make new repos compliant quickly.

**Likely follow-up questions:**

- *"How do you stop a rogue pipeline using the prod connection?"* — Pipeline permissions + branch control + required template checks on the connection.

- *"Audit trail?"* — Environment deployment history + approvals + audit stream to Log Analytics.

## Design 6 — Enterprise RBAC Model

**Requirements:** 200 engineers, 25 teams, regulated industry, auditable least privilege.

![Architecture diagram](assets/e4b74133639b311de8d5baecf53a7b7e21f0c2e0.png)

**Components:** HR-driven lifecycle; Entra security groups per team/env/function; Azure RBAC at RG/subscription scope; PIM for Groups; access packages for guests; workload identities; access reviews; Activity Log alerts; RBAC as code.

**Design trade-offs:** Fine-grained groups (precise) vs fewer broad groups (simpler) — use a naming standard and automation. Approval for every elevation (secure) vs on-call speed — approvals only for highest privilege.

**Security:** No standing Owner; break-glass accounts monitored; Conditional Access for admin roles; deny assignments via deployment stacks for critical resources.

**Cost:** Entra ID P2/Governance licensing for PIM and reviews.

**Scalability:** Group creation in Terraform per team onboarding.

**Likely follow-up questions:**

- *"Entra roles vs Azure roles?"* — Directory vs resource permissions; both should use PIM.

- *"How do you prove least privilege to auditors?"* — Exports of assignments, PIM activation logs, access review results.

## Design 7 — Cost-Efficient Infrastructure for Growing Workloads

**Requirements:** Startup growing 3× in a year; unpredictable traffic; small ops team; must control spend.

![Architecture diagram](assets/00e46f8360d31ed4382819d47ddbb649a2e9f246.png)

**Components:** Serverless/consumption services (Container Apps, Functions Flex Consumption, SQL serverless or Cosmos DB serverless/autoscale), Front Door caching, storage lifecycle, budgets/anomaly alerts, tagging.

**Design trade-offs:** Serverless = pay per use and low ops, but cold starts and per-unit cost higher at sustained high load — revisit with savings plans or dedicated tiers once load stabilises. Managed services over self-hosted to save people cost.

**Security:** Managed identities; private networking where needed (Container Apps environment with VNet); WAF.

**Cost:** Scale to zero; auto-pause SQL serverless for dev; commitments only once baseline is stable; FinOps reviews monthly; unit cost per customer tracked.

**Scalability:** Each component scales automatically; queue-based load levelling.

**Likely follow-up questions:**

- *"When would you move off serverless?"* — When sustained load makes dedicated capacity + commitments cheaper; measure unit cost.

- *"Cold starts?"* — Minimum replicas = 1 for latency-sensitive apps; always-ready instances in Flex Consumption.

## Design 8 — Disaster Recovery Across Azure Regions

**Requirements:** Tier-1 order platform: RTO 1h, RPO 5 min; UK data residency.

![Architecture diagram](assets/a3717e13438936fb7edd0d4e7ce1f4ae194aaec7.png)

**Components:** Front Door with priority origin groups; App tier in both regions (warm standby); SQL auto-failover group (listener endpoint); GZRS storage; Key Vault per region with secrets deployed by pipeline; ACR geo-replication; IaC for both regions; DR runbook and drills.

**Design trade-offs:** Warm standby vs active-active (cost and complexity vs RTO). Automatic vs customer-managed SQL failover (speed vs control and data loss risk). UK West has fewer services/capacity than UK South — validate SKU availability.

**Security:** Same policies and RBAC in both regions; secrets replicated securely; monitoring in both regions.

**Cost:** Secondary minimal; scale on failover; reservations only for primary baseline.

**Scalability:** Secondary autoscale rules ready; quota pre-approved in secondary region.

**Likely follow-up questions:**

- *"How do you test?"* — Quarterly planned failover; game days; measure actual RTO/RPO.

- *"Failback?"* — Re-establish replication, planned failover back in a maintenance window.

## Design 9 — Terraform Module Architecture for Multiple Teams

**Requirements:** 10 teams, consistent secure infrastructure, independent delivery, central governance.

![Architecture diagram](assets/ae31c5c3d453b58eedbb86b70bee0170d874220e.png)

**Components:** Versioned platform modules (built on Azure Verified Modules where possible); team repos with thin root modules per environment; separate state per team/env; shared pipeline template; policy as safety net; module tests and changelogs.

**Design trade-offs:** Opinionated modules (consistency) vs flexibility — expose escape hatches carefully. Monorepo vs polyrepo for modules. Central approval vs team autonomy — teams own their roots; platform owns modules and policy.

**Security:** Secure defaults in modules (private endpoints, diagnostics, TLS); Checkov/tflint in CI; state storage RBAC per team.

**Cost:** Infracost in PRs; SKU validation in module variables.

**Scalability:** New teams start from a template repo; module upgrades through Renovate/Dependabot PRs.

**Likely follow-up questions:**

- *"How do you roll out a breaking module change?"* — Major version, migration guide, moved blocks, support both versions for a period.

- *"Cross-team dependencies?"* — Data sources or outputs published to App Configuration/Key Vault rather than shared state.

## Design 10 — Secure Private Networking for Azure PaaS Services

**Requirements:** All PaaS (SQL, Storage, Key Vault, ACR, Service Bus) private only; on-prem connectivity; centralised DNS and egress control.

![Architecture diagram](assets/9234aabb18cd589f4e7bbd2eaef2fdc074b8b3c5.png)

**Components:** Hub-spoke; private endpoints for each PaaS sub-resource; central private DNS zones linked to the hub; DNS Private Resolver for hybrid resolution; spokes use hub DNS (custom DNS = resolver inbound IP or Azure DNS with zone links); Azure Firewall for egress; Policy to deny public network access and auto-create DNS records.

**Design trade-offs:** Private endpoints (strong isolation, cost per endpoint + data processing) vs service endpoints (cheaper, weaker, no on-prem). Routing PE traffic through firewall (inspection) vs direct (simplicity, performance).

**Security:** Public network access disabled; NSGs on PE subnets; firewall egress allow-list; Defender for Cloud.

**Cost:** PE hourly + per-GB; firewall; resolver endpoints — consolidate where possible.

**Scalability:** Policy-driven DNS record creation; subnet sizing for many PEs; IP address planning.

**Likely follow-up questions:**

- *"Why central DNS zones?"* — One record per name; avoids conflicts and duplicate zones per spoke.

- *"Developers need access from laptops?"* — VPN/ZTNA into the network, or Azure Bastion/jump hosts — not reopening public access.

# Section 7 — Mock Interview: Senior Azure Cloud / DevOps Engineer

**Format:** 35 questions in the order a real panel might ask them. For each: the question, a strong model answer to speak (about 60–120 seconds), and **what the interviewer expects** from someone with 5+ years of Azure experience.

**Practice method:** Cover the model answer, answer aloud, then compare. Time yourself — most answers should be under two minutes.

## Part 1 — Technical Questions (15)

### T1. "Tell me about your Azure experience and the environments you've supported."

**Model answer structure (fill with your real experience):** "I've worked with Azure for \[X\] years, mainly on \[platform/DevOps/SRE\] work. Most recently I supported \[type of environment — e.g., ~N subscriptions, AKS and App Service workloads\] for \[type of business\]. My main areas are \[RBAC and identity, monitoring with Azure Monitor and App Insights, Azure DevOps pipelines and Terraform\]. A piece of work I'm proud of is \[one concrete outcome with a number\]. I'm now looking for a role where I can \[set standards / lead platform work\], which is why this role interests me."

**What the interviewer expects:** A 90-second, structured, honest summary with scale (subscriptions, services, team size), your specific ownership, one quantified outcome, and a link to this JD. Not a CV read-out.

### T2. "Explain Owner, Contributor, Reader and User Access Administrator."

**Model answer:** "Owner has full access, including managing access. Contributor can manage all resources but cannot grant access — Microsoft.Authorization write and delete are excluded. Reader can view but not change. User Access Administrator can manage role assignments but not resources. There's also Role Based Access Control Administrator, which can assign roles and supports conditions to limit which roles. I assign these to groups, at the narrowest scope, with PIM for privileged roles in production."

**What the interviewer expects:** Precise distinctions, the Contributor nuance, awareness of RBAC Administrator with conditions, and least-privilege practice.

### T3. "What's the difference between a system-assigned and user-assigned managed identity?"

**Model answer:** "System-assigned is created with a resource and deleted with it — one-to-one. User-assigned is a standalone resource, can be attached to many resources and exists independently, so I can grant RBAC before deploying the app. I use user-assigned for scale sets, AKS workload identity, blue-green or when several apps share permissions; system-assigned for a simple single app."

**What the interviewer expects:** Lifecycle difference and real use cases.

### T4. "How does Azure Monitor collect data from a VM today?"

**Model answer:** "Platform metrics come automatically from the host. For guest data, the Azure Monitor Agent is installed — usually via Azure Policy — and Data Collection Rules define what to collect, like performance counters, Windows events or syslog, and where to send it. The legacy Log Analytics agent was retired in 2024. VM insights adds performance views and optionally the dependency map."

**What the interviewer expects:** AMA + DCR, policy deployment, awareness of MMA retirement.

### T5. "Write a KQL query to find the top 5 slowest API operations in the last 24 hours."

**Model answer:**

**KQL**

AppRequests

\| where TimeGenerated \> ago(24h)

\| summarize P95 = percentile(DurationMs, 95), Count = count() by OperationName

\| where Count \> 100

\| top 5 by P95 desc

"I use the 95th percentile because averages hide tail latency, and I filter low-volume operations so the result is meaningful."

**What the interviewer expects:** Correct syntax, percentiles not averages, sensible filters, ability to explain.

### T6. "What types of alerts exist in Azure Monitor and when do you use each?"

**Model answer:** "Metric alerts — near real-time on numeric metrics, with static or dynamic thresholds. Log search alerts — KQL-based for complex conditions and correlation. Activity Log alerts — for control-plane events like role assignments or deletes, plus Service Health and Resource Health alerts. Prometheus alerts for AKS metrics. Smart detection and availability tests from Application Insights. All route to action groups, and alert processing rules can suppress or add actions at scale."

**What the interviewer expects:** Complete list with appropriate use; action groups and processing rules.

### T7. "How do Azure DevOps environments, approvals and checks work?"

**Model answer:** "An environment is a deployment target in Azure DevOps — a logical group that can contain Kubernetes namespaces or VMs. Deployment jobs target environments, which gives deployment history. Approvals and checks are configured on the environment, not in YAML: manual approvals, branch control, business hours, required template, Azure Monitor alerts, Azure Function or REST API checks, and exclusive lock. They're evaluated before a stage that uses the environment runs, so a developer can't bypass them by editing YAML."

**What the interviewer expects:** Checks on the resource; list of check types; why that matters.

### T8. "Explain workload identity federation for service connections."

**Model answer:** "Instead of storing a client secret, Entra ID trusts tokens issued by Azure DevOps for a specific service connection — via a federated credential on an app registration or a user-assigned managed identity. Each pipeline run gets a short-lived OIDC token, exchanges it for an Entra access token, and there's nothing to rotate or leak. It's the recommended option, and existing connections can be converted."

**What the interviewer expects:** OIDC trust concept, no secrets, conversion awareness.

### T9. "How does Terraform state locking work with the azurerm backend?"

**Model answer:** "The azurerm backend takes a lease on the state blob during operations that write state. A second process gets 'Error acquiring the state lock' with lock details. If a run crashes, the lease can remain; after confirming nothing is running, terraform force-unlock with the lock ID releases it. I combine that with pipeline-only applies and exclusive lock checks so concurrency is avoided in the first place."

**What the interviewer expects:** Blob lease, force-unlock with caution, process controls.

### T10. "What's the difference between terraform import and import blocks?"

**Model answer:** "terraform import is an imperative CLI command that writes directly into state and needs you to write the config yourself. Import blocks, from Terraform 1.5, are declarative — they live in code, are reviewed in PRs, run as part of plan and apply, and with -generate-config-out Terraform can generate the configuration. I prefer import blocks."

**What the interviewer expects:** Up-to-date Terraform knowledge.

### T11. "How do you choose between App Service, AKS, Container Apps and Functions?"

**Model answer:** "App Service for web apps and APIs with minimal ops. Functions for event-driven, short-lived work, especially with triggers like queues or timers. Container Apps for containerised microservices that want serverless scaling, KEDA and Dapr without managing Kubernetes. AKS when we need full Kubernetes control, custom operators, service mesh, or we're running many services where the platform team can manage it. Team skills and operational capacity matter as much as features."

**What the interviewer expects:** Clear decision criteria and recognition of operational cost.

### T12. "Explain Private Endpoint vs Service Endpoint."

**Model answer:** "A private endpoint gives the PaaS resource a private IP in my VNet via Private Link — traffic stays private, it works from peered VNets and on-premises, and I can disable public access. It needs private DNS. A service endpoint keeps the public endpoint but lets the service restrict access to specific subnets, and traffic goes over the Azure backbone — simpler and free, but no on-prem support and weaker exfiltration protection. I default to private endpoints for production data services."

**What the interviewer expects:** DNS awareness and the trade-off.

### T13. "How do you scale AKS workloads?"

**Model answer:** "Pods with HPA on CPU/memory or custom metrics — requests must be set. Event-driven scaling with KEDA, for example on Service Bus queue length. Nodes with the cluster autoscaler or node auto-provisioning when pods are pending. Plus quotas and capacity planning, and PodDisruptionBudgets so scale-down and upgrades don't hurt availability."

**What the interviewer expects:** Both layers, requests, KEDA.

### T14. "How do you manage secrets for an app on AKS?"

**Model answer:** "Prefer no secrets — workload identity to access Azure services directly. For secrets that must exist, Key Vault with the Secrets Store CSI driver, authenticating with workload identity, optionally syncing to Kubernetes secrets, with rotation polling enabled. Kubernetes secrets are only base64-encoded, so I enable etcd encryption with KMS if they're used, and restrict RBAC on secrets."

**What the interviewer expects:** Workload identity, CSI driver, awareness that K8s secrets aren't encrypted by default.

### T15. "What's in your Azure cost governance toolkit?"

**Model answer:** "Visibility: Cost Management views and exports, tags enforced by policy, showback. Alerts: budgets with forecast thresholds and anomaly alerts. Optimisation: Advisor, rightsizing, auto-shutdown, storage lifecycle, Log Analytics table plans and DCR filtering, reservations and savings plans after rightsizing. Governance: allowed SKUs and regions policies, cost estimates in PRs, and a monthly FinOps review with owners."

**What the interviewer expects:** A system, not a list of tricks.

## Part 2 — Troubleshooting Questions (10)

### TS1. "Users report the website is slow, but CPU and memory are normal. What do you do?"

**Model answer:** "Normal CPU and memory means the app is probably waiting. I'd check Application Insights Performance for which operations are slow and their dependencies — SQL, Redis, external APIs. Check SQL Query Store and DTU, Redis server load, SNAT port exhaustion for outbound calls, and thread pool starvation. Also check front-end and network: Front Door latency, page load times by region. Then fix the biggest contributor and verify with percentiles."

**What the interviewer expects:** Understanding of non-CPU bottlenecks (dependencies, SNAT, thread starvation).

### TS2. "A storage account suddenly returns 403 to an application."

**Model answer:** "403 is either authorisation or network. The error message tells: 'AuthorizationPermissionMismatch' means RBAC — the identity lacks a data role like Storage Blob Data Contributor; 'AuthorizationFailure' with network rules means firewall or private endpoint. Also check if shared key access was disabled while the app still uses keys or SAS — that gives 'KeyBasedAuthenticationNotPermitted'. I check the storage logs (StorageBlobLogs) for the status and auth type, then fix the identity or network."

**What the interviewer expects:** Classification by error code; storage logs.

### TS3. "AKS pods are stuck in Pending."

**Model answer:** "kubectl describe pod Events say why: insufficient CPU/memory — check requests vs node capacity and whether the cluster autoscaler is scaling or at max or blocked by quota; node selectors/taints/affinity that no node matches; PVC issues — for example a zonal disk in a different zone; or too many pods per node. I fix requests, autoscaler limits, quota, or scheduling constraints."

**What the interviewer expects:** Events-first, autoscaler/quota, volume zone awareness.

### TS4. "A pipeline deploy step times out connecting to an Azure SQL database."

**Model answer:** "Likely network. Microsoft-hosted agents come from public IPs; if SQL has public access disabled or a firewall, they're blocked. Options: run the job on a Managed DevOps Pool or self-hosted agent in the VNet with private endpoint DNS; or temporarily allow the agent IP — not great for prod. Also check authentication — Entra-only auth needs the pipeline identity created as a database user."

**What the interviewer expects:** Agent networking knowledge.

### TS5. "After enabling a new Azure Policy, deployments fail. What do you do?"

**Model answer:** "The error is RequestDisallowedByPolicy and names the assignment and definition. I check whether the deployment is genuinely non-compliant or the policy is too broad. For an urgent legitimate deployment, a time-limited exemption with justification. Then fix: update the template to comply or adjust the policy. Lesson: roll out policies in audit or DoNotEnforce mode first and communicate."

**What the interviewer expects:** Calm process, exemptions, audit-first rollout.

### TS6. "Front Door returns 504/503 for some users."

**Model answer:** "Check Front Door access logs for the error info and which origin. 504 often means the origin took longer than the response timeout — default 60 seconds — or isn't reachable. 503 can mean all origins unhealthy by probes. I check origin health probes and the probe path, origin access restrictions — for example App Service only allowing the Front Door service tag but missing the FDID header config — Private Link approval status for Premium origins, and origin performance."

**What the interviewer expects:** Logs first; probes, timeouts, Private Link approval.

### TS7. "A VM can't be reached over RDP/SSH via Bastion."

**Model answer:** "Check Bastion subnet and NSG rules — Bastion needs specific inbound and outbound rules; the target VM NSG must allow 3389/22 from the Bastion subnet; the VM is running and the guest OS firewall allows it; boot diagnostics and serial console show if the OS is healthy; and for Entra login, the user needs the Virtual Machine Administrator/User Login role."

**What the interviewer expects:** Layered approach; boot diagnostics/serial console.

### TS8. "Terraform plan shows changes nobody made."

**Model answer:** "Possible causes: drift from portal changes — check Activity Log; Azure adding defaults or tags via policy Modify — use ignore_changes for those attributes; provider upgrade changing defaults or API normalisation — check provider changelog; or different variables. I use plan -refresh-only to see real drift separately from config differences."

**What the interviewer expects:** Several causes, including policy and provider versions.

### TS9. "Function App triggers stopped firing."

**Model answer:** "Check the Function host status and logs in App Insights for host errors. Common causes: storage account connection issues — the runtime needs blob/queue/table access, especially after private endpoints or key changes; trigger connection setting changed; the app is stopped or the plan scaled to zero without scale controller access in network-restricted setups; or a function disabled by app setting. For Service Bus triggers, check the queue has messages and the identity has Data Receiver."

**What the interviewer expects:** Knowledge of Functions runtime dependencies on storage.

### TS10. "Alerts didn't fire during an outage. Why?"

**Model answer:** "Check the alert rule's history — was the condition met? The rule might be disabled, scoped to the wrong resource, use a metric that didn't change, have too long an evaluation window, or a log alert query returned no rows because telemetry stopped — which is why 'absence of data' alerts matter. Also check alert processing rules suppressing notifications and the action group delivery. Then add a test alert and synthetic monitoring."

**What the interviewer expects:** Meta-monitoring; absence-of-data alerts.

## Part 3 — Architecture Questions (5)

### A1. "Design monitoring for a new microservices platform from scratch."

**Model answer:** "Central Log Analytics workspace per environment; OpenTelemetry instrumentation with role names; Container Insights and Managed Prometheus with Grafana; control-plane diagnostics; SLOs per service with burn-rate alerts; availability tests; action groups by team and severity; workbooks per service; all deployed as code with policy enforcing diagnostics; cost managed by table plans and namespace filtering."

**What the interviewer expects:** End-to-end design across metrics, logs, traces, alerting, dashboards, cost.

### A2. "How would you design landing zones for a company moving 50 apps to Azure?"

**Model answer:** "Azure landing zone architecture: management group hierarchy with platform and landing zones; hub-spoke or Virtual WAN; central identity, logging and policy; subscription vending so each app/environment gets a subscription with network, RBAC and policies pre-configured. Migration waves starting with low-risk apps. Everything in Terraform or Bicep."

**What the interviewer expects:** Knowledge of CAF/ALZ, vending, waves.

### A3. "Design zero-downtime deployments for a stateful legacy app on VMs."

**Model answer:** "First reduce state: move sessions to Redis, files to Storage. Then put VMs in a scale set or pools behind Application Gateway, and do rolling or blue-green: deploy new version to a new pool, health-check, switch the backend pool, keep the old pool for rollback. Database changes backward-compatible. Longer term, containerise or move to App Service."

**What the interviewer expects:** Pragmatism with legacy; state externalisation.

### A4. "Design secure access for developers to production for troubleshooting."

**Model answer:** "Read-only by default — Reader and resource-context log access. Elevation through PIM with MFA, justification and time limit; approval for high-privilege roles. Access to VMs via Bastion with Entra login, no public IPs. Kubernetes access via Entra and namespace-scoped roles. All actions logged and reviewed. Break-glass documented and monitored."

**What the interviewer expects:** Just-in-time, auditable, no standing privilege.

### A5. "How would you design for a 10× traffic event (e.g., a marketing campaign)?"

**Model answer:** "Capacity plan with load testing at 10× using Azure Load Testing; identify bottlenecks; pre-scale and raise autoscale limits and quotas; cache aggressively at Front Door and Redis; queue writes; protect dependencies with rate limits and circuit breakers; feature flags to turn off non-essential features; war room with dashboards and alerts; rollback plan; post-event review."

**What the interviewer expects:** Proactive capacity planning and graceful degradation.

## Part 4 — Behavioural and Leadership Questions (5)

> Answer with **your real stories** using STAR. The frameworks below show what a strong answer contains.

### B1. "Tell me about a major incident you handled."

**Strong answer contains:** Situation and impact (numbers), your role, the first actions (mitigation first), how you used data (specific tools), communication, the result (time to recover), and what you changed afterwards. Ends with a lesson learned.

**What the interviewer expects:** Calm, structured thinking; ownership; learning culture. Not blame.

### B2. "Tell me about a time you disagreed with a technical decision."

**Strong answer contains:** The decision, your concern backed by data, how you raised it respectfully, how the decision was made (maybe a PoC or ADR), and that you committed once decided — even if it didn't go your way.

**What the interviewer expects:** Influence without authority; professionalism.

### B3. "How have you improved a process or platform?"

**Strong answer contains:** The problem (cost, toil, risk), the change you led (automation, templates, policy), how you got adoption, and a measured result ("deployment time from 2 hours to 15 minutes", "alerts down 60%").

**What the interviewer expects:** Initiative and measurable impact.

### B4. "How do you mentor or support other engineers?"

**Strong answer contains:** A specific person/example, what you did (pairing, reviews, ownership), and how they grew.

**What the interviewer expects:** Genuine interest in others' growth — central for a senior role per the JD.

### B5. "This role works with UK-based teams. How do you handle that?"

**Model answer:** "I'm comfortable working UK business hours — currently that's 14:30 to 23:00 IST while the UK is on GMT — and joining incident bridges when needed. I communicate clearly in writing, confirm decisions in a summary after calls, state time zones explicitly, and raise risks early. I've \[mention any real experience working with distributed or international teams\]."

**What the interviewer expects:** Clear commitment to the hours and strong async communication.

## Mock Interview Self-Scoring

| **Area**    | **Weak signal**           | **Strong signal (5+ years)**                     |
|-------------|---------------------------|--------------------------------------------------|
| Structure   | Jumps between ideas       | Clarify → mitigate → investigate → fix → prevent |
| Specificity | "Check the logs"          | Names blades, tables, commands, error codes      |
| Safety      | Restarts/scales first     | Mitigates safely, preserves evidence             |
| Security    | Owner/keys as quick fixes | Least privilege, identities, no secrets          |
| Prevention  | Stops at the fix          | Adds alerts, automation, policy, runbooks        |
| Seniority   | Only own tasks            | Standards, mentoring, trade-offs, stakeholders   |
| Honesty     | Bluffs                    | "I haven't used X, but I'd approach it like…"    |

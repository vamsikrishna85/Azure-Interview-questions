# Azure DevOps Migration Engineer – 35 Scenario-Based Interview Questions & Answers

**Prepared for:** Reddi
**Author:** Reddi
**Role:** Azure DevOps Engineer – ADO project migration (discovery, extraction, validation, packaging, reconciliation, handoff)

> Note: "factory" in this JD means a **migration factory**, a repeatable, wave-based process for moving Azure DevOps projects. It has nothing to do with Azure Data Factory.
>
> How to use: each answer follows **Situation → Approach → Tools/Commands → Validation/Evidence**. Interviewers for this role want to hear *restartable, reconciled, secret-free, audit-ready*.

---

## Section A – Factory Design & Setup (Q1–Q6)

### Q1. You join on day one and are asked to design the migration "factory." What are its building blocks?
**Answer:**
I treat the factory as a repeatable pipeline with stages, not a set of one-off scripts:
1. **Intake/Discovery** – inventory of org/projects/assets via REST APIs; output a project profile (JSON + CSV).
2. **Pre-flight** – access checks, size estimates, blockers (LFS, huge repos, classic releases, custom processes).
3. **Extraction** – repos (mirror/bundle), work items + links + attachments, tests, Wikis, pipeline definitions, templates, metadata.
4. **Validation & Reconciliation** – source counts vs extracted counts, checksums, Git integrity.
5. **Packaging** – standard folder layout, manifest, SHA-256 checksums, version, secret scan.
6. **Handoff** – evidence pack, readiness checklist, customer sign-off.
7. **Support & Improvement** – defects feed back into automation backlog; metrics per wave.

Infrastructure: a factory Git repo (code + config + runbooks) with branch policies, self-hosted execution agents, Key Vault for credentials, staging storage, central logging. Every stage is idempotent and checkpointed, so any project can resume from its last good step.

### Q2. How would you structure the factory code repository and its branching controls?
**Answer:**
```
/src/discovery  /src/extract  /src/validate  /src/package  /src/common (auth, http, logging, retry)
/config (per-wave, per-project YAML)   /tests   /runbooks   /pipelines
```
- `main` protected: PR required, minimum 2 reviewers, build validation (linting, Pester/pytest), linked work item, no direct pushes.
- Short-lived feature branches; releases tagged (`factory-v1.4.0`) so every package records the exact factory version used to build it.
- Config separate from code; no secrets in config, only Key Vault secret *names*.

### Q3. How do you configure the execution agents?
**Answer:**
- Self-hosted agents (VM or VMSS) in a dedicated pool, sized for large clones (fast disk, enough space for mirrors plus packages).
- Tooling pinned: Git, Git LFS, PowerShell 7, Python version and required modules, az CLI.
- Agent identity is a **managed identity** to read Key Vault; no PATs stored on disk.
- Workspace cleaned after each job; staging on encrypted disk/Storage with restricted ACLs.
- Pool permissions limited to the factory project; capability tags (e.g., `bigdisk`) route large repos to the right agents.

### Q4. Which authentication model would you use, and why?
**Answer:**
- Preferred: **Entra ID service principal or managed identity** added to the ADO org with least-privilege (read-only access on source projects) and token acquired at runtime.
- Where PATs are unavoidable (some tools): minimal scopes (Code Read, Work Items Read, Build Read, Release Read, Test Read, Wiki Read), short expiry, stored in Key Vault, rotated per wave, owner documented.
- Never log tokens; mask them in pipeline variables; access reviews at wave end.

### Q5. What does your pre-flight validation check before a project enters a wave?
**Answer:**
- Credential can reach org/project; required permissions confirmed with a test call per API area.
- Asset counts and sizes (repos, largest repo, LFS usage, work item count, attachment volume, test plans, Wikis, pipelines).
- Process template (inherited/custom fields), classic vs YAML pipelines, disabled repos, forks.
- Disk/time estimate vs agent capacity.
- Known blockers flagged (repo > X GB, missing permissions, archived project).
Output: `preflight_<project>.json` with status `READY / READY_WITH_WARNINGS / BLOCKED` and reasons. Blocked projects never enter extraction.

### Q6. How do you define standards so different engineers produce identical packages?
**Answer:** Standard package layout, naming convention, manifest schema, logging format (structured JSON with correlation ID), exit codes, and a "definition of done" checklist. Templates and a shared `common` module enforce them in code, and a validation step fails any package that doesn't match the schema.

---

## Section B – Discovery & SDLC Analysis (Q7–Q11)

### Q7. A project has 40 repos, 200 pipelines and 15k work items. How do you analyze it as an application-delivery system?
**Answer:**
I map how code moves from idea to production:
- **Plan:** Boards, area/iteration paths, process template, custom fields.
- **Code:** repos, branch policies, default branches, submodules, LFS.
- **Build/Test:** YAML pipelines and their `resources`/`extends` templates (often in other repos), test plans and suites.
- **Release:** classic releases, environments, approvals/checks, deployment groups.
- **Dependencies:** service connections, variable groups, secure files, feeds, agent pools, Key Vault links.
I produce a dependency graph (pipeline → repo → template → service connection → environment) so the customer knows what must exist *before* anything can build or deploy.

### Q8. How do you find hidden cross-project dependencies?
**Answer:**
- Parse YAML for `resources.repositories`, `template: x@repo`, `extends`, `checkout`, cross-project pipeline triggers.
- Parse classic definitions for artifact sources from other projects.
- Check feeds (`nuget.config`, `npmrc`, `pip.conf`) for upstream feed URLs.
- Grep repos for org URLs, hard-coded hostnames, connection names.
- Use Analytics/REST to find work item links pointing to other projects.
These appear in the manifest as **external dependencies** with type and target.

### Q9. The customer asks, "What do we need to rebuild this app?" What do you deliver?
**Answer:** A dependency inventory per application: repos and default branches, pipeline definitions and templates, required service connection *names and types* (e.g., AzureRM → subscription ID/scope, no secret), variable group names plus variable names (secret values excluded, flagged as `isSecret`), environments and approvals, agent pool demands, feeds, secure files (names only), certificates/Key Vault references, DNS/network endpoints. The customer recreates and rewires; we supply everything except secrets.

### Q10. How do you discover all assets via REST APIs?
**Answer (key endpoints):**
- Projects: `_apis/projects`
- Repos: `{project}/_apis/git/repositories`, refs: `.../refs`
- Work items: WIQL `_apis/wit/wiql` then batch `_apis/wit/workitemsbatch` (200 IDs per call)
- Pipelines: `_apis/build/definitions`, releases: `vsrm.dev.azure.com/.../release/definitions`
- Tests: `_apis/testplan/plans`, suites, test cases
- Wikis: `_apis/wiki/wikis`
- Service connections: `_apis/serviceendpoint/endpoints`
- Variable groups: `_apis/distributedtask/variablegroups`
- Environments: `_apis/distributedtask/environments`
- Feeds: `feeds.dev.azure.com/.../_apis/packaging/feeds`

### Q11. WIQL returns an error for a project with 60k work items. Why, and how do you fix it?
**Answer:** WIQL caps results at 20,000. I split the query by ranges, e.g., `[System.Id] > lastId` ordered by ID, or by `ChangedDate` windows, loop until empty, then hydrate IDs in batches of 200 via `workitemsbatch`. I checkpoint the last ID processed so a restart continues from there.

---

## Section C – Automation Engineering (Q12–Q18)

### Q12. Show how you handle pagination with continuation tokens.
**Answer (PowerShell):**
```powershell
$items = @(); $token = $null
do {
    $uri = "$base/_apis/build/definitions?api-version=7.1&`$top=200"
    if ($token) { $uri += "&continuationToken=$token" }
    $resp = Invoke-WebRequest -Uri $uri -Headers $h -Method Get
    $items += ($resp.Content | ConvertFrom-Json).value
    $token = $resp.Headers['x-ms-continuationtoken']
} while ($token)
```
Some ADO APIs use `$top/$skip`, others the `x-ms-continuationtoken` header; the common module abstracts both so every extractor pages the same way.

### Q13. You start getting HTTP 429 and `Retry-After` headers. What do you do?
**Answer:** ADO uses TSTU-based rate limiting. I:
- Honour `Retry-After` exactly; also watch `X-RateLimit-Remaining` and slow down before hitting zero.
- Use exponential backoff with jitter for 429/5xx; no retry on 400/401/403/404.
- Limit concurrency per org (e.g., 4 parallel projects), and schedule heavy waves off-hours.
- Log throttling events as metrics to tune the wave plan.
```python
for attempt in range(max_retries):
    r = session.get(url, headers=h, timeout=60)
    if r.status_code in (429, 500, 502, 503, 504):
        wait = int(r.headers.get("Retry-After", 2 ** attempt)) + random.uniform(0, 1)
        log.warning("throttled", extra={"url": url, "wait": wait}); time.sleep(wait); continue
    r.raise_for_status(); return r.json()
raise RuntimeError(f"Retries exhausted: {url}")
```

### Q14. Extraction of a large project fails at hour 5. How did you design it to be restartable?
**Answer:**
- Each project has a **checkpoint file** (JSON) recording completed stages and last processed IDs per asset type.
- Each unit of work (one repo, one batch of 200 work items, one attachment) is idempotent: writes go to a temp path then rename atomically; existing files with matching checksums are skipped.
- On restart, the orchestrator reads the checkpoint and resumes. No duplicates, no full rerun.
- Failed items go to an exception list for targeted retry rather than blocking the run.

### Q15. How do you design logging and exception handling?
**Answer:** Structured JSON logs (timestamp, wave, project, stage, asset, correlation ID, duration, status, error), shipped to central storage/Log Analytics. Errors classified as **transient** (retry), **access** (escalate), **data** (exception list), **fatal** (stop project). Every run ends with a summary: processed / succeeded / skipped / failed. Secrets masked by a log filter.

### Q16. How do you download work item attachments reliably?
**Answer:** Get relations with `$expand=relations`, filter `rel == AttachedFile`, download by URL with the same retry wrapper, stream to disk, compute SHA-256, record original name, size, work item ID and checksum in an attachment manifest. Sanitize file names (illegal characters, long paths) but keep the original name in metadata. Reconcile: attachment relations count = downloaded files count.

### Q17. What would you unit/integration test in the factory?
**Answer:** Pester/pytest for pagination logic (mocked multi-page responses), retry behaviour on 429/503, manifest generation, checksum calculation, secret-scan rules (positive and negative samples), and a nightly integration run against a seeded sandbox project with known counts. Tests run as PR build validation.

### Q18. Someone wants to run extraction scripts from their laptop "just this once." Your response?
**Answer:** No. Runs must happen on approved agents with approved identities so logs, evidence and access controls stay consistent. A laptop run breaks the audit trail and risks credentials and data on unmanaged devices. I'd help them queue the official pipeline or a targeted re-run instead.

---

## Section D – Repository Extraction & Git Integrity (Q19–Q23)

### Q19. How do you extract a repo with full history, branches and tags?
**Answer:**
```bash
git clone --mirror https://dev.azure.com/org/proj/_git/repo repo.git
cd repo.git
git lfs fetch --all          # if LFS is used
git fsck --full
git bundle create ../repo.bundle --all
git bundle verify ../repo.bundle
```
Mirror captures all refs; bundle produces one portable file for the package. I record branch and tag counts, default branch, HEAD SHAs per branch, and bundle checksum.

### Q20. How do you prove the extracted repo matches the source?
**Answer:**
- Compare `git ls-remote` of the source with `git show-ref` of the mirror: same refs, same SHAs.
- Compare commit counts per branch: `git rev-list --count <branch>`.
- `git bundle verify` passes, and a clone from the bundle reproduces identical refs.
- SHA-256 of the bundle recorded in the manifest.
Results go into a reconciliation report with pass/fail per repo.

### Q21. A repo uses Git LFS and the clone from the bundle has pointer files only. What happened?
**Answer:** Bundles don't carry LFS objects. I must `git lfs fetch --all` and package the LFS object store separately (or as an archive) with its own checksum, and document the restore step (`git lfs push --all` to the target). Pre-flight should flag LFS repos so this never surprises the customer.

### Q22. Mirror clone of a 30 GB repo keeps failing midway. How do you troubleshoot?
**Answer:** Check agent disk and network timeouts; increase `http.postBuffer` is irrelevant for fetch, so instead try `git clone --mirror` with retries, or fetch incrementally by refs (`git fetch origin refs/heads/*:refs/heads/*` in batches), or use a shallow then `--unshallow`. Check for huge binaries/LFS misuse. Route to a big-disk agent. Document the repo as an exception with root cause.

### Q23. After extraction, the customer says a tag is missing. Investigation steps?
**Answer:** Check the source refs at extraction time (our logged `ls-remote` snapshot), check if the tag was created after extraction (delta), check whether it was an annotated vs lightweight tag issue, or a ref outside `refs/tags`. If it existed at extraction and is missing, it's a factory defect: fix, produce a **corrected package** with incremented version, and add a reconciliation check that would have caught it.

---

## Section E – Work Items, Tests, Wikis & Pipelines (Q24–Q28)

### Q24. How do you extract work items so links and history survive?
**Answer:** Export fields, revisions (`/workitems/{id}/revisions`) or updates, relations (parent/child, related, predecessor, hyperlinks, commit/PR artifact links), comments, attachments. Store as JSON per work item plus CSV summary. Record source IDs so the target can remap. Reconcile counts by type and state, link counts by type, and attachment counts.

### Q25. Identity and field mapping issues: users have left the company and custom fields exist in a custom inherited process. How do you handle it?
**Answer:** Export the process definition (work item types, fields, states, picklists, rules). Produce a **field mapping file** (source → target, data type) and an **identity mapping file** (source UPN → target UPN, with a default "migration user" for departed users, original name preserved in a field or comment). The customer approves mappings before import; mismatches are logged, never silently dropped.

### Q26. How do you extract Test Plans?
**Answer:** Plans → suites (static, requirement-based, query-based) → test cases (which are work items with steps XML) → shared steps and parameters → points/configurations. Results history is optional by agreement. Reconcile counts at each level. Requirement-based suites depend on work item links, so they must stay consistent with the work item extraction.

### Q27. How do you extract Wikis?
**Answer:** Project wikis are backed by a hidden Git repo (`<project>.wiki`); code wikis are normal repos. Mirror/bundle the backing repo, including `.attachments` and `.order` files. Validate page count and attachment count against the Pages API. Note internal links that reference work items or other projects as dependencies.

### Q28. How do you extract classic release pipelines vs YAML pipelines?
**Answer:**
- **YAML:** the definition lives in the repo; export the build definition JSON (triggers, variables, repo binding, agent pool) plus the referenced templates.
- **Classic build/release:** export definition JSON via REST (build and vsrm endpoints), including task groups (versions), stages, approvals, gates, artifact sources.
- Strip or mask anything secret; record service connection references by ID and name.
Note for the customer: classic releases often need conversion to YAML or re-import plus manual rewiring of connections and approvals.

---

## Section F – Dependencies & Secrets (Q29–Q30)

### Q29. How do you inventory service connections, variable groups and secure files without exporting secrets?
**Answer:**
- Service connections: name, type, auth scheme, Azure subscription/scope or URL, which pipelines use them. Never credentials.
- Variable groups: names, variable names, `isSecret` flag, Key Vault-linked or not, linked KV name. Secret values are always null in the API and we never try to get them.
- Secure files: names and which pipelines reference them, not content.
- Environments, approvals/checks, agent pools/demands, feeds and upstreams, certificates (name, thumbprint, expiry, KV location), DNS/network endpoints.
All go into `dependencies.json` and a human-readable `DEPENDENCIES.md`.

### Q30. During packaging the secret scan finds a connection string in a repo's history. What do you do?
**Answer:** Stop that package. Don't rewrite customer history unilaterally. Log a security finding, notify the security lead and the customer per process, and record it in evidence. Options agreed with the customer: rotate the credential (always recommended), and either accept the history as is (secret already compromised and rotated) or have the customer approve a history rewrite. The package proceeds only with documented approval. Then add the pattern to the scan rules.

---

## Section G – Packaging, Reconciliation & Handoff (Q31–Q33)

### Q31. What goes into a package manifest?
**Answer:**
```json
{
  "packageId": "PRJ-ALPHA", "version": "1.2.0", "type": "corrected",
  "factoryVersion": "factory-v1.4.0", "extractedUtc": "2026-11-06T06:00:00Z",
  "source": { "org": "contoso-src", "project": "Alpha" },
  "assets": [
    { "type": "repo", "name": "api", "file": "repos/api.bundle", "sha256": "…", "branches": 14, "tags": 22 },
    { "type": "workitems", "count": 15234, "attachments": 3120 }
  ],
  "reconciliation": { "status": "PASS", "report": "evidence/reconciliation.csv" },
  "secretScan": { "status": "PASS", "tool": "…", "findings": 0 },
  "previousVersion": "1.1.0", "changes": "Added missing tag v3.2.1"
}
```
Plus `checksums.sha256` covering every file, and a package-level hash.

### Q32. The customer needs updates two weeks after the first package because the source team kept working. How do you do a delta package?
**Answer:** Use the extraction timestamp and checkpoint as the baseline. Repos: fetch new refs and produce an incremental bundle (`git bundle create delta.bundle --all ^<old-sha>...`) or a full new bundle. Work items: WIQL `ChangedDate > baseline`. Pipelines: compare definition revisions. Package as type `delta` with `baseVersion` in the manifest, so the customer applies it in order. Reconcile delta counts separately.

### Q33. What is "handoff ready" in your definition?
**Answer:** All assets extracted; reconciliation PASS (or exceptions approved); checksums generated and verified by re-reading; secret scan PASS; manifest valid against schema; dependency inventory and rebuild/rewire guide included; evidence pack (logs, reports, approvals) attached; package versioned and stored in the controlled location; customer notified with the checksum so they can verify on receipt.

---

## Section H – Support, Troubleshooting & Communication (Q34–Q35)

### Q34. Mid-wave, 30 projects fail with 401 at the same time. Walk through L1/L2 triage.
**Answer:**
- **L1:** same error everywhere at the same time means a shared cause, not project data. Check credential expiry (PAT/secret), Key Vault access for the agent identity, conditional access policy changes, org policy changes, service health.
- **L2:** reproduce with a single authenticated call from the agent; inspect token claims; check whether the SP/user was removed from the org or its license changed.
- Fix (rotate secret, restore access), then resume from checkpoints, no full reruns.
- Communicate: incident note with impact, root cause, ETA; then add pre-flight credential-expiry check and an alert 14 days before expiry.

### Q35. A customer engineer says, "Your package is broken – the pipeline won't build." How do you handle it?
**Answer:**
1. Get specifics: pipeline, error, log, target setup.
2. Check whether it's a **package gap** (missing template, file, tag) or a **rewiring gap** (service connection not created, variable group missing, agent pool demand not met, feed upstream not configured).
3. Verify against our manifest and dependency inventory. Most often the dependency is listed but not yet recreated, so I point to it and explain clearly, without blame.
4. If it's our gap: corrected package, root cause, and a new reconciliation check.
5. Track all such issues; recurring patterns become automation improvements or better documentation (e.g., a pre-built "rewire checklist" per pipeline).

---

## Quick Revision – Phrases to Use in the Interview
- "Every step is **idempotent and checkpointed**, so restarts resume rather than rerun."
- "We **reconcile source to package** with counts, ref SHAs and checksums, and keep evidence."
- "We **inventory dependencies, never export secrets**."
- "Packages are **versioned with manifests**; corrections and deltas are new versions, never silent edits."
- "Recurring support issues become **automation backlog items**."

## Topics to Brush Up Before the Interview
- ADO REST API rate limits (TSTU) and continuation tokens
- `git clone --mirror`, `git bundle create/verify`, `git fsck`, LFS behaviour
- WIQL 20k limit and `workitemsbatch`
- Inherited process customization and field/identity mapping
- Classic release vs YAML (environments, checks, approvals)
- Microsoft's migration tooling options (e.g., Data Migration Tool for Azure DevOps Server → Services, open-source work item migrators) and when each applies
- Terraform basics, Docker/K8s pipeline patterns, SonarQube/Checkmarx integration in pipelines

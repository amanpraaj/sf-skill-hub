# SF Skill Hub

Centralized Salesforce AI skill hub with single-file auto-routing for Codex and Claude.

## Quick Navigation
- [Start in 30 Seconds](#start-in-30-seconds)
- [How It Works](#how-it-works)
- [Repository Structure](#repository-structure)
- [Interactive Prompt Examples](#interactive-prompt-examples)
- [Routing Transparency](#routing-transparency)
- [Create Repo + Push](#create-repo--push)
- [Maintenance](#maintenance)

## Start in 30 Seconds
1. Tag only this file in your AI tool:
- `./router/SKILL.md`

2. Send your normal Salesforce prompt.

3. Router auto-selects and runs the best specialist skill.

Copy-ready starter prompts:
```text
Create a record-triggered flow for renewal reminders.
```
```text
Generate Apex service and tests for lead dedupe.
```
```text
Deploy metadata to UAT and validate permissions.
```

## How It Works
1. Router reads `./manifests/SALESFORCE_SKILLS_MANIFEST.json`.
2. It scores skills using exact match, aliases, category match, and avoid penalties.
3. It selects the best skill path under `./skills/salesforce/...`.
4. It executes selected skill workflow and loads references only when needed.

## Repository Structure
- `./router/SKILL.md`
  Single entrypoint to tag in Codex/Claude.

- `./manifests/SALESFORCE_SKILLS_MANIFEST.json`
  Machine routing source of truth.

- `./manifests/SALESFORCE_SKILLS_MANIFEST.yaml`
  YAML mirror for readability.

- `./manifests/SALESFORCE_SKILLS_MANIFEST.md`
  Human-readable manifest companion.

- `./manifests/ROUTER_PROMPT.md`
  Deterministic routing logic template.

- `./skills/salesforce/`
  All specialized Salesforce skills.

## Interactive Prompt Examples
Use these directly, then iterate.

### Flow + Validation
```text
Create a before-save flow for Account to normalize phone format and add a validation rule for invalid country code.
```

### Apex + Agentforce
```text
Create an invocable Apex class for order eligibility and wire it into an Agentforce action with test coverage.
```

### Metadata + Deploy
```text
Generate custom object, fields, page layout, permission set, then deploy to UAT with a validation checklist.
```

### Incident + Rollback
```text
Analyze failed production deployment, classify root cause, and provide rollback-first recovery steps.
```

## Routing Transparency
Ask these when you want explainability:
```text
Show selected skill and why.
```
```text
Show top 2 candidate skills with confidence.
```
```text
Show execution stages for this multi-domain task.
```

## Create Repo + Push
If this is a brand new GitHub repo:

```bash
git init
git add .
git commit -m "Initial SF Skill Hub"
git branch -M main
git remote add origin https://github.com/<you>/sf-skill-hub.git
git push -u origin main
```

If remote already exists:

```bash
git remote set-url origin https://github.com/<you>/sf-skill-hub.git
git push -u origin main
```

## Maintenance
When adding/updating skills:
1. Update files in `./skills/salesforce/...`
2. Regenerate manifest JSON
3. Regenerate YAML and MD mirrors
4. Keep router paths aligned with manifest

## License
Use repository license and upstream licenses where applicable.

## Appendix

### A. Path Cheat Sheet
- Router skill to tag:
`./router/SKILL.md`

- Primary machine manifest:
`./manifests/SALESFORCE_SKILLS_MANIFEST.json`

- YAML manifest:
`./manifests/SALESFORCE_SKILLS_MANIFEST.yaml`

- Human-readable manifest:
`./manifests/SALESFORCE_SKILLS_MANIFEST.md`

- Specialized skills root:
`./skills/salesforce/`

### B. Routing Output Template
Use this response shape when exposing router decisions:
```text
selected_skill: ./skills/salesforce/<skill-name>
reason: <short rationale>
confidence: high|medium|low
execution_summary: <what was executed>
```

### C. Prompt Writing Tips
- Start with business goal + Salesforce artifact.
- Add environment target (dev/qa/uat/prod).
- Mention constraints (security, performance, deadlines).
- Ask for staged output when task spans multiple domains.

Example:
```text
Build a UAT-ready lead qualification flow with Apex fallback logic and permission updates; include deploy validation steps.
```

### D. Troubleshooting
- Router picked wrong skill:
Ask: `Show top 2 candidate skills with confidence.`

- Multi-domain task feels incomplete:
Ask: `Run staged execution: metadata -> build -> validate -> deploy.`

- Manifest seems stale:
Regenerate manifest JSON/YAML/MD from current `./skills/salesforce/`.

### E. Suggested GitHub Topics
`salesforce`, `agentforce`, `apex`, `flow`, `metadata-api`, `devops`, `llm`, `ai-agents`, `prompt-engineering`, `automation`

### F. Source Repositories Used
This hub was assembled from the following repositories.

1. Official Salesforce skills library
- Repo: `https://github.com/forcedotcom/afv-library`
- Used for: core Salesforce official skill set
- Mapped into: `./skills/salesforce/*` (official skills)

2. Community Salesforce skills
- Repo: `https://github.com/Jaganpro/sf-skills`
- Used for: expanded community skill coverage
- Mapped into: `./skills/salesforce/*` (deduplicated)

3. Community Claude-oriented Salesforce skills
- Repo: `https://github.com/Jaganpro/claude-code-sfskills`
- Used for: Claude-compatible Salesforce skill variants
- Mapped into: `./skills/salesforce/*` (deduplicated)

Notes:
- Duplicate skill folders were removed by name and content-hash checks.
- Manifest files in `./manifests/` reflect the final deduplicated set.

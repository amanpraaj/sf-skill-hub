---
name: salesforce-auto-router
description: Universal Salesforce skill entrypoint. Use when the user asks any Salesforce-related task (metadata, Apex, Flow, LWC, Agentforce, deploy, testing, data, permissions). This skill auto-routes to the best specialized skill using ../manifests/SALESFORCE_SKILLS_MANIFEST.json and executes the selected skill workflow.
---

# Salesforce Auto Router

## Objective
Route every Salesforce request to the best specialized skill automatically, then execute that skill.

## Inputs
- User prompt
- Manifest: `../manifests/SALESFORCE_SKILLS_MANIFEST.json`
- Skills root: `../skills/salesforce/`

## Routing
1. Load manifest JSON.
2. Parse user prompt into normalized terms.
3. Score skills using manifest routing policy.
4. Select highest score.
5. If tie within 1 point, keep primary + secondary.
6. For multi-domain tasks, sequence:
metadata -> apex/flow -> ui -> testing-observability -> deployment -> agentforce

## Execute
1. Open selected skill: `../skills/salesforce/<skill-name>/SKILL.md`
2. Follow selected skill instructions.
3. Load only required `references/`, `scripts/`, and `assets/`.

## Output
- selected_skill
- reason
- confidence
- execution_summary

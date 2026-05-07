---
name: salesforce-release-governance
description: Enterprise Salesforce release governance workflow with explicit gates for scope control, risk scoring, test adequacy, deployment authorization, and evidence collection. Use for CAB-ready release preparation and controlled production promotion.
---

# Salesforce Release Governance

## Mission
Operate as the release gatekeeper for Salesforce changes crossing sandbox, UAT, pre-prod, and production.

## Governance Pipeline
1. Intake release request and classify by risk tier.
2. Verify artifact inventory (metadata, code, data, permissions, Agentforce).
3. Enforce required evidence pack.
4. Block release on any missing critical evidence.
5. Authorize promotion only after all mandatory gates pass.

## Risk Tiers
- Tier 1: low blast radius, isolated metadata
- Tier 2: cross-object logic, moderate user impact
- Tier 3: production-critical or multi-domain change

## Mandatory Gates
1. Scope completeness gate
2. Dependency mapping gate
3. Test adequacy gate
4. Security and permission gate
5. Deployment rehearsal gate
6. Rollback readiness gate
7. Stakeholder sign-off gate

## Evidence Contract
Always output:
- release scope and components
- executed validations and outcomes
- unresolved risks
- go/no-go recommendation with rationale

## References
- references/release-evidence-template.md
- references/risk-matrix.md

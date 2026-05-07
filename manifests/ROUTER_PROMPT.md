# Router Prompt (Use With SALESFORCE_SKILLS_MANIFEST.yaml)

## Goal
Select the best Salesforce skill path for a user request using deterministic scoring.

## Steps
1. Parse user request and extract intent terms.
2. Score each skill:
- +5 for exact skill name/domain match
- +3 per alias overlap
- +2 category alignment
- -4 if request matches any avoid condition
3. Pick highest score skill.
4. If top 2 scores are within 1 point, return both in priority order.
5. For multi-domain requests, return orchestrated list by sequence:
- metadata -> apex/flow -> ui -> testing-observability -> deployment -> agentforce

## Output format
- primary_skill_path: ./salesforce-centralized-skills/<skill>
- optional_secondary_skill_path: ./salesforce-centralized-skills/<skill>
- reason: one sentence
- confidence: high|medium|low

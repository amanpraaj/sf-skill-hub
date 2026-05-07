# Salesforce Skill Set

## Structure
- `./router/SKILL.md` : single file to tag in Codex/Claude
- `./manifests/SALESFORCE_SKILLS_MANIFEST.json` : machine routing source of truth
- `./manifests/SALESFORCE_SKILLS_MANIFEST.yaml` : YAML equivalent
- `./skills/salesforce/` : all specialized skill folders

## Use
1. Tag `./router/SKILL.md`
2. Prompt normally
3. Router auto-selects and runs the best Salesforce skill

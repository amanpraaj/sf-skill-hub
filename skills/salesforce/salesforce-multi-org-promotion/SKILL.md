---
name: salesforce-multi-org-promotion
description: Orchestrate Salesforce change promotion across multiple orgs with consistency checks, delta validation, promotion sequencing, and environment parity control. Use for enterprise pipelines with Dev, QA, UAT, and Prod orgs.
---

# Salesforce Multi-Org Promotion

1. Build org topology map.
2. Detect metadata drift before promotion.
3. Promote in dependency-safe order.
4. Validate each hop before next promotion.
5. Keep promotion ledger with deployment IDs.


## References
- references/promotion-sequence.md
- references/drift-detection-checks.md

---
name: backlog-refinement
description: Use when backlog refinement or estimation needs an evidence-based Jira story-point assessment.
---

# Backlog Refinement

Scope: refine and estimate existing Jira work only.

## Gather Evidence

For a directed Jira issue, fetch the direct Jira key with Jira lookup. To
discover related issues or context, use Rovo Search. Use JQL only when explicitly asked.
After Jira evidence, inspect relevant local repositories; do not substitute repository 
guesses for Jira evidence.

Never invent a numeric estimate when evidence is unavailable. State the
missing evidence instead.

## Estimate And Update Fields

Initial refinement: select an estimate and write it to both `Original Story Points` and `Story Points`.

Mid-release re-estimation: preserve `Original Story Points`, update only `Story Points`, and explain the delta from the original estimate.

When the request includes `--dry-run`, gather and assess evidence normally but make no Jira edits. 
For every ticket, report the proposed estimate or blocked result, intended Jira field action, and rationale.

For a multi-ticket set, include every ticket and use the full scale `1, 2, 3, 5, 8, 13, 21, Bust`.
Before comparing the set, identify which stories have sufficient evidence, then pick the
smallest and largest of those as anchors. There are no valid anchors with fewer than two
understood stories; report that evidence gap rather than assigning numeric estimates.

For one concise story, use only `1, 2, 3, 5, 8`. When evidence is insufficient,
output `Estimate blocked` with exactly two rationale bullets:

```text
Estimate blocked
- Missing evidence: <specific Jira or repository evidence needed>
- Missing evidence: <specific Jira or repository evidence needed>
```

## Output

For every ticket, report:

```text
<TICKET-KEY>: <estimate or Estimate blocked>
- Jira field action: <fields written, or "none (--dry-run)">
- Rationale: <evidence-based reasoning, or the two missing-evidence bullets>
```

For a mid-release change, add a line with the original and new `Story Points` values and
the delta explanation.

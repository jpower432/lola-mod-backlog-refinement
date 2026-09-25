---
description: Refine and estimate one or more Jira tickets using evidence-based story points.
argument-hint: "<ticket-key> [ticket-key...] [--dry-run]"
---

Invoke the backlog-refinement skill for the given ticket key(s). If none are given, ask the user for this information.

1. Treat each `PROJ-123`-style token in the arguments as a ticket key to refine and estimate.
2. If `--dry-run` is present, gather and assess evidence normally but make no Jira edits.
3. If the request also states scope changed on an already-estimated ticket, treat it as
   mid-release re-estimation: preserve `Original Story Points`, update only `Story Points`.
4. Follow the skill's evidence-gathering, estimation, and output rules exactly.

Arguments from user: $ARGUMENTS

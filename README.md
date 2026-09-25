# backlog-refinement

A [Lola](https://docs.getlola.dev/) module for evidence-based backlog refinement
and Jira story-point estimation. It activates when an agent encounters `backlog`
or `estimation`, or via the `/estimate` slash command.

## Install

```bash
# One time:
uv tool install git+https://github.com/LobsterTrap/lola

# From this repository:
lola mod add --name backlog-refinement backlog-refinement
lola install backlog-refinement -a claude-code --scope user

# Or use Task:
task install ASSISTANT=opencode SCOPE=project
```

## Examples

### Initial refinement

Ask: "Refine the backlog item PROJ-123 and estimate it."

The skill fetches `PROJ-123`, discovers context with Rovo Search as needed,
then inspects a relevant local repository. With sufficient evidence, it reports
the rationale and writes the selected value to both `Original Story Points` and
`Story Points`.

### Mid-release re-estimation

Ask: "The backlog scope of PROJ-123 changed; re-estimate it."

The skill gathers current Jira and repository evidence, preserves `Original
Story Points`, updates only `Story Points`, and explains the delta. If evidence
is insufficient, it returns `Estimate blocked` with exactly two rationale
bullets instead of inventing a number.

### Dry run

Run `/estimate PROJ-123 --dry-run`, or ask: "Refine PROJ-123 and estimate it --dry-run."

The skill gathers and assesses the same evidence, then reports the proposed
estimate, intended Jira field action, and rationale without making Jira edits.

> Requires https://github.com/atlassian/atlassian-mcp-server
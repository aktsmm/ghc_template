# Prompt: Review Agents & Instructions

Prompt for reviewing agent definitions (.agent.md) and instruction files (.github/instructions/**/*.md) with cross-reference validation against project assets.

## Step 0: Context Collection (Do First)

Read the following files before reviewing:

- [ ] `README.md` — Project overview and purpose
- [ ] `AGENTS.md` — Agent registry and role definitions
- [ ] `.github/agents/*.agent.md` — All agent definitions
- [ ] `.github/instructions/**/*.md` — Shared rules and constraints
- [ ] `.github/copilot-instructions.md` — Global guardrails

## Design Principles Checklist

### Tier 1: Core Principles (Required)

- [ ] **SRP**: Is it 1 agent = 1 responsibility?
- [ ] **SSOT**: Is information centrally managed?
- [ ] **Fail Fast**: Can errors be detected early?

### Tier 2: Quality Principles (Recommended)

- [ ] **I/O Contract**: Are inputs/outputs clearly defined?
- [ ] **Done Criteria**: Are completion conditions verifiable?
- [ ] **Idempotency**: Is the design retry-safe?
- [ ] **Error Handling**: Is error handling documented?

### Structure Check

- [ ] Is Role clear in one sentence?
- [ ] Are Goals specific?
- [ ] Are Permissions minimal?
- [ ] Is Workflow broken into steps?

## Cross-Reference Validation

- [ ] Does AGENTS.md role description match .agent.md Role section?
- [ ] Are prohibited operations (from instructions) not granted in Permissions?
- [ ] No duplicate information between AGENTS.md and .agent.md? (SSOT)
- [ ] Does workflow align with project context described in README.md?
- [ ] Does workflow respect dependencies defined in other agents?

## Instructions File Review (`.github/instructions/**/*.md`)

### SSOT Validation

- [ ] No duplicate definitions (e.g., page allocation tables, keyword guidelines) across multiple files?
- [ ] Definitions consolidated in one place with references elsewhere?
- [ ] No rule duplication between AGENTS.md and instructions?

### Consistency Check

- [ ] MCP tool names are correct? (e.g., `mcp_microsoftdocs_*`)
- [ ] File reference paths exist?
- [ ] No contradictions with other instructions?

### Maintainability

- [ ] Each file under 200 lines? (Consider splitting if exceeded)
- [ ] Template sections separated into dedicated files?
- [ ] Proper balance between explanations and references?

## Output Format

```markdown
## Review Result

### ✅ Good Points

- [Good points]

### ⚠️ Improvements Needed

- [Improvement points]

### Recommendation

[Overall evaluation and recommended actions]
```

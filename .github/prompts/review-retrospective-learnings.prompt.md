# Prompt: Agent Design Retro

Extract reusable design insights from events (incident response, errors, fix PRs, conversations)
and reflect them in design assets for prevention and quality improvement.

## Input

- Response history (timeline, logs, error messages, fixes)
- Terminal history (commands executed, outputs, errors)
- Git changes (diff, commit messages)
- **Chat context (conversation history, Q&A exchanges, problem-solving threads)**
- Scope of reflection (Agents.md / \*.agent.md / instructions)

## Steps

### Step 0: Context Collection

1. Read target files:
   - README.md
   - AGENTS.md
   - .github/agents/\*.agent.md
   - .github/instructions/\*.md
   - .github/copilot-instructions.md
2. Summarize existing rules in 5 lines or less

**Example:**

```
Existing rules summary:
- SRP: 1 agent = 1 responsibility
- No git push without confirmation
- Error handling must be explicit
- Idempotency required for all operations
```

### Step 1: Extract Learnings

Identify insights at these levels:

- Design principle (separation of concerns, idempotency)
- Workflow (call order, preconditions, error handling)
- Prompt patterns (effective phrasing, tool usage)

Format: `Learning` → `Evidence` → `Impact`

**Example:**

```
Learning: Break complex tasks into numbered steps
Evidence: Multi-step request succeeded when numbered vs. failed as prose
Impact: Add "numbered steps" pattern to prompt guidelines
```

### Step 2: Decide Action & Target

**Action decision:**
| Frequency | Severity | Action |
|-----------|----------|--------|
| Once | Low | Document in PR only |
| Once | High | Add to specific agent |
| Multiple | Any | Generalize to instructions |
| Chat insight | Reusable | Add to prompts or instructions |

**Target mapping:**
| Learning Type | Target File |
|---------------|-------------|
| Common principle | AGENTS.md |
| Agent-specific | .github/agents/\*.agent.md |
| Workflow rule | .github/instructions/\*.md |
| Prompt pattern | .github/prompts/\*.prompt.md |

### Step 3: Propose Changes

Show exact content to add/replace in code blocks.

Verify before proposing:

- No duplicate rules
- Consistent with existing design
- Minimal and focused change

## Output Format

```markdown
# Retro: [Title]

## Learnings

- **Learning**: [What was learned]
  - Evidence: [What happened]
  - Action: [Generalize / Individual / Strengthen] → [target file]

## Changes

\`\`\`markdown
[Exact content to add/replace]
\`\`\`
```

---
applyTo: ".github/agents/**"
---

# Agent Instructions

Rules applied when editing files in the `.github/agents/` directory.

## Agent Definition Structure

```markdown
# Agent: {name}

## Role
Describe the agent's role in one sentence

## Responsibilities
- Responsibility 1
- Responsibility 2

## Input
- input1: Description

## Output
- output1: Description

## Constraints
- Constraint details
```

## Best Practices

1. **1 Agent = 1 Responsibility** - Split if there are multiple responsibilities
2. **Clear I/O** - Avoid ambiguous definitions
3. **Explicit Constraints** - Consider edge cases

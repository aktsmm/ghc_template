---
applyTo: ".github/agents/**/*.agent.md"
---

# Agent Workflow Design Instructions

## Part 1: Agent Design Principles

### 1. Single Responsibility Principle (SRP)

- **1 Agent, 1 Goal**: Give each agent one clearly defined role.
- **Separation of Roles**: Separate by phase: "planning", "implementation", "review", "testing".

### 2. Stateless & Idempotency

- Design agents to judge based on file system state, not conversation history.
- Design workflows to converge to correct state when re-run.

### 3. Orchestration

- For complex tasks, use "manager agent" delegating to "worker agents".
- Clearly define expected deliverables for handoffs.

### 4. Fail-safe & Human-in-the-loop

- Before irreversible operations, ask human confirmation.
- Design prompts to analyze errors and attempt fixes.

### 5. Observability

- Record decisions as Issue comments or documents.
- For long tasks, have regular status reports.

## Part 2: Workflow Architecture

### 6. Two-stage Architecture

Input → IR (Intermediate Representation) → Output

### 7. IR Specification

- Define allowed structure (JSON/YAML/structured Markdown)
- Strict validation; do not auto-complete

### 8. Separation of Concerns

| Responsibility | Description            |
| -------------- | ---------------------- |
| Generate       | Generate IR            |
| Validate       | Verify IR              |
| Transform      | Convert IR to output   |
| Render         | Output to final format |

### 9. Determinism

Same IR → Same output. No creativity in transformation.

## Part 3: Agent Manifest Specification

### 10. YAML Front Matter Requirements

エージェント定義ファイル（`.agent.md`）には以下の YAML front matter が必須：

```yaml
---
name: <agent-name> # 必須: @メンション用の識別子
description: <description> # 必須: 1行での役割説明
model: <model-name> # 必須: 使用するLLMモデル
---
```

### 11. Tools Field Specification

| 記載方法       | 動作                                         |
| -------------- | -------------------------------------------- |
| **省略**       | すべてのツールが利用可能（推奨）             |
| `tools: []`    | ツールなし                                   |
| ツール名を列挙 | 指定したツールのみ利用可能（ホワイトリスト） |

> **注意**: MCP ツールは実行時に自動的に利用可能になるため、front matter への明示は不要。不明なツール名を記載するとエラーになる。

### 12. Agent Structure Template

各エージェントは以下のセクションを持つ：

| セクション     | 必須 | 説明                                 |
| -------------- | ---- | ------------------------------------ |
| Role           | ✅   | 1 文での責任定義                     |
| Goals          | ✅   | 達成目標のリスト                     |
| Done Criteria  | ✅   | 検証可能な完了条件（**1 箇所のみ**） |
| Permissions    | ✅   | 許可/禁止事項                        |
| I/O Contract   | ✅   | 入出力の定義                         |
| Workflow       | 推奨 | ステップ分けした作業手順             |
| Error Handling | 推奨 | エラーパターンと対応                 |
| Idempotency    | 推奨 | 冪等性の保証方法                     |

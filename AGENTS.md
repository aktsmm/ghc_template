# AGENTS

このリポジトリにあるすべての構造化エージェントをまとめた中央レジストリです。各エントリは `.github/agents` 配下のマニフェストへリンクしています。

> `sample.agent.md` が最小構成の例、`orchestrator.agent.md` がオーケストレーター構成の例です。テンプレ用途で増やすときはここに行を追加してください。

| エージェント名     | マニフェスト                           | 主な役割                             |
| ------------------ | -------------------------------------- | ------------------------------------ |
| Sample Agent       | `.github/agents/sample.agent.md`       | エージェント定義のテンプレート       |
| Orchestrator Agent | `.github/agents/orchestrator.agent.md` | サブエージェントを統括する司令塔の例 |

## 使い方

1. タスクに最も近いエージェントを選び、Copilot Chat で対応するマニフェストを読み込む（例: `/agent sample`）。
2. `.github/copilot-instructions.md` の共通ルールと、エージェント固有ガイドを組み合わせて使用する。
3. 新しいエージェントを追加する場合は、このテーブルに行を追加し、`.github/agents/` にマニフェストを配置する。

## 関連アセット

### 共有ガードレール

- [copilot-instructions.md](.github/copilot-instructions.md) — Copilot の振る舞い・回答スタイル・検証手順を定義

### Instructions（ドメイン別ルール）

| ファイル                                                                              | 説明                                                           |
| ------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| [git.instructions.md](.github/instructions/git.instructions.md)                       | Git コミット規約（Conventional Commits、Push 禁止）            |
| [terminal.instructions.md](.github/instructions/terminal.instructions.md)             | ターミナル操作規約（PowerShell 互換、破壊的操作の注意）        |
| [agent-design.instructions.md](.github/instructions/agent-design.instructions.md)     | エージェント設計原則（単一責任、冪等性、オーケストレーション） |
| [security.instructions.md](.github/instructions/security.instructions.md)             | セキュリティガイドライン（機密情報、外部 API、入力検証）       |
| [communication.instructions.md](.github/instructions/communication.instructions.md)   | コミュニケーションスタイル（結論ファースト、言語設定）         |
| [microsoft-docs.instructions.md](.github/instructions/microsoft-docs.instructions.md) | Microsoft 公式ドキュメント参照（MCP ツール活用、ソース明記）   |

### Prompts（再利用可能なプロンプト）

| ファイル                                                               | 説明                             |
| ---------------------------------------------------------------------- | -------------------------------- |
| [create-agent.prompt.md](.github/prompts/create-agent.prompt.md)       | 新規エージェント作成             |
| [review-agent.prompt.md](.github/prompts/review-agent.prompt.md)       | エージェント定義のレビュー・改善 |
| [plan-workflow.prompt.md](.github/prompts/plan-workflow.prompt.md)     | タスク実行計画                   |
| [design-workflow.prompt.md](.github/prompts/design-workflow.prompt.md) | ワークフロー設計                 |

### その他

- `.vscode/mcp.json` — VS Code MCP クライアントモードとの対応表

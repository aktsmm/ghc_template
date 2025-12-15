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

- `.github/copilot-instructions.md` — 共有ガードレール
- `.github/instructions/` — エージェントが取り込めるドメイン指示
  - [Agent Design Rules](.github/instructions/agent-design.instructions.md) — エージェント設計のベストプラクティス
  - [Security Rules](.github/instructions/security.instructions.md) — セキュリティガイドライン
  - [Communication Rules](.github/instructions/communication.instructions.md) — コミュニケーションスタイル
- `.github/prompts/` — ワークフロー向けの再利用可能なプロンプト
- `.vscode/mcp.json` — VS Code MCP クライアントモードとの対応表

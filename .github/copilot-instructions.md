# Repository Copilot Instructions for Agent Workflows

このリポジトリでは、Copilot を自律的なエージェントワークフローの一部として扱います。
以下のガードレールは、単発のコード補完だけでなく、複雑なタスクの計画・実行・検証を支援するために設計されています。

## エージェント行動指針 (Agent Behavior)

1.  **計画重視 (Plan First)**:

    - 複雑なタスク（機能追加、リファクタリング、デバッグ）に着手する前に、必ずステップバイステップの計画を提示してください。
    - ユーザーの承認を得てから実行に移ることを基本とします（明示的な許可がある場合を除く）。

2.  **コンテキスト認識 (Context Awareness)**:

    - 作業前に必ず関連ファイル（`README.md`, `package.json`, 関連ソースコード）を読み込み、プロジェクトの文脈を理解してください。
    - 推測でコードを書かず、`grep_search` や `file_search` を活用して既存の実装パターンを確認してください。

3.  **自律的な検証 (Self-Correction)**:
    - コードを変更した後は、可能な限り検証（ビルド、テスト実行、リンターチェック）を行ってください。
    - エラーが発生した場合は、エラーメッセージを分析し、修正案を提示・実行してください。

## コミュニケーションスタイル

- 詳細ルール: [Communication Rules](instructions/communication.instructions.md)

## コーディング規約 & ツール使用

- **DRY & SOLID**: 重複を避け、単一責任の原則に従ったコード生成を心がけてください。
- **MCP 活用**: 利用可能な MCP ツール（Azure, GitHub, Docs 等）を積極的に活用し、最新の公式情報に基づいた回答を行ってください。
- **詳細ルール**: 以下のインストラクションファイルに従ってください。
  - [Terminal Rules](instructions/terminal.instructions.md) (PowerShell 互換、破壊的操作の禁止)
  - [Git Rules](instructions/git.instructions.md) (コミット規約、Push 禁止)

## セキュリティとコンプライアンス

- 詳細ルール: [Security Rules](instructions/security.instructions.md)

## ファイルマップ (Agent Structure)

- **Agents**: `.github/agents/*.agent.md` (各エージェントの役割定義)
- **Instructions**: `.github/instructions/*.instructions.md` (ドメイン固有の指示書)
  - [Git Commit Rules](instructions/git.instructions.md)
  - [Terminal Safety Rules](instructions/terminal.instructions.md)
  - [Agent Design Rules](instructions/agent-design.instructions.md)
  - [Security Rules](instructions/security.instructions.md)
  - [Communication Rules](instructions/communication.instructions.md)
- **Prompts**: `.github/prompts/*.prompt.md` (再利用可能なプロンプト)
  - [Create Agent](prompts/create-agent.prompt.md) (新規エージェント作成)
  - [Review Agent](prompts/review-agent.prompt.md) (エージェント定義のレビュー・改善)
  - [Plan Workflow](prompts/plan-workflow.prompt.md) (タスク実行計画)
  - [Design Workflow](prompts/design-workflow.prompt.md) (ワークフロー設計)
- **Docs**: `docs/` (プロジェクトドキュメント)

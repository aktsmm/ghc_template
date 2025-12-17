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

- **結論ファースト**: 結論を先に述べ、その後に理由や詳細を記述する
- **日本語で回答**: ユーザーが日本語なら日本語で応答する
- 詳細ルール: [Communication Rules](instructions/communication.instructions.md)

## コーディング規約 & ツール使用

- **DRY & SOLID**: 重複を避け、単一責任の原則に従ったコード生成を心がけてください。
- **SSOT (Single Source of Truth)**: 情報は一箇所で管理し、他はそこを参照する。設定やドキュメントの重複を避け、変更時の不整合を防ぐ。
- **MCP 活用**: 利用可能な MCP ツール（Azure, GitHub, Docs 等）を積極的に活用し、最新の公式情報に基づいた回答を行ってください。
- **詳細ルール**: 以下のインストラクションファイルに従ってください。
  - [Terminal Rules](instructions/terminal.instructions.md) (PowerShell 互換、破壊的操作の禁止)
  - [Git Rules](instructions/git.instructions.md) (コミット規約、Push 禁止)

## セキュリティとコンプライアンス

- 詳細ルール: [Security Rules](instructions/security.instructions.md)

## ファイルマップ

エージェント一覧・関連アセットの詳細は [AGENTS.md](../AGENTS.md) を参照してください。

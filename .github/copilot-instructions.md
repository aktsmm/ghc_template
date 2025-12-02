# Repository Copilot Instructions

より詳細なエージェントマニフェストがある場合を除き、すべての Copilot Chat セッションで以下のガードレールを適用する。

## コミュニケーションスタイル

1. 余計な前置きよりも、簡潔で実行可能な返信を優先し、先にブロッカーを共有する。
2. 人間とのやりとりは日本語で返し、コードコメントはファイル指定がない限り英語のままにする。
3. コードを参照するときは必ずファイルパス（例: `src/api/server.ts`）を示す。

## コーディング規約

- 既存ファイルに Unicode 拡張が必要な場合を除き ASCII をデフォルトとする。
- PowerShell 互換のコマンド（`;` で連結し `&&` は禁止）を使う。
- 複雑なロジックや直感的でない判断に限ってコメントを最小限で追加する。

## テスト期待値

1. 挙動変更時には欠落しているユニットテストを指摘する。
2. 依存不足や不安定さでテストを実行できない場合はブロッカーを説明し、代替の検証手順を提案する。
3. 迅速なフィードバックのため、`npm run test -- api` のような対象テストコマンドを優先する。

## セキュリティとコンプライアンス

- 機密情報や個人情報をコミットしない。サンプル設定もマスキングする。
- インフラ議論では最小権限の IAM ロールを推奨する。
- ライセンスが不明なサードパーティコードを見つけたら必ず警告する。

## ファイルマップ

- Agents: `.github/agents/*.agent.md`
- Chat Modes: `.github/copilot-chat-modes/*.chatmode.md`
- Domain Instructions: `.github/instructions/*.instructions.md`
- Prompt Snippets: `.github/prompts/*.prompt.md`
- MCP Settings: `.vscode/mcp.json`

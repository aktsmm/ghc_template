# Template Repository

このリポジトリは GitHub Copilot × VS Code を使ったエージェント/モード開発の叩き台、テンプレートだよ。`.github` 配下には README とサンプル Markdown を 1 つずつ置いてあるから、必要に応じてコピーして使ってね。

> Inspiration: https://github.com/openjny/dotgh/blob/main/docs/user-guide.md — dotgh の方が高機能だから、本格的にテンプレートを量産したい場合はそっちのツールを使うと手っ取り早いよ。粋な OSS を公開してくれてマジ感謝。

## 収録内容

- `.github/copilot-instructions.md` — 共有ガードレール。Copilot が最初に読み込み、回答トーンやレビュー方針を決める。
- `.github/agents/` — `README.md` と `sample.agent.md`。新規エージェントを増やすときはこの例を複製。
- `.github/copilot-chat-modes/` — `README.md` と `sample.chatmode.md`。チャットモードの基本レイアウトを確認できる。
- `.github/instructions/` — ドメインガイド。`sample.instructions.md` を修正して用途別ルールを定義する。
- `.github/prompts/` — 再利用可能なプロンプト置き場。`sample.prompt.md` のフォーマットに沿って書き換える。
- `AGENTS.md` — 登録済みエージェントの目次。新しいマニフェストを追加したらここにも追記する。
- `.vscode/mcp.json` — MCP クライアント設定。例えば Microsoft Learn の MCP サーバー (`Docs`) を登録して、Copilot から公式ドキュメント検索ツールを使えるようにする。

## 使い方

1. 必要なカテゴリ（エージェント / チャットモード / インストラクション / プロンプト）でサンプルファイルをコピーする。
2. ファイル名と内容をユースケースに合わせて編集し、`AGENTS.md` や README からリンクを張る。
3. Copilot Chat 側で `/agent <name>` や `/mode <name>` を実行して期待通りに読み込めるか確認する。

> Copilot の話し方やレビュー順を変えたいときは `.github/copilot-instructions.md` を更新、自律タスクの流れや許可範囲を変えたいときは `AGENTS.md` を編集する。

### `.github/copilot-instructions.md` と `AGENTS.md` の違い

| 観点         | `.github/copilot-instructions.md`                      | `AGENTS.md`                                             |
| ------------ | ------------------------------------------------------ | ------------------------------------------------------- |
| 読む主体     | GitHub Copilot（補完/チャット/PR レビュー）            | Copilot Coding Agent や Codex などエージェント系ツール  |
| 役割         | 話し方・出力スタイル・レビュー順序を決める             | ビルド/テスト/デプロイ手順やタスク境界を定義            |
| 適用範囲     | リポジトリ内のすべての Copilot アクション              | エージェントモードでの自律作業（issue 対応、PR 作成）   |
| 内容の粒度   | 「日本語で答える」「ESLint/Prettier 準拠」などポリシー | `pnpm install` など具体コマンド、Git フロー、Boundaries |
| フォーマット | Markdown（構造自由）                                   | Setup / Commands / Boundaries など推奨セクション        |

#### 書き分けの例

- `.github/copilot-instructions.md` に書く: 「回答は日本語」「CLI は PowerShell 形式」「結論 → 手順の順」など普遍ルール。
- `AGENTS.md` に書く: 「依存インストールは `pnpm install`」「テストは `pnpm test`」「DB マイグレーションは触らない」など具体的フロー。

## カスタマイズのヒント

- コーディング規約やテスト方針は `.github/instructions/` にまとめておくと複数エージェントで共有しやすい。
- サンプルの英語コメントはそのままにして、日本語でインラインメモを足したい場合は ASCII で記述する。
- 追加のプロンプトが増えたら `.github/prompts/README.md` に簡単な使い分けを追記すると親切だよ。

## テンプレ更新フロー

1. まず `git status` で差分を確認。
2. ドキュメント変更のみならテストは不要。コードに影響する設定を加えた場合は関連スクリプトを案内する（例: `npm run test -- api`）。
3. `AGENTS.md` と各 README の参照が最新ファイルと一致しているか最後にもう一度チェックする。

このテンプレをベースに独自ガイドラインを組み立てて、チームの標準ワークフローに合わせてね。

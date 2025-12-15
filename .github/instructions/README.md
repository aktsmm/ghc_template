# `.github/instructions` ディレクトリ

エージェントが読み込むドメイン別ガイドラインを置く場所。

## 標準インストラクション

以下のファイルはテンプレートに含まれており、すべてのエージェントで共有される基本ルールです。

| ファイル                        | 説明                                                           |
| ------------------------------- | -------------------------------------------------------------- |
| `git.instructions.md`           | Git コミット規約（Conventional Commits、Push 禁止）            |
| `terminal.instructions.md`      | ターミナル操作規約（PowerShell 互換、破壊的操作の注意）        |
| `agent-design.instructions.md`  | エージェント設計原則（単一責任、冪等性、オーケストレーション） |
| `security.instructions.md`      | セキュリティガイドライン（機密情報、外部 API、入力検証）       |
| `communication.instructions.md` | コミュニケーションスタイル（結論ファースト、言語設定）         |
| `sample.instructions.md`        | カスタムインストラクション作成用テンプレート                   |

## カスタマイズ

- ファイル名は `<topic>.instructions.md` のようにしておくと分かりやすい。
- コーディング規約やドキュメント方針など、共有したいルールを簡潔にまとめる。
- runSubagent の利用条件や「軽量タスクはメインで対応する」といったナレッジもここに書いておけば、各エージェントから参照できる。

`sample.instructions.md` を下敷きにして、必要なトピックを追加してね。

# Microsoft Documentation Instructions

Microsoft 製品に関するコード生成・回答を行う際のドキュメント参照ガイドラインです。

---

## 1. 基本方針

Microsoft/Azure 関連の質問やコード生成を行う際は、**最新の公式ドキュメント**を参照して回答の正確性を担保してください。

### 必須手順

1. **MCP ツールの活用**: `mcp_docs_microsoft_*` または `mcp_microsoftdocs_*` ツールを使用して最新情報を取得する
2. **ソース明記**: 回答には必ず参照元 URL を含める
3. **バージョン確認**: API やサービスのバージョンに注意し、最新の推奨方法を提示する

---

## 2. 参照すべき公式リソース

### 2.1 Microsoft Learn ドキュメント

| リポジトリ                                                     | 用途                                  | 備考                |
| -------------------------------------------------------------- | ------------------------------------- | ------------------- |
| [MicrosoftDocs/learn](https://github.com/MicrosoftDocs/learn)  | Cloud & AI トレーニングコンテンツ     | 閲覧のみ（PR 不可） |
| [MicrosoftDocs Organization](https://github.com/MicrosoftDocs) | Azure・各種製品の公式ドキュメント     | PR 受付可能         |
| [MicrosoftLearning](https://github.com/MicrosoftLearning)      | コース・ラボ教材（AZ-400、AZ-700 等） | 567+ リポジトリ     |

### 2.2 主要なラボ教材リポジトリ例

- `MicrosoftLearning/mslearn-azure-ml` - Azure Machine Learning
- `MicrosoftLearning/AZ-400-DesigningandImplementingMicrosoftDevOpsSolutions` - DevOps
- `MicrosoftLearning/AZ-700-DesigningandImplementingMicrosoftAzureNetworkingSolutions` - ネットワーク
- `MicrosoftLearning/SC-401T00A-Administering-Microsoft-365-Security` - セキュリティ

---

## 3. MCP ツールの使用ガイド

### 3.1 検索ワークフロー

```
1. microsoft_docs_search  → 概要・関連ドキュメントの発見
2. microsoft_code_sample_search → コードサンプルの取得
3. microsoft_docs_fetch → 詳細情報・完全なコンテンツの取得
```

### 3.2 ツール選択基準

| シナリオ                             | 使用ツール                     |
| ------------------------------------ | ------------------------------ |
| Azure/Microsoft 製品の概要を知りたい | `microsoft_docs_search`        |
| 具体的なコード例が必要               | `microsoft_code_sample_search` |
| 詳細な手順・チュートリアルが必要     | `microsoft_docs_fetch`         |
| 特定リポジトリのコードを参照したい   | `github_repo` ツール           |

### 3.3 使用例

```markdown
# 質問: Azure Functions の Python での書き方を教えて

## エージェントの行動:

1. `microsoft_docs_search` で "Azure Functions Python" を検索
2. `microsoft_code_sample_search` で Python コードサンプルを取得
3. 必要に応じて `microsoft_docs_fetch` で詳細ページを取得
4. 回答に参照 URL を明記
```

---

## 4. GitHub リポジトリの直接参照

MCP ツールで情報が不足する場合は、`github_repo` ツールで直接リポジトリを検索してください。

### 検索例

```
repo: "MicrosoftDocs/azure-docs"
query: "app service deployment slots"
```

```
repo: "MicrosoftLearning/mslearn-azure-ml"
query: "pipeline training"
```

---

## 5. 回答フォーマット

Microsoft 製品に関する回答には、以下を含めてください：

### 必須項目

- ✅ **参照元 URL**: 公式ドキュメントへのリンク
- ✅ **API バージョン**: 使用している API のバージョン（該当する場合）
- ✅ **更新日の確認**: ドキュメントが古い場合はその旨を注記

### 推奨フォーマット

```markdown
## 回答

[回答内容]

### 参照ソース

- [ドキュメントタイトル](URL) - Microsoft Learn
- API バージョン: 2024-01-01
```

---

## 6. 注意事項

### やってはいけないこと

- ❌ 古い記憶やトレーニングデータだけに頼った回答
- ❌ バージョン非互換のコード例の提示
- ❌ 非公式ソースのみを根拠にした回答

### 優先順位

1. **MCP ツール経由の公式ドキュメント** (最優先)
2. **GitHub 上の公式リポジトリ**
3. **公開されている公式ブログ・アナウンス**

---

## 7. よく使うクエリパターン

| 目的                   | 検索クエリ例                                 |
| ---------------------- | -------------------------------------------- |
| Azure サービスの概要   | `"Azure [サービス名] overview"`              |
| クイックスタート       | `"Azure [サービス名] quickstart [言語]"`     |
| ベストプラクティス     | `"Azure [サービス名] best practices"`        |
| トラブルシューティング | `"Azure [サービス名] troubleshoot [エラー]"` |
| 料金・制限             | `"Azure [サービス名] limits pricing"`        |

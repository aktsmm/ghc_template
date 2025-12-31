# Azure Updates MCP Server セットアップガイド

Azure Updates MCP Server は、Azure サービスの最新アップデート情報を取得するための MCP サーバーです。
ローカルでビルドして使用します。

## 前提条件

- **Node.js**: v18 以上（推奨: v20 LTS）
- **npm**: v9 以上
- **Git** または **GitHub CLI**

> Node.js のインストールは [nodejs.instructions.md](../.github/instructions/dev/nodejs.instructions.md) を参照

---

## セットアップ手順

### 1. リポジトリを検索してクローン

> ⚠️ リポジトリは個人開発者によるものです。移動や非公開になる可能性があるため、まず検索して確認してください。

```powershell
# 任意のディレクトリで実行
cd D:\  # 例: Dドライブ直下

# Step 1: GitHub で検索（公開リポジトリを探す）
gh search repos "azure-updates-mcp-server" --limit 5

# Step 2: 見つかったリポジトリをクローン（例: owner/repo の形式）
gh repo clone <owner>/azure-updates-mcp-server

# または git を使用
git clone https://github.com/<owner>/azure-updates-mcp-server.git
```

**検索結果が 0 件の場合**: 別の MCP サーバーを探すか、Azure Updates RSS フィードを直接利用してください。

### 2. 依存関係のインストールとビルド

```powershell
cd azure-updates-mcp-server
npm install
npm run build
```

ビルドが成功すると `dist/index.js` が生成されます。

### 3. VS Code MCP 設定

`.vscode/mcp.json` に以下を追加：

```jsonc
{
  "servers": {
    "azure-updates": {
      "command": "C:\\Program Files\\nodejs\\node.exe", // Node.js の絶対パス
      "args": ["D:\\azure-updates-mcp-server\\dist\\index.js"], // ビルド成果物のパス
      "env": {}
    }
  }
}
```

> ⚠️ **パスは環境に合わせて変更してください**
>
> - `command`: `Get-Command node | Select-Object Source` で確認
> - `args`: クローンした場所 + `\dist\index.js`

### 4. 動作確認

1. VS Code を再起動（またはウィンドウをリロード）
2. MCP サーバーのステータスを確認（Output パネル → MCP）
3. Copilot Chat で「Azure Functions の最新アップデートを教えて」と質問

---

## トラブルシューティング

### `spawn node ENOENT` エラー

**原因**: VS Code が `node` コマンドを見つけられない

**解決策**: `command` を絶対パスに変更

```powershell
# Node.js のパスを確認
Get-Command node | Select-Object Source
# 例: C:\Program Files\nodejs\node.exe
```

### ビルドエラー

```powershell
# Node.js バージョン確認
node --version  # v18 以上が必要

# キャッシュクリアして再ビルド
Remove-Item -Recurse -Force node_modules
npm install
npm run build
```

---

## 参考リンク

- [azure-updates-mcp-server を検索 (GitHub)](https://github.com/search?q=azure-updates-mcp-server&type=repositories)
- [Azure Updates MCP 使用ガイド](../.github/instructions/integrations/microsoft-docs.instructions.md#7-azure-updates-mcp)

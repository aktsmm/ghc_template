```instructions
# Python Environment Instructions

エージェントがPythonコードを実行・開発する際のガイドラインです。

## 1. 仮想環境の必須化

Pythonプロジェクトでは、**必ず仮想環境を作成・使用**してください。
グローバル環境への直接インストールは避け、プロジェクトごとに依存関係を分離します。

### なぜ仮想環境が必要か

- **依存関係の衝突回避**: プロジェクトごとに異なるバージョンのライブラリを使用できる
- **再現性の確保**: `requirements.txt` や `pyproject.toml` で環境を再現可能
- **システム環境の保護**: グローバルPython環境を汚染しない

### 推奨: venv（標準ライブラリ）

```powershell
# 1. プロジェクトディレクトリに移動
Set-Location "d:\projects\my-project"

# 2. 仮想環境を作成
python -m venv .venv

# 3. 仮想環境を有効化 (PowerShell)
.\.venv\Scripts\Activate.ps1

# 4. パッケージをインストール
pip install -r requirements.txt
```

### 代替: conda

```powershell
# 環境を作成
conda create -n myenv python=3.12

# 環境を有効化
conda activate myenv

# パッケージをインストール
conda install numpy pandas
```

### 推奨: uv（2025年のベストプラクティス）

[uv](https://docs.astral.sh/uv/) は Rust 製の超高速 Python パッケージマネージャーです。
pip より **10〜100倍高速**で、pip / venv / pyenv / pip-tools を1つに統合します。

> 参考: [Python 環境で泣かない！Windows で uv を使った Python ベストプラクティス](https://yamapan.tokyo/?p=4064)

```powershell
# 1. uv をインストール
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"

# ターミナルを再起動、または PATH を追加
$env:Path = "C:\Users\$env:USERNAME\.local\bin;$env:Path"

# 2. Python をインストール（pyenv 不要！）
uv python install 3.12

# 3. 仮想環境を作成
Set-Location "d:\projects\my-project"
uv venv --python 3.12

# 4. パッケージをインストール
uv pip install requests pandas numpy

# または プロジェクト管理（pyproject.toml）を使う場合
uv init
uv add requests pandas numpy
```

#### uv の主なコマンド

| 従来の方法 | uv を使う方法 |
|------------|---------------|
| Python 公式インストーラー | `uv python install 3.12` |
| `python -m venv .venv` | `uv venv` |
| `pip install package` | `uv pip install package` |
| `pip freeze > requirements.txt` | `uv pip freeze` または `uv lock` |

#### VS Code との連携

```json
// .vscode/settings.json
{
  "python.defaultInterpreterPath": "${workspaceFolder}/.venv/Scripts/python.exe"
}
```

## 2. 仮想環境の確認

コマンド実行前に、正しい仮想環境がアクティブか確認してください。

```powershell
# 現在のPython実行パスを確認
python -c "import sys; print(sys.executable)"

# 期待される出力例（venvの場合）
# d:\projects\my-project\.venv\Scripts\python.exe
```

### チェック項目

- [ ] プロンプトに `(.venv)` や環境名が表示されているか
- [ ] `python -c "import sys; print(sys.executable)"` が期待するパスか
- [ ] グローバル環境を使っていないか

## 3. 依存関係の管理

### requirements.txt の作成

```powershell
# 現在の環境の依存関係を出力
pip freeze > requirements.txt
```

### pyproject.toml（推奨）

モダンなPythonプロジェクトでは `pyproject.toml` を使用します。

```toml
[project]
name = "my-project"
version = "0.1.0"
dependencies = [
    "requests>=2.28.0",
    "pydantic>=2.0.0",
]

[project.optional-dependencies]
dev = [
    "pytest>=7.0.0",
    "black>=23.0.0",
]
```

## 4. PowerShell での注意事項

### 実行ポリシー

初回は実行ポリシーの変更が必要な場合があります。

```powershell
# 現在のポリシーを確認
Get-ExecutionPolicy

# 必要に応じて変更（管理者権限が必要な場合あり）
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### パス区切り文字

- Windows: バックスラッシュ `\` またはスラッシュ `/`
- Python内: `pathlib.Path` を使用して OS 非依存にする

```python
from pathlib import Path

# OS非依存のパス操作
project_dir = Path(__file__).parent
config_file = project_dir / "config" / "settings.yaml"
```

## 5. .gitignore の設定

仮想環境はGitにコミットしないでください。

```gitignore
# Python
__pycache__/
*.py[cod]
*.egg-info/
dist/
build/

# Virtual environments
.venv/
venv/
ENV/

# IDE
.vscode/
.idea/
```

## 6. エージェントへの指示

- 新規Pythonプロジェクトを作成する際は、まず仮想環境を作成してください
- `pip install` を実行する前に、仮想環境がアクティブか確認してください
- 依存関係を追加したら `requirements.txt` または `pyproject.toml` を更新してください
- グローバル環境へのインストール（`pip install --user` 含む）は原則禁止です

```

# Sample Agent

## Role

あなたは [役割名] です。[対象] に対して [アクション] を行います。

## Goals

- [ゴール 1]
- [ゴール 2]

## Permissions

- **Allowed**: ファイルの読み込み、提案の作成
- **Denied**: `git push`、ユーザーの許可なきファイル削除

## I/O Contract

- **Input**: [入力形式の説明]
- **Output**: [出力形式の説明]
- **IR Format**: （該当する場合）構造化データの仕様

## References

- [Git Rules](../instructions/git.instructions.md)
- [Terminal Rules](../instructions/terminal.instructions.md)
- [Security Rules](../instructions/security.instructions.md)

## Workflow

1. **Plan**: ユーザーの要求を分析し、手順を提示する。
2. **Act**: 承認を得たら実行する。
3. **Verify**: 結果を確認する。

## Idempotency

- 既存ファイルの存在を確認してから操作する
- 重複処理を避けるため、状態を必ずチェックする

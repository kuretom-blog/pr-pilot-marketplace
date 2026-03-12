---
name: changelog
description: Generate a structured changelog entry from git diffs or commit history following Keep a Changelog format
---
与えられた差分またはコミット履歴から、Keep a Changelog 形式に準拠した変更履歴エントリを生成してください。

## ルール
1. 変更を以下のカテゴリに自動分類する:
   - **Added** — 新機能
   - **Changed** — 既存機能の変更
   - **Deprecated** — 将来削除予定の機能
   - **Removed** — 削除された機能
   - **Fixed** — バグ修正
   - **Security** — セキュリティに関する修正
2. 各エントリは **ユーザー視点** で簡潔に記述する（実装の詳細ではなく、何が変わったか）
3. 関連する Issue / PR 番号があれば末尾に付記する
4. 変更が多い場合はカテゴリごとに重要度順にソートする

## 出力フォーマット
```markdown
## [Unreleased] - YYYY-MM-DD

### Added
- 項目

### Changed
- 項目

### Fixed
- 項目
```

該当しないカテゴリは省略してください。

## 入力
$ARGUMENTS

引数が空または未指定の場合は、以下の順序で自動取得してください:
1. `git log --oneline -10` を実行して直近のコミット履歴を取得
2. コミット履歴が空の場合は `git diff --cached`、それも空なら `git diff` で差分を取得
3. どちらも空の場合はユーザーに差分またはコミットログを渡すよう案内する

- diff: 差分テキストまたはコミットログ
- version: バージョン番号（省略時は Unreleased）

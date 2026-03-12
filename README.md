# pr-pilot

PRワークフロー全体を支援する Claude Code プラグインです。コードレビュー、変更履歴の生成、コミットメッセージの作成、テスト不足の分析を提供します。

## インストール
```bash
/plugin marketplace add kuretom-blog/pr-pilot-marketplace
/plugin install pr-pilot@kuretom-blog
```

## スキル一覧

### `/review` — コードレビュー
差分やコードスニペットを4つの観点で分析します:
- **可読性** — 命名、構造、明瞭さ
- **パフォーマンス** — 非効率な処理、N+1クエリ、不要なアロケーション
- **セキュリティ** — インジェクション、認証の漏れ、機密情報の露出
- **保守性** — 重複コード、密結合、テスト容易性

各問題は重要度（Critical / Warning / Info）付きで、具体的な修正案とともに提示されます。

### `/changelog` — 変更履歴の生成
差分やコミット履歴から [Keep a Changelog](https://keepachangelog.com/) 形式のエントリを自動生成します。Added、Changed、Fixed、Removed、Deprecated、Security に自動分類されます。

### `/commit-msg` — コミットメッセージの作成
[Conventional Commits](https://www.conventionalcommits.org/) 準拠のコミットメッセージを作成します。type・scope の自動検出、破壊的変更の識別に対応し、最大3つの候補を提示します。

### `/test-suggest` — テスト不足の分析
変更されたコードに対して、不足しているテストケースを特定します:
- 正常系 — 主要なユースケースのカバレッジ
- 境界値 — null、空配列、最大値/最小値
- 異常系 — 例外処理、エラーレスポンス
- 回帰テスト — 今回の変更で壊れうる既存機能

プロジェクトのテストフレームワークに合わせた、すぐに使えるテストコードを出力します。

## 使い方

```bash
# ステージされた変更をレビュー（引数なしで自動取得）
/review

# 直近のコミットから変更履歴を生成
/changelog

# ステージされた差分からコミットメッセージを作成
/commit-msg

# 変更ファイルに対するテストを提案
/test-suggest

# 明示的に差分を渡すことも可能
/review $(git diff main)
/changelog $(git log --oneline v1.0..HEAD)
```

## プロジェクト構成

```
.claude-plugin/
  marketplace.json                  # マーケットプレイスのメタデータ
plugins/
  pr-pilot/
    plugin.json                     # プラグインのメタデータ
    skills/
      review/SKILL.md               # コードレビュースキル
      changelog/SKILL.md            # 変更履歴生成スキル
      commit-msg/SKILL.md           # コミットメッセージ作成スキル
      test-suggest/SKILL.md         # テスト提案スキル
```

## ライセンス

MIT License。詳細は [LICENSE](LICENSE) を参照してください。

## 作者

kuretom

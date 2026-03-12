---
name: commit-msg
description: Draft a Conventional Commits message from staged changes with scope detection and breaking change identification
---
与えられた差分（またはステージされた変更）から、Conventional Commits 仕様に準拠したコミットメッセージを生成してください。

## ルール
1. **type** を自動判定する: feat, fix, refactor, perf, docs, test, chore, ci, style, build
2. **scope** を変更対象のモジュール/ディレクトリから推測する（例: `feat(auth):`, `fix(api):`）
3. **subject** は50文字以内、命令形、英語で記述
4. 変更が大きい場合は **body** に箇条書きで詳細を追記
5. 破壊的変更がある場合は `BREAKING CHANGE:` フッターを付記
6. 候補を最大3つ提示し、ユーザーが選べるようにする

## 出力フォーマット
```
Option 1:
type(scope): subject

body (if needed)

Option 2:
...
```

## 入力
$ARGUMENTS
- diff: 差分テキスト（省略時は git diff --cached の実行を提案）

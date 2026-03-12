---
name: test-suggest
description: Suggest missing test cases for changed code including edge cases, error paths, and boundary conditions
---
与えられた差分またはコードに対して、不足しているテストケースを提案してください。

## 分析観点
1. **正常系** — 主要なユースケースのカバレッジ
2. **境界値** — 空配列、null/undefined、最大値/最小値、空文字列等
3. **異常系** — 例外、エラーレスポンス、タイムアウト、不正入力
4. **回帰テスト** — 今回の変更で壊れうる既存機能

## 出力フォーマット
各テストケースについて以下を記述:
- **テスト名**: `should ...` 形式の説明的な名前
- **カテゴリ**: 正常系 / 境界値 / 異常系 / 回帰テスト
- **優先度**: High / Medium / Low
- **テストコード**: プロジェクトのテストフレームワークに合わせたコード例

既存テストがある場合は重複を避け、不足分のみ提案してください。

## 入力
$ARGUMENTS
- diff: 差分テキストまたはコード
- framework: テストフレームワーク指定（省略可、自動検出）
- language: 言語指定（省略可、自動検出）

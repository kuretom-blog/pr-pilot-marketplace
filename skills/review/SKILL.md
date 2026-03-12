---
name: review
description: Analyze diffs or code for readability, performance, security, and maintainability issues with actionable fix suggestions
---
受け取った差分またはコードを以下の観点で分析し、それぞれ具体的な改善提案を出してください。

## 分析観点
1. **可読性** — 命名、構造、コメントの明瞭さ
2. **パフォーマンス** — 不要なアロケーション、アルゴリズムの非効率、N+1クエリ等
3. **セキュリティ** — インジェクション、認証・認可の漏れ、機密情報の露出等
4. **保守性** — 重複コード、密結合、テスト容易性の低下

## 出力フォーマット
各観点について以下の形式で出力してください:
- 重要度: Critical / Warning / Info
- 該当箇所: ファイル名と行番号（わかる場合）
- 問題: 何が問題か
- 提案: どう修正すべきか（コード例があれば含める）

問題がない観点は「問題なし」と明記してください。

## 入力
$ARGUMENTS
- diff: 差分テキストまたはコードスニペット
- language: 言語指定（省略可、自動検出）

# Skill: post-note

# note.com 投稿スキル

## 前提

- note.com には**公開 API が無い**。投稿はブラウザの編集画面への貼り付けによる（人間 or ブラウザ自動化）。
- 記事本体は Markdown で管理（例: `~/wiki/raw/<MM>/`）。

## 使い方

### 1. 記事 Markdown を用意

```
# タイトル

本文…
```

### 2. note 用にテキスト整形（任意）

- note は Markdown をそのまま貼ると改行が小さくなる → **HTML に変換して貼るのが綺麗**。
- WSL での変換:
  ```bash
  pandoc article.md -f markdown -t html -o article.html
  # または軽量に: python3 - <<'EOF'
  # import markdown; print(markdown.markdown(open('article.md').read()))
  # EOF
  ```
- 親子対話スタイル（`父「…」/ 娘「…」`）なら、各行を `<p>` にして貼れば OK。

### 3. note 編集画面へ貼り付け

1. https://note.com/new/note を開く
2. タイトルを入力
3. 本文に HTML（または Markdown）を貼り付け
4. タグ・サムネイル（カバー画像）を設定
5. 「下書きに保存」→ 確認して「公開する」

### 4. 自動化（マウスが使えない時）

- ブラウザ自動化（CDP 経由 chrome.exe 操作）で貼り付けも可能だが、note の編集画面はログイン済み前提。
- まず「下書き保存」まで自動化し、公開は手動推奨（誤爆防止）。

## トリガー

- 「note に投稿」「note 下書き」「note 記事にする」「note に書いて」

## 注意

- 一度公開した記事の URL は後から変更不可。公開前に必ずプレビュー確認。
- マーケティング文・プロモーション等は note のガイドライン準拠で。
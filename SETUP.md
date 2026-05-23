# GOODPICK セットアップガイド
## GitHub Pages で無料公開するまでの全手順

---

## ステップ1：GitHubアカウントを作る

1. https://github.com を開く
2. 「Sign up」ボタンをクリック
3. メールアドレス・パスワード・ユーザー名を設定してアカウント作成
   - ユーザー名は公開URLに使われます（例：`murata` → `murata.github.io`）
4. メール認証を完了させる

---

## ステップ2：リポジトリを作る

1. GitHubにログインした状態で右上の「+」→「New repository」をクリック
2. 以下のように設定する：
   - **Repository name**：`goodpick`（または任意の名前）
   - **Visibility**：Public（無料公開には必須）
   - **Initialize this repository with a README**：チェックする
3. 「Create repository」をクリック

---

## ステップ3：ファイルをアップロードする

1. 作成したリポジトリのページを開く
2. 「uploading an existing file」のリンクをクリック（または「Add file」→「Upload files」）
3. このフォルダ内のファイルをすべてドラッグ＆ドロップ
   - `_config.yml`
   - `Gemfile`
   - `index.html`
   - `_layouts/` フォルダ全体
   - `_includes/` フォルダ全体
   - `_posts/` フォルダ全体
   - `assets/` フォルダ全体
4. 下部の「Commit changes」をクリック

---

## ステップ4：GitHub Pagesを有効化する

1. リポジトリページの「Settings」タブをクリック
2. 左メニューの「Pages」をクリック
3. **Source** を「Deploy from a branch」に設定
4. **Branch** を「main」、フォルダを「/ (root)」に設定
5. 「Save」をクリック
6. 数分待つと、ページ上部に公開URLが表示される
   - 例：`https://あなたのユーザー名.github.io/goodpick/`

---

## ステップ5：サイトを確認する

表示されたURLをブラウザで開く。GOODPICKのトップページが表示されれば完成です。

初回ビルドには2〜5分かかることがあります。

---

## 記事の書き方（日々の運用）

### 記事ファイルの命名ルール

```
_posts/YYYY-MM-DD-記事の英語スラッグ.md
```

例：
```
_posts/2026-05-01-stanley-tumbler-review.md
```

---

### 記事テンプレート（コピーして使ってください）

```markdown
---
layout: post
title: "ブランド名「商品名」— キャッチコピー"
subtitle: "サブタイトル（記事のリード文）"
date: 2026-05-01
category: gadget   # gadget / outdoor / daily / wear / kitchen / travel
category_label: ガジェット
brand: ブランド名
tags: [タグ1, タグ2, タグ3]
rating: 4.5        # 5段階評価
editor_pick: false # true にすると Editor's Pick に表示
is_new: true
price: "¥9,800"
verdict: "総評コメント（購入ボタン近くに表示）"
ratings:
  - label: 評価項目1
    score: 4.5
  - label: 評価項目2
    score: 4.0
buy_amazon: "https://..."     # Amazonアフィリエイトリンク
buy_rakuten: "https://..."    # 楽天アフィリエイトリンク
buy_official: "https://..."   # メーカー公式
author: 村田大嘉
---

ここから記事本文を書く。

## 見出し（h2）

本文テキスト。**太字**や*斜体*が使えます。

> 引用文（体験談や印象的な一言）はこの書式で

- リスト項目1
- リスト項目2

| 仕様項目 | 内容 |
|---------|------|
| 重量 | 200g |
| 素材 | ナイロン |
```

---

### カテゴリ一覧

| category値 | 表示名 |
|-----------|-------|
| gadget | ガジェット |
| outdoor | アウトドア |
| daily | 日用品・生活雑貨 |
| wear | ウェア・アパレル |
| kitchen | キッチン |
| travel | トラベル |

---

## 画像の使い方

1. `assets/images/` フォルダに画像をアップロード
2. 記事のフロントマターに追記：
```yaml
image: /assets/images/ファイル名.jpg
```
3. 記事内での画像挿入：
```markdown
![説明テキスト](/assets/images/ファイル名.jpg)
```

推奨サイズ：横1200px以上・横長（16:9または2:1）

---

## よくある操作

### 記事を修正したい

1. GitHubの `_posts/` フォルダを開く
2. 修正したいファイルをクリック
3. 右上の鉛筆アイコン（Edit）をクリック
4. 内容を変更して「Commit changes」

### _config.yml でサイト情報を変更する

```yaml
title: GOODPICK          # サイト名
description: "..."       # サイト説明
baseurl: "/goodpick"     # リポジトリ名に合わせる
```

### 独自ドメインを設定したい（後から）

1. ドメインを取得（お名前.com、ムームードメイン等。年1,000〜1,500円程度）
2. GitHub Settings → Pages → Custom domain に入力
3. ドメインのDNS設定でGitHub PagesのIPアドレスを指定

---

## トラブルシューティング

**サイトが表示されない**
→ Settings → Pages でビルドが成功しているか確認。エラーがあれば「Actions」タブでログを確認。

**スタイルが崩れる**
→ `_config.yml` の `baseurl` がリポジトリ名と一致しているか確認。

**記事が表示されない**
→ ファイル名が `YYYY-MM-DD-slug.md` の形式になっているか確認。日付が未来だと表示されない（`_config.yml` に `future: true` を追加で解決）。

---

## GOODPICKとClaudeで記事を書く流れ

1. **あなた**：商品を使ってみて、感想をメモしておく（箇条書きでOK）
2. **あなた→Claude**：「〇〇のレビュー記事を書いて。良かった点：△△、気になった点：□□、使ったシーン：○○」と伝える
3. **Claude**：記事の下書きをMarkdown形式で作成
4. **あなた**：一人称の体験談や固有の感想を追記・修正
5. **あなた**：`_posts/` にファイルを追加してGitHubにアップロード
6. 自動でサイトに反映 ✓

このサイクルで週2〜3本は無理なく継続できます。

---

*最終更新：2026年4月*

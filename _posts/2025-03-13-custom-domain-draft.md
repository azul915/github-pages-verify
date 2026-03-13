---
layout: post
title: "GitHub Pages にサブドメインを設定した手順（お名前.com + hello-ghpages.azul915.com）"
date: 2025-03-13
---

## 概要

お名前.com で管理している `azul915.com` にサブドメイン `hello-ghpages.azul915.com` を切り、GitHub Pages のカスタムドメインとして設定した手順をまとめる。

## 前提

- ドメイン `azul915.com` を お名前.com で管理
- GitHub リポジトリ `azul915/github-pages-verify` を GitHub Pages で公開済み
- サブドメイン `hello-ghpages.azul915.com` を GitHub Pages に紐づけたい

## 手順

### 1. お名前.com で DNS レコードを追加

1. [お名前.com](https://www.onamae.com/) にログイン
2. **ドメイン一覧** から `azul915.com` を選択
3. **DNS レコード設定を利用する** をクリック
4. **レコード追加** で以下を入力

| 項目 | 値 |
|------|-----|
| ホスト名 | `hello-ghpages` |
| TYPE | `CNAME` |
| VALUE（ポイント先） | `azul915.github.io` |

> **補足**: ホスト名は `hello-ghpages` のみ。`.azul915.com` は不要（自動で付与される）。

5. **追加** をクリックして保存

### 2. GitHub Pages にカスタムドメインを設定

1. リポジトリ `github-pages-verify` の **Settings** → **Pages** を開く
2. **Custom domain** の入力欄に `hello-ghpages.azul915.com` を入力
3. **Save** をクリック
4. DNS の反映を待つ（数分〜最大48時間。お名前.com は比較的早いことが多い）
5. **Enforce HTTPS** にチェックが入るのを待つ（DNS 反映後、自動で有効になる場合あり。出ない場合は手動でチェック）

### 3. Jekyll の _config.yml を変更

カスタムドメインではサイトがルート（`https://hello-ghpages.azul915.com/`）に配信されるため、`baseurl` を空にする。

```yaml
baseurl: ""
url: "https://hello-ghpages.azul915.com"
```

変更後、push する。

```bash
git add _config.yml
git commit -m "Configure for custom domain hello-ghpages.azul915.com"
git push
```

### 4. 動作確認

`https://hello-ghpages.azul915.com` にアクセスし、ブログが表示されれば完了。

## 詰まった点

（設定時に気づいた点があれば追記）

## Enforce HTTPS の反映時間

- 設定時刻: （記録）
- 有効化まで: （記録）

## 参考

- [GitHub Pages のカスタムドメイン](https://docs.github.com/ja/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [お名前.com DNS レコード設定](https://www.onamae.com/guide/step/domain/3/2/)

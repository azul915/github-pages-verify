---
layout: post
title: "調査した制限と実際に使ってみた感想（初回セットアップ）"
date: 2025-03-13
---

## はじめに

静的サイトホスティングの調査を踏まえ、実際に GitHub Pages でブログを構築してみる。この記事は初回セットアップの記録と、調査内容との照合である。

## やったこと

- Jekyll でブログの雛形を作成
- GitHub リポジトリに push
- GitHub Pages を有効化

## つまずき: HTML が 404 になる

デプロイ直後、トップページは表示されるが CSS が読み込まれず、記事リンクをクリックすると 404 になる現象が発生した。

**原因**: プロジェクトサイト（`username.github.io/リポジトリ名/`）では、Jekyll の `_config.yml` に `baseurl` の設定が必須。未設定だと `/assets/css/style.css` などが `https://username.github.io/assets/...` を参照してしまい、正しいパス `https://username.github.io/リポジトリ名/assets/...` に届かない。

**対処**: `_config.yml` に以下を追加。

```yaml
baseurl: "/github-pages-verify"  # リポジトリ名
url: "https://azul915.github.io"
```

push 後、数分で解消した。

## 調査との照合（随時追記）

| 調査内容 | 実際の挙動 | 備考 |
|----------|------------|------|
| Jekyll はネイティブ対応 | （検証中） | |
| ビルド 10 回/時 | （検証中） | |
| デプロイ 10 分タイムアウト | （検証中） | |

## 次にやること

- カスタムドメイン（apex / www）の設定
- Enforce HTTPS の有効化と反映時間の計測
- 1 ドメイン制限の確認

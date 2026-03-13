---
layout: default
title: ホーム
---

# GitHub Pages 検証ブログ

**調査→実践**: 静的サイトホスティングの調査内容を、実際に GitHub Pages で構築して検証するブログです。

- [公開サイト](https://azul915.github.io/github-pages-verify/) / [リポジトリ](https://github.com/azul915/github-pages-verify)

## 検証項目

- [ ] 調査内容と実運用の差
- [ ] カスタムドメイン（apex / www）の設定手順とつまずき
- [ ] Enforce HTTPS の反映時間や挙動
- [ ] 1ドメイン制限の実感

## 記事一覧

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <span>{{ post.date | date: "%Y-%m-%d" }}</span>
    </li>
  {% endfor %}
</ul>

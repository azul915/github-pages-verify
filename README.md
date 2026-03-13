# GitHub Pages 検証ブログ

**調査→実践**: 静的サイトホスティングの調査内容を、実際に GitHub Pages で構築して検証するブログです。

- **公開サイト**: https://azul915.github.io/github-pages-verify/
- **リポジトリ**: https://github.com/azul915/github-pages-verify

## 検証項目

- [ ] 調査内容と実運用の差
- [ ] カスタムドメイン（apex / www）の設定手順とつまずき
- [ ] Enforce HTTPS の反映時間や挙動
- [ ] 1 ドメイン制限の実感

## セットアップ

### 1. GitHub にリポジトリを作成

```bash
cd github-pages-verify
git init
git add .
git commit -m "Initial commit: Jekyll blog for GitHub Pages verification"
git branch -M main
git remote add origin https://github.com/<USERNAME>/<REPO>.git
git push -u origin main
```

### 2. GitHub Pages を有効化

1. リポジトリの **Settings** → **Pages**
2. **Source**: Deploy from a branch
3. **Branch**: `main` / `/ (root)`
4. Save

数分後、`https://<USERNAME>.github.io/<REPO>/` で公開される（ユーザーサイトの場合は `https://<USERNAME>.github.io/`）

### 3. カスタムドメイン（任意）

**apex ドメイン（example.com）の場合**

1. リポジトリの **Settings** → **Pages** → **Custom domain** にドメインを入力
2. DNS に A レコードを追加（GitHub の IP）:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
3. **Enforce HTTPS** にチェック（反映に数分〜数時間かかる場合あり）

**www サブドメイン（www.example.com）の場合**

1. **Custom domain** に `www.example.com` を入力
2. DNS に CNAME レコード: `www` → `<USERNAME>.github.io`

### 4. ローカルでプレビュー（任意）

```bash
bundle install
bundle exec jekyll serve
```

`http://localhost:4000` で確認できる。

## 記事の追加

`_posts/` に `YYYY-MM-DD-title.md` 形式で Markdown を追加する。

## 参考

- [GitHub Pages ドキュメント](https://docs.github.com/ja/pages)
- [Jekyll ドキュメント](https://jekyllrb.com/docs/)

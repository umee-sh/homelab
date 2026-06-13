# git-pages

Forgejo 向け静的サイトホスティングサーバー。

## URL 構造

`pages` org 配下のリポジトリが `pages.umee.sh/<reponame>` で公開される。

```
pages.umee.sh/mysite
 → Forgejo: code.umee.sh/pages/mysite (pages ブランチ)
```

個人ユーザーのインデックスページは `<user>.umee.sh/` でも引き続き利用可能。

## Cloudflare Tunnel 設定

Cloudflare Zero Trust ダッシュボードで以下のルートを追加してください：

- **Public hostname**: `pages.umee.sh`
- **Service**: `http://git-pages.app-git-pages.svc.cluster.local:3000`

`pages.umee.sh` は `*.umee.sh` の Cloudflare Universal SSL でカバーされます。

## Forgejo 設定

1. `code.umee.sh` に `pages` という Organization を作成する
2. 各サイトは `pages` org 配下にリポジトリを作成し、`pages` ブランチにコンテンツを配置する

## ノード上のディレクトリ作成

デプロイ前に PV が使用するディレクトリを作成してください：

```bash
sudo mkdir -p /mnt/local-storage/git-pages
```

## Forgejo Action の設定例

リポジトリのビルド成果物を git-pages に公開する場合、以下の Forgejo Action を使用します。

```yaml
# .forgejo/workflows/pages.yml
name: pages
on:
  push:
    branches:
      - main

jobs:
  publish:
    runs-on: docker
    steps:
      - uses: actions/checkout@v4
      # ビルドステップ（例: npm run build で _site/ を生成）
      - name: publish
        uses: docker://data.forgejo.org/git-pages/git-pages-cli:1.9.0
        with:
          site: pages.umee.sh/${{ gitea.event.repository.name }}
          source: _site/
          server: https://pages.umee.sh
          token: ${{ secrets.GIT_PAGES_TOKEN }}
```

`GIT_PAGES_TOKEN` には Forgejo のアクセストークンを設定します（Settings → Applications → Access tokens）。

必要な権限:
- User: Read
- Repository: Read and Write

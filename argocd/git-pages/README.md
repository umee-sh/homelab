# git-pages

Forgejo 向け静的サイトホスティングサーバー。

## Cloudflare Tunnel 設定

Cloudflare Zero Trust ダッシュボードで以下のルートを追加してください：

- **Public hostname**: `*.pages.umee.sh`
- **Service**: `http://git-pages.app-git-pages.svc.cluster.local:3000`

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
          site: <user>.pages.umee.sh
          source: _site/
          server: https://pages.umee.sh
          token: ${{ secrets.GIT_PAGES_TOKEN }}
```

`GIT_PAGES_TOKEN` には Forgejo のアクセストークンを設定します（Settings → Applications → Access tokens）。

必要な権限:
- User: Read
- Repository: Read and Write

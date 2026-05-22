# Hermes Agent

```bash
docker run -it --rm -v ./data:/opt/data \
  nousresearch/hermes-agent:sha-a91a57fa5a13d516c38b07a141a9ce8a3daabeb0 \
  setup
```

Secret の情報を得る。

```bash
# コメントや空行を除く
grep -v '^\s*#\|^$' data/.env
```

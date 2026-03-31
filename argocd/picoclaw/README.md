# PicoClaw

## Secret の作成

`.security.yml` を作成し、Secret として登録してください。

### .security.yml の例

```yaml
model_list:
  gpt-4o:
    api_keys:
      - "sk-xxxxxxxxxxxxxxxxxxxxxxxx"

channels:
  telegram:
    token: "123456789:AAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

web: {}

skills: {}
```

使わないセクションは `{}` のまま残してください。

### Secret の登録

```bash
kubectl create secret generic picoclaw-secret \
    --namespace app-picoclaw \
    --from-file=.security.yml=/path/to/.security.yml
```

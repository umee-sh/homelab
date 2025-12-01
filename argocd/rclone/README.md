# rclone

次を参考に、Dropbox の認証情報を得る。
https://rclone.org/remote_setup/

```bash
rclone authorize dropbox
```

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: rclone-dropbox
  namespace: default
type: Opaque
stringData:
  remote: "dropbox"
  remotePath: "umeesh-homelab"
  configData: |
    [dropbox]
    type = dropbox
    token = {"access_token":"sl.B1234567890abcdef...","token_type":"bearer","expiry":"2024-01-01T00:00:00Z"}
```

```bash
kubectl apply -f secret.yaml
```

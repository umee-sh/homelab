# arc

```bash
kubectl create secret generic arc-github \
  --namespace=my_namespace \
  --from-literal=github_app_id=123456 \
  --from-literal=github_app_installation_id=654321 \
  --from-literal=github_app_private_key="$TOKEN"
```

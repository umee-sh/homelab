# SearXNG

```bash
kubectl create secret generic searxng-secret \
  --namespace=app-searxng \
  --from-literal=secret-key="$SECRET"
```

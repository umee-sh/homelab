# hollo

```bash
kubectl create secret generic sakura-obj-credentials \
  -n app-hollo \
  --from-literal=ACCESS_KEY_ID=CHANGE_HERE \
  --from-literal=SECRET_ACCESS_KEY=CHANGE_HERE
```

```bash
kubectl create secret generic hollo-secret \
  --namespace=app-hollo \
  --from-literal=DATABASE_URL="postgres://hollo:CHANGE_HERE@hollo-pg-rw.app-hollo.svc.cluster.local:5432/hollo" \
  --from-literal=SECRET_KEY="$(openssl rand -hex 32)"
```

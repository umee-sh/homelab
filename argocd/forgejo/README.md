# Forgejo

```bash
kubectl create secret generic forgejo-admin-secret \
    --namespace app-forgejo \
    --from-literal=username=admin \
    --from-literal=password=password
```

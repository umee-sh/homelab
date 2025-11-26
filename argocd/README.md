# argocd

```bash
sudo microk8s kubectl create secret generic cloudflare-tunnel \
  --from-literal=token="$TOKEN"

sudo microk8s kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

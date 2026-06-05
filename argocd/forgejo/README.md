# Forgejo

```bash
kubectl create secret generic forgejo-admin-secret \
    --namespace app-forgejo \
    --from-literal=username=admin \
    --from-literal=password=password
```

## Cloudflare Turnstile

```bash
kubectl create secret generic forgejo-turnstile-secret \
    --namespace app-forgejo \
    --from-literal=sitekey=<TURNSTILE_SITEKEY> \
    --from-literal=secret=<TURNSTILE_SECRET>
```

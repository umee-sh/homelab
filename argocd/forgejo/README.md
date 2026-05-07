# Forgejo

```bash
kubectl create secret generic forgejo-admin-secret \
    --namespace app-forgejo \
    --from-literal=username=admin \
    --from-literal=password=password

kubectl apply -f - <<EOF
apiVersion: v1
kind: Secret
metadata:
  name: forgejo-config-secret
  namespace: app-forgejo
type: Opaque
stringData:
  database: |
    HOST: forgejo-pg-rw.app-forgejo.svc.cluster.local
    NAME: forgejo
    USER: user
    PASSWORD: password
EOF
```

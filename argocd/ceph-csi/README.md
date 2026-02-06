# ceph-csi

```bash
kubectl create secret generic csi-rbd-secret \
  --namespace=ceph-csi \
  --from-literal=userID="kubernetes" \
  --from-literal=userKey="$userKey"
```

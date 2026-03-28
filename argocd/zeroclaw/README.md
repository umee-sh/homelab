# ZeroClaw

```bash
# https://start.1password.com/open/i?a=GXIGW4EGSNAZFGQKHWG5XISQIY&v=4adb6fwinshbphz7rkitd6mn7e&i=sa4up5iulqxejrglhl2i3vaxhq&h=my.1password.com
kubectl create secret generic zeroclaw-secret \
    --namespace app-zeroclaw \
    --from-literal=OPENAI_API_KEY=<your-key>
```

# Hermes Agent

## Secret の登録

```bash
cat <<EOF | sudo microk8s kubectl apply -f -
apiVersion: v1
kind: Secret
metadata:
  name: hermes-agent-secret
  namespace: app-hermes-agent
type: Opaque
stringData:
  .env: |
    TERMINAL_MODAL_IMAGE=nikolaik/python-nodejs:python3.11-nodejs20
    TERMINAL_TIMEOUT=60
    TERMINAL_LIFETIME_SECONDS=300
    BROWSERBASE_PROXIES=true
    BROWSERBASE_ADVANCED_STEALTH=false
    BROWSER_SESSION_TIMEOUT=300
    BROWSER_INACTIVITY_TIMEOUT=120
    WEB_TOOLS_DEBUG=false
    VISION_TOOLS_DEBUG=false
    MOA_TOOLS_DEBUG=false
    IMAGE_TOOLS_DEBUG=false
    ANTHROPIC_API_KEY=
    ANTHROPIC_TOKEN=
    DISCORD_BOT_TOKEN=
    DISCORD_ALLOWED_USERS=
    DISCORD_HOME_CHANNEL=
EOF
```

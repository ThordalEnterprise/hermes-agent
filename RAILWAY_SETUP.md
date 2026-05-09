# Railway Setup

This fork is configured to run Hermes Agent as a Telegram-first personal agent on Railway.

## Service

- Source: `ThordalEnterprise/hermes-agent`
- Branch: `main`
- Builder: Dockerfile
- Start command: `gateway run`
- Volume mount: `/opt/data`
- Public dashboard: disabled

## Required Railway Variables

Set these in Railway service variables. Do not commit real values to Git.

```env
PORT=8443
OPENROUTER_API_KEY=<your-openrouter-key>
TELEGRAM_BOT_TOKEN=<your-botfather-token>
TELEGRAM_ALLOWED_USERS=<your-numeric-telegram-user-id>
TELEGRAM_WEBHOOK_URL=https://<railway-domain>/telegram
TELEGRAM_WEBHOOK_PORT=8443
TELEGRAM_WEBHOOK_SECRET=<random-secure-token>
GATEWAY_ALLOW_ALL_USERS=false
```

## First Deploy Checklist

1. Connect the Railway service to this GitHub repo and enable autodeploy from `main`.
2. Add a Railway volume mounted at `/opt/data`.
3. Generate a Railway public domain.
4. Set the variables above, replacing placeholders with real secrets.
5. Deploy and confirm logs show the Telegram webhook listening on `0.0.0.0:8443/telegram`.
6. Message the bot from the allowlisted Telegram account and run `/status` and `/model`.

# openclaw-jentic-skill

OpenClaw skill for [Jentic](https://jentic.com) — AI agent API middleware.

This skill lets OpenClaw agents discover and execute real-world APIs (Gmail, GitHub, Stripe, Twilio, Google Calendar, NYT, Finnhub, and many more) through a single uniform interface, **without storing any API credentials in the agent**.

## Install

```bash
clawhub install jentic
```

Or manually:

```bash
curl -s https://raw.githubusercontent.com/seanblanchfield/openclaw-jentic-skill/main/scripts/jentic.py \
  -o ~/.openclaw/workspace/scripts/jentic.py
chmod +x ~/.openclaw/workspace/scripts/jentic.py
```

## Setup

1. Create a Jentic account at [app.jentic.com](https://app.jentic.com)
2. Create an agent and copy your API key (`ak_...`)
3. Store it in OpenClaw:
   ```json
   { "skills": { "entries": { "jentic": { "apiKey": "ak_your_key_here" } } } }
   ```
4. Add credentials for each API you want to call at app.jentic.com → Credentials

## Usage

```bash
uv run scripts/jentic.py apis                                    # list scoped APIs
uv run scripts/jentic.py search "send an email"                  # find by intent
uv run scripts/jentic.py load op_7ae5ecc5d29bed24               # inspect schema
uv run scripts/jentic.py execute op_7ae5ecc5d29bed24 \
  --inputs '{"category":"general"}'                              # run it
uv run scripts/jentic.py pub-search "home automation"            # browse full catalog (no auth)
```

## Why Jentic?

Credentials stored in an agent are a prompt injection target. Jentic removes that attack surface: your API secrets (OAuth tokens, API keys) are stored in Jentic and injected server-side. The agent only ever holds a scoped agent key.

## Links

- [Jentic](https://jentic.com)
- [Jentic Docs](https://docs.jentic.com)
- [Jentic SDK](https://github.com/jentic/jentic-sdks)
- [OpenClaw](https://openclaw.ai)
- [ClawHub](https://clawhub.ai)

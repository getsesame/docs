# Source: https://github.com/getsesame/sesame/blob/main/README.md

[getsesame](https://github.com/getsesame) / **[sesame](https://github.com/getsesame/sesame)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fsesame) You must be signed in to change notification settings
- [Fork 0](https://github.com/login?return_to=%2Fgetsesame%2Fsesame)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fsesame)
 

 

## FilesExpand file tree

 main

/

# README.md

Copy path

Blame

More file actions

Blame

More file actions

## Latest commit

## History

[History](https://github.com/getsesame/sesame/commits/main/README.md)

History

140 lines (106 loc) · 7.79 KB

## FilesExpand file tree

 main

/

# README.md

Copy path

Top

## File metadata and controls

- Preview
 
- Code
 
- Blame
 

140 lines (106 loc) · 7.79 KB

[Raw](https://github.com/getsesame/sesame/raw/refs/heads/main/README.md)

Copy raw file

Download raw file

Outline

Edit and raw actions

# Sesame

**Your AI agents need secrets. They don't need to see them.**

[![Website](https://camo.githubusercontent.com/800bf61f65670da5e118cd4a4cc23ea0cb5893c665e451e0c2f76d7ee17167c2/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f776562736974652d676574736573616d652e6465762d3235363365623f7374796c653d666c61742d737175617265)](https://getsesame.dev) [![Install](https://camo.githubusercontent.com/9df7644a65bfbe5f7fa92d873e74d98d17897f2bb8297931690892212c300d5f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f696e7374616c6c2d6375726c25323025374325323073682d3232633535653f7374796c653d666c61742d737175617265)](https://getsesame.dev) [![Contact](https://camo.githubusercontent.com/6fa5bee1db7e38ecc5084f5870b5cba7d036859734608e8a5921ec0556f708f0/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f636f6e746163742d6869253430676574736573616d652e6465762d3634373438623f7374796c653d666c61742d737175617265)](mailto:hi@getsesame.dev)

Sesame is a user-controlled broker that proxies authenticated HTTP API calls. 
Your agent calls `sesame request` instead of `curl` — and the broker attaches the right `Authorization` header server-side, based on the target hostname. 
**Credentials never enter the agent's prompt, never appear in logs, never touch agent memory.**

 [![Sesame approval flow — 30-second demo](https://github.com/getsesame/sesame/raw/main/docs/demo.gif)](https://github.com/getsesame/sesame/raw/main/docs/demo.mp4)[![Sesame approval flow — 30-second demo](https://github.com/getsesame/sesame/raw/main/docs/demo.gif)](https://github.com/getsesame/sesame/raw/main/docs/demo.mp4)

---

## Why

Modern AI agents need API keys for everything: GitHub, Stripe, OpenAI, Anthropic, your internal services. Today they get those keys via:

- **Environment variables** — leak via logs, prompt injection, or a careless `printenv`.
- **Tool arguments** — same leak surface, one layer deeper.
- **MCP servers with credentials baked in** — the agent can read its own config.

Sesame moves the credential out of the agent's reach entirely. The agent passes a _reference_ (the target hostname); the broker — running where you control it — resolves the credential and signs the outbound request. The agent sees only the response body.

## Quickstart

```shell
# Install the CLI (macOS arm64/x86_64, Linux x86_64)
curl -fsSL https://getsesame.dev/install.sh | sh

# Register this device — generates an Ed25519 keypair, opens the
# broker's claim URL in your browser for one-click approval
sesame login

# Make an authenticated request — no API key in sight
sesame request POST https://api.anthropic.com/v1/messages \
  -H "Content-Type: application/json" \
  -H "anthropic-version: 2023-06-01" \
  -d '{"model": "claude-sonnet-4-5", "max_tokens": 1024,
       "messages": [{"role": "user", "content": "Hi"}]}'
```

### For AI agents

Drop in the official skill so your agent (Claude Code, Codex, Cursor, OpenClaw, +40 more) reaches for `sesame request` instead of raw `curl` / `fetch` / `requests`:

```shell
npx skills add getsesame/skills
```

Walks you through agent selection interactively. Add `--global` to install to the user-level agent directory, or `--all` to install to every agent the CLI detects.

## Commands

| Command | What it does |
| --- | --- |
| `sesame login` | Register this device with the broker. Generates an Ed25519 keypair, opens a one-click claim URL. |
| `sesame login --new` | Register an additional agent on the same device. |
| `sesame refresh` | Refresh expired tokens via challenge-response with the device key. |
| `sesame status` | Show device fingerprint, registered agents, token state. |
| `sesame switch <agent-id>` | Switch the active agent for this shell. |
| `sesame hostnames` | List hostnames the broker has secrets configured for. |
| `sesame request <METHOD> <URL>` | Proxy an authenticated HTTP request. Supports `-H`, `-d`, `--raw`. |
| `sesame --version` | Print the CLI version. |

## How it works

```
   Agent device                Sesame Broker                  Upstream API
                                                              (Anthropic,
   [On login / refresh]                                        Stripe, …)
     │  ┌── challenge: nonce ───┤
     │◄─────────────────────────┤
     │                          │
     │  ── sign nonce with ────►│
     │     device Ed25519 priv  │  ┌── verify signature
     │                          │  │   with stored device pub key
     │                          │  └── issue access JWT (EdDSA)
     │◄─────────────────────────┤
     │      (JWT)               │
                                                                 │
   [On every authenticated request]                              │
     │  sesame request POST … + JWT                              │
     ├─────────────────────────►│  ┌── 1. verify JWT sig (EdDSA) │
     │                          │  ├── 2. check agent is active  │
     │                          │  ├── 3. look up policy         │
     │                          │  ├── 4. Telegram-approve       │
     │                          │  │      (first time per host)  │
     │                          │  └── 5. inject Auth header     │
     │                          │                                │
     │                          ├───────────────────────────────►│
     │                          │       (with credential)        │
     │                          │                                │
     │                          │◄───────────────────────────────┤
     │                          │       (response body)          │
     │◄─────────────────────────┤                                │
     │       (response body,                                     │
     │        no credential)                                     │
```

The broker is your trust boundary. It enforces:

- **Cryptographic identity (Ed25519, end-to-end)**: on first `sesame login`, the device generates an Ed25519 keypair locally — the **private key never leaves the device**. Identity is proved via challenge-response (the device signs a broker nonce; the broker verifies with the stored public key) and only then is a short-lived JWT issued, also Ed25519-signed by the broker's own key. Every subsequent request is gated on that JWT signature. Replays, forged tokens, and in-transit tampering all fail verification.
- **Per-hostname policy**: which methods (`GET`, `POST`, …) and path patterns are allowed for each agent.
- **Just-in-time approval**: first request to a new hostname blocks until you tap _Approve_ in the dashboard or Telegram bot. Subsequent requests within the approved window are instant.
- **Instant revocation**: deactivating an agent invalidates all its grants in one click. Replays return `403`, and any further authentication attempt with that agent's keypair surfaces as a security alert in the dashboard.
- **Audit log**: every proxied request, every approval, every revocation, with the credential value redacted everywhere.

## Install options

```shell
# Specific version
curl -fsSL https://getsesame.dev/install.sh | sh -s -- --version v0.3.22

# Custom prefix (default: /usr/local/bin, falls back to ~/.local/bin)
curl -fsSL https://getsesame.dev/install.sh | sh -s -- --prefix ~/.local/bin

# Uninstall
curl -fsSL https://getsesame.dev/install.sh | sh -s -- --uninstall
```

The installer also runs `npx skills add getsesame/skills --yes --global --all` if Node is available, so your AI agents pick up the skill automatically.

## Status

**Pre-1.0.** The end-to-end flow works (broker, CLI, mobile approval, dashboard), and the hosted broker at `getsesame.dev` is live. Treat it as alpha — APIs may change, and we don't yet recommend pushing production secrets through the SaaS until self-host lands.

## Links

- 🌐 [**getsesame.dev**](https://getsesame.dev) — landing page, signup, dashboard
- ✉️ [hi@getsesame.dev](mailto:hi@getsesame.dev) — questions, feedback, security reports
- 🧠 [`getsesame/skills`](https://github.com/getsesame/skills) — the agent skill that wires AI tools into Sesame
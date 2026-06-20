# Source: https://getsesame.dev/

# Secrets stay secret. Even from your AI agent.

Brokered. Audited. Revocable in one click.

Stop injecting secrets into agents. Sesame brokers every call — credentials injected server-side, every grant approved by you, every agent access killable on demand.

Sign In[See how it works](https://getsesame.dev/#zero-trust)

sesame · demo

## The prompt-injection reality check

Every AI agent you run needs API keys, but traditional methods are dangerous

security

### Prompt Leaks

System instructions are easily bypassed. If you pass an API key in the context, a clever agent can extract it

description

### Insecure .env Files

Hardcoding secrets in agent environments is a compliance nightmare. They stay resident in memory and disk logs

monitoring

### Blind Execution

Once an agent has a key, you have no visibility into how it's used until the billing alert hits your inbox

## The Zero-Trust Broker

Sesame creates a secure perimeter where secrets are injected at the edge, never reaching the agent's logic.

Secret Perimeter

terminal

#### The Agent

Requesting Tool Execution

No Secrets

No secrets in transit

person\_check

#### Approver

Human approval

encrypted

#### Sesame Broker

Identity & Policy Node

keySECRET INJECTED

![Anthropic](https://cdn.simpleicons.org/anthropic)

![Stripe](https://cdn.simpleicons.org/stripe)

![GitHub](https://cdn.simpleicons.org/github)

terminal

#### The Agent

Requesting Tool Execution

No Secrets

No secrets in transit

person\_check

#### Approver

Human approval

encrypted

#### Sesame Broker

Identity & Policy Node

keySECRET INJECTED

![Anthropic](https://cdn.simpleicons.org/anthropic)

![Stripe](https://cdn.simpleicons.org/stripe)

![GitHub](https://cdn.simpleicons.org/github)

Secret Perimeter

## Time Authorization

Grant ephemeral access to critical infrastructure. Just-in-time credentials that expire automatically, reducing your attack surface to the absolute minimum.

timer

#### Auto-Expiring Keys

Credentials are valid for minutes, not months

verified\_user

#### JIT Provisioning

Inject secrets only when a specific tool is invoked

ACTIVE NOW

### Stripe API Key

api.stripe.com

Expires in 3h 59m · Granted 13s ago

Methods:

GETPOST

![MCP](https://cdn.simpleicons.org/modelcontextprotocol)

### Integrate Internal & External MCP Servers

Connect any MCP server alongside your API keys. Your agent gets the tools, never the tokens.

![Linear](https://cdn.simpleicons.org/linear)Linear![Atlassian](https://www.google.com/s2/favicons?domain=atlassian.com&sz=64)Atlassian![Sentry](https://www.google.com/s2/favicons?domain=sentry.io&sz=64)Sentry![MCP](https://cdn.simpleicons.org/modelcontextprotocol)Your own

sesame · mcp relayconnected

Agentdarwin / claude-codeServermcp.linear.app

tools/list✓ 24 tools · auto

tools/call create\_issue⏸ approval required

approved by you · telegram2.1s

→ LIN-142 created✓ relayed

Self-hosted for enterprise

![AWS](https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg)

## Deploy Sesame inside your cloud in 5 minutes.

Deploy the broker inside your VPC, connect it to your own Secrets Manager, and keep every AI agent request behind your security boundary.

dns

### Private network deployment

Run the proxy next to production workloads in AWS, Kubernetes, or your own infrastructure.

rocket\_launch

### Set it up in 5 minutes

One CLI command provisions the broker inside your own AWS account — VPC, Secrets Manager, and database included.

## Enterprise-grade by design

Infrastructure that meets the security standards of the world's most regulated industries.

### Policy + Human Approval

Scoped policies auto-approve what's safe. Anything outside them routes to you for approval — via the app or Telegram — approve once, and the agent can keep running until your window expires. No approval fatigue.

check\_circleAllowed Paths

api.stripe.com/\*\*

GETPOST

blockDenied Paths

No deny rules configured

notifications\_activeApproval requestFirst-time request

smart\_toy

MyClaudeAgent

darwin · Kushagras-MacBookPro

wants access to

![Stripe](https://cdn.simpleicons.org/stripe/white)

Stripe API Key

api.stripe.com

Grant for

4h8h24h

Policy

FullRead-onlyDefault

shield\_lockRead-only

GETHEAD

DenycheckApprove

You'll only be asked again when this approval expires. 
The agent's request waits on the broker until you decide.

### Instant Revocation

power\_settings\_new

#### Revoke an agent

Sesame ends its sessions, voids its refresh tokens, rejects its next request. Every previously-granted approval becomes inert because no agent identity can use them.

content\_cut

#### Revoke a single approval

Surgically remove one (agent, secret) grant without touching the agent itself. Useful when a window was too generous for just one credential.

door\_open

#### For Bring Your Own Vault secrets — cut the door

Delete the IAM role in your own AWS. Sesame loses its ability to assume.

shieldAgents · Sesame dashboardLive

smart\_toy

MyClaudeAgent

darwin · 3 active approvals

ActiveRevoke

smart\_toy

legacy-bot

linux · revoked 1 min ago

RevokedActivate

check4 pending approvals cancelled

check2 refresh tokens voided

checkNext request rejected with 403

smart\_toy

test-agent

macOS · 2 active approvals

ActiveRevoke

Every revocation is timestamped in the audit log below.

analytics

### Real-time Monitoring & Audit

Complete visibility into every request your AI agents make. Immutable logs captured at the proxy level for security and compliance.

| Time | Event | Hostname | Details |
| --- | --- | --- | --- |
| 4/16/2026, 1:55 AM | Proxy Request | api.stripe.com | POST https://api.stripe.com/v1/payment\_intents |
| 4/16/2026, 1:55 AM | Authorization Granted | api.stripe.com | Stripe API Key |
| 4/16/2026, 1:54 AM | Registration | — | MyOpenclawAgent |

Proxy Request4/16/2026, 1:55 AM

Hostapi.stripe.comDetailPOST https://api.stripe.com/v1/payment\_intents

Authorization Granted4/16/2026, 1:55 AM

Hostapi.stripe.comDetailStripe API Key

Registration4/16/2026, 1:54 AM

Host—DetailMyOpenclawAgent

### 70+ Providers Built In. Bring Your Own.

Pre-built integrations for Anthropic, OpenAI, Stripe, GitHub, and more. Add any custom API with a single command.

Any hostname. Any auth method. Any MCP server.

![Anthropic](https://www.google.com/s2/favicons?domain=anthropic.com&sz=64)

![OpenAI](https://www.google.com/s2/favicons?domain=openai.com&sz=64)

![Stripe](https://www.google.com/s2/favicons?domain=stripe.com&sz=64)

![GitHub](https://www.google.com/s2/favicons?domain=github.com&sz=64)

![Slack](https://www.google.com/s2/favicons?domain=slack.com&sz=64)

![Twilio](https://www.google.com/s2/favicons?domain=twilio.com&sz=64)

![Mistral](https://www.google.com/s2/favicons?domain=mistral.ai&sz=64)

![Vercel](https://www.google.com/s2/favicons?domain=vercel.com&sz=64)

![Cloudflare](https://www.google.com/s2/favicons?domain=cloudflare.com&sz=64)

![Coinbase](https://www.google.com/s2/favicons?domain=coinbase.com&sz=64)

![Discord](https://www.google.com/s2/favicons?domain=discord.com&sz=64)

![Sentry](https://www.google.com/s2/favicons?domain=sentry.io&sz=64)

![Datadog](https://www.google.com/s2/favicons?domain=datadoghq.com&sz=64)

![PagerDuty](https://www.google.com/s2/favicons?domain=pagerduty.com&sz=64)

![SendGrid](https://www.google.com/s2/favicons?domain=sendgrid.com&sz=64)

![PayPal](https://www.google.com/s2/favicons?domain=paypal.com&sz=64)

![Netlify](https://www.google.com/s2/favicons?domain=netlify.com&sz=64)

![Railway](https://www.google.com/s2/favicons?domain=railway.app&sz=64)

![Fly.io](https://www.google.com/s2/favicons?domain=fly.io&sz=64)

![Render](https://www.google.com/s2/favicons?domain=render.com&sz=64)

![DigitalOcean](https://www.google.com/s2/favicons?domain=digitalocean.com&sz=64)

![GitLab](https://www.google.com/s2/favicons?domain=gitlab.com&sz=64)

![Groq](https://www.google.com/s2/favicons?domain=groq.com&sz=64)

![Cohere](https://www.google.com/s2/favicons?domain=cohere.com&sz=64)

![Perplexity](https://www.google.com/s2/favicons?domain=perplexity.ai&sz=64)

![Deepseek](https://www.google.com/s2/favicons?domain=deepseek.com&sz=64)

![Resend](https://www.google.com/s2/favicons?domain=resend.com&sz=64)

![Postmark](https://www.google.com/s2/favicons?domain=postmarkapp.com&sz=64)

![Plaid](https://www.google.com/s2/favicons?domain=plaid.com&sz=64)

![Clerk](https://www.google.com/s2/favicons?domain=clerk.com&sz=64)

![Mercury](https://www.google.com/s2/favicons?domain=mercury.com&sz=64)

![Ramp](https://www.google.com/s2/favicons?domain=ramp.com&sz=64)

![Wise](https://www.google.com/s2/favicons?domain=wise.com&sz=64)

![Notion](https://www.google.com/s2/favicons?domain=notion.so&sz=64)

![Linear](https://www.google.com/s2/favicons?domain=linear.app&sz=64)

![Airtable](https://www.google.com/s2/favicons?domain=airtable.com&sz=64)

![Spotify](https://www.google.com/s2/favicons?domain=spotify.com&sz=64)

![New Relic](https://www.google.com/s2/favicons?domain=newrelic.com&sz=64)

![PostHog](https://www.google.com/s2/favicons?domain=posthog.com&sz=64)

![CircleCI](https://www.google.com/s2/favicons?domain=circleci.com&sz=64)

![Buildkite](https://www.google.com/s2/favicons?domain=buildkite.com&sz=64)

![Square](https://www.google.com/s2/favicons?domain=squareup.com&sz=64)

![Adyen](https://www.google.com/s2/favicons?domain=adyen.com&sz=64)

![Checkout.com](https://www.google.com/s2/favicons?domain=checkout.com&sz=64)

![Dwolla](https://www.google.com/s2/favicons?domain=dwolla.com&sz=64)

![Shopify](https://www.google.com/s2/favicons?domain=shopify.com&sz=64)

![HubSpot](https://www.google.com/s2/favicons?domain=hubspot.com&sz=64)

![Intercom](https://www.google.com/s2/favicons?domain=intercom.com&sz=64)

![Anthropic](https://www.google.com/s2/favicons?domain=anthropic.com&sz=64)

![OpenAI](https://www.google.com/s2/favicons?domain=openai.com&sz=64)

![Stripe](https://www.google.com/s2/favicons?domain=stripe.com&sz=64)

![GitHub](https://www.google.com/s2/favicons?domain=github.com&sz=64)

![Slack](https://www.google.com/s2/favicons?domain=slack.com&sz=64)

![Twilio](https://www.google.com/s2/favicons?domain=twilio.com&sz=64)

![Mistral](https://www.google.com/s2/favicons?domain=mistral.ai&sz=64)

![Vercel](https://www.google.com/s2/favicons?domain=vercel.com&sz=64)

![Cloudflare](https://www.google.com/s2/favicons?domain=cloudflare.com&sz=64)

![Coinbase](https://www.google.com/s2/favicons?domain=coinbase.com&sz=64)

![Discord](https://www.google.com/s2/favicons?domain=discord.com&sz=64)

![Sentry](https://www.google.com/s2/favicons?domain=sentry.io&sz=64)

![Datadog](https://www.google.com/s2/favicons?domain=datadoghq.com&sz=64)

![PagerDuty](https://www.google.com/s2/favicons?domain=pagerduty.com&sz=64)

![SendGrid](https://www.google.com/s2/favicons?domain=sendgrid.com&sz=64)

![PayPal](https://www.google.com/s2/favicons?domain=paypal.com&sz=64)

![Netlify](https://www.google.com/s2/favicons?domain=netlify.com&sz=64)

![Railway](https://www.google.com/s2/favicons?domain=railway.app&sz=64)

![Fly.io](https://www.google.com/s2/favicons?domain=fly.io&sz=64)

![Render](https://www.google.com/s2/favicons?domain=render.com&sz=64)

![DigitalOcean](https://www.google.com/s2/favicons?domain=digitalocean.com&sz=64)

![GitLab](https://www.google.com/s2/favicons?domain=gitlab.com&sz=64)

![Groq](https://www.google.com/s2/favicons?domain=groq.com&sz=64)

![Cohere](https://www.google.com/s2/favicons?domain=cohere.com&sz=64)

![Perplexity](https://www.google.com/s2/favicons?domain=perplexity.ai&sz=64)

![Deepseek](https://www.google.com/s2/favicons?domain=deepseek.com&sz=64)

![Resend](https://www.google.com/s2/favicons?domain=resend.com&sz=64)

![Postmark](https://www.google.com/s2/favicons?domain=postmarkapp.com&sz=64)

![Plaid](https://www.google.com/s2/favicons?domain=plaid.com&sz=64)

![Clerk](https://www.google.com/s2/favicons?domain=clerk.com&sz=64)

![Mercury](https://www.google.com/s2/favicons?domain=mercury.com&sz=64)

![Ramp](https://www.google.com/s2/favicons?domain=ramp.com&sz=64)

![Wise](https://www.google.com/s2/favicons?domain=wise.com&sz=64)

![Notion](https://www.google.com/s2/favicons?domain=notion.so&sz=64)

![Linear](https://www.google.com/s2/favicons?domain=linear.app&sz=64)

![Airtable](https://www.google.com/s2/favicons?domain=airtable.com&sz=64)

![Spotify](https://www.google.com/s2/favicons?domain=spotify.com&sz=64)

![New Relic](https://www.google.com/s2/favicons?domain=newrelic.com&sz=64)

![PostHog](https://www.google.com/s2/favicons?domain=posthog.com&sz=64)

![CircleCI](https://www.google.com/s2/favicons?domain=circleci.com&sz=64)

![Buildkite](https://www.google.com/s2/favicons?domain=buildkite.com&sz=64)

![Square](https://www.google.com/s2/favicons?domain=squareup.com&sz=64)

![Adyen](https://www.google.com/s2/favicons?domain=adyen.com&sz=64)

![Checkout.com](https://www.google.com/s2/favicons?domain=checkout.com&sz=64)

![Dwolla](https://www.google.com/s2/favicons?domain=dwolla.com&sz=64)

![Shopify](https://www.google.com/s2/favicons?domain=shopify.com&sz=64)

![HubSpot](https://www.google.com/s2/favicons?domain=hubspot.com&sz=64)

![Intercom](https://www.google.com/s2/favicons?domain=intercom.com&sz=64)

![Anthropic](https://www.google.com/s2/favicons?domain=anthropic.com&sz=64)

![OpenAI](https://www.google.com/s2/favicons?domain=openai.com&sz=64)

![Stripe](https://www.google.com/s2/favicons?domain=stripe.com&sz=64)

![GitHub](https://www.google.com/s2/favicons?domain=github.com&sz=64)

![Slack](https://www.google.com/s2/favicons?domain=slack.com&sz=64)

![Twilio](https://www.google.com/s2/favicons?domain=twilio.com&sz=64)

![Mistral](https://www.google.com/s2/favicons?domain=mistral.ai&sz=64)

![Vercel](https://www.google.com/s2/favicons?domain=vercel.com&sz=64)

![Cloudflare](https://www.google.com/s2/favicons?domain=cloudflare.com&sz=64)

![Coinbase](https://www.google.com/s2/favicons?domain=coinbase.com&sz=64)

![Discord](https://www.google.com/s2/favicons?domain=discord.com&sz=64)

![Sentry](https://www.google.com/s2/favicons?domain=sentry.io&sz=64)

![Datadog](https://www.google.com/s2/favicons?domain=datadoghq.com&sz=64)

![PagerDuty](https://www.google.com/s2/favicons?domain=pagerduty.com&sz=64)

![SendGrid](https://www.google.com/s2/favicons?domain=sendgrid.com&sz=64)

![PayPal](https://www.google.com/s2/favicons?domain=paypal.com&sz=64)

![Netlify](https://www.google.com/s2/favicons?domain=netlify.com&sz=64)

![Railway](https://www.google.com/s2/favicons?domain=railway.app&sz=64)

![Fly.io](https://www.google.com/s2/favicons?domain=fly.io&sz=64)

![Render](https://www.google.com/s2/favicons?domain=render.com&sz=64)

![DigitalOcean](https://www.google.com/s2/favicons?domain=digitalocean.com&sz=64)

![GitLab](https://www.google.com/s2/favicons?domain=gitlab.com&sz=64)

![Groq](https://www.google.com/s2/favicons?domain=groq.com&sz=64)

![Cohere](https://www.google.com/s2/favicons?domain=cohere.com&sz=64)

![Perplexity](https://www.google.com/s2/favicons?domain=perplexity.ai&sz=64)

![Deepseek](https://www.google.com/s2/favicons?domain=deepseek.com&sz=64)

![Resend](https://www.google.com/s2/favicons?domain=resend.com&sz=64)

![Postmark](https://www.google.com/s2/favicons?domain=postmarkapp.com&sz=64)

![Plaid](https://www.google.com/s2/favicons?domain=plaid.com&sz=64)

![Clerk](https://www.google.com/s2/favicons?domain=clerk.com&sz=64)

![Mercury](https://www.google.com/s2/favicons?domain=mercury.com&sz=64)

![Ramp](https://www.google.com/s2/favicons?domain=ramp.com&sz=64)

![Wise](https://www.google.com/s2/favicons?domain=wise.com&sz=64)

![Notion](https://www.google.com/s2/favicons?domain=notion.so&sz=64)

![Linear](https://www.google.com/s2/favicons?domain=linear.app&sz=64)

![Airtable](https://www.google.com/s2/favicons?domain=airtable.com&sz=64)

![Spotify](https://www.google.com/s2/favicons?domain=spotify.com&sz=64)

![New Relic](https://www.google.com/s2/favicons?domain=newrelic.com&sz=64)

![PostHog](https://www.google.com/s2/favicons?domain=posthog.com&sz=64)

![CircleCI](https://www.google.com/s2/favicons?domain=circleci.com&sz=64)

![Buildkite](https://www.google.com/s2/favicons?domain=buildkite.com&sz=64)

![Square](https://www.google.com/s2/favicons?domain=squareup.com&sz=64)

![Adyen](https://www.google.com/s2/favicons?domain=adyen.com&sz=64)

![Checkout.com](https://www.google.com/s2/favicons?domain=checkout.com&sz=64)

![Dwolla](https://www.google.com/s2/favicons?domain=dwolla.com&sz=64)

![Shopify](https://www.google.com/s2/favicons?domain=shopify.com&sz=64)

![HubSpot](https://www.google.com/s2/favicons?domain=hubspot.com&sz=64)

![Intercom](https://www.google.com/s2/favicons?domain=intercom.com&sz=64)

## Works With Your Stack

![OpenClaw](https://www.google.com/s2/favicons?domain=openclaw.ai&sz=64)

OpenClaw

![Claude Code](https://www.google.com/s2/favicons?domain=anthropic.com&sz=64)

Claude Code

![Claude](https://www.google.com/s2/favicons?domain=claude.ai&sz=64)

Claude

![Codex](https://www.google.com/s2/favicons?domain=openai.com&sz=64)

Codex

![Cursor](https://www.google.com/s2/favicons?domain=cursor.com&sz=64)

Cursor

auto\_awesome

Custom Agents

Ready for 70+ API integrations

[View GitHub Repository](https://github.com/getsesame)

## Install in three simple steps

bash — sesame-install

1curl -sSL https://getsesame.dev/install.sh | sh

2sesame login

3sesame request POST https://api.stripe.com/v1/payment\_intents ...

4\# \[Success\] Proxy running at localhost:8080

5\# \[Ready\] 76 providers discovered in vault.

## Ready to secure your agents?

Join developers building trustable AI applications with Sesame.

Sign In[Contact us](mailto:hi@getsesame.dev)
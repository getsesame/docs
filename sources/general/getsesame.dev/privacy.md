# Source: https://getsesame.dev/privacy

# Privacy Policy

Last updated: April 19, 2026

## Overview

Sesame ("we", "our", "us") is an open-source credential broker that lets AI agents make authenticated API requests without directly accessing your secrets. This policy describes how we collect, use, and protect your information when you use the Sesame web dashboard, mobile app, and broker service.

## Information We Collect

### Account Information

When you sign in with Google, we receive your email address and display name. This is used solely for authentication and identifying your account.

### API Credentials (Secrets)

You may store API keys, tokens, and webhook URLs. Secret values are encrypted and stored in AWS Secrets Manager — they are never stored in our application database. Only metadata (label, hostname, injection mode) is stored in our database to facilitate the proxy flow.

### Device & Agent Information

When you register an AI agent, we collect the device hostname, platform (OS), and a device fingerprint. This is used to identify which agent is requesting access to your secrets.

### Push Notification Tokens

If you use the Sesame mobile app, we collect your Expo push notification token to deliver real-time approval requests to your device. Tokens are removed when you sign out.

### Telegram Integration

If you configure Telegram notifications, we store your Telegram bot token and chat ID to send approval requests. You can remove this at any time from Settings.

### Audit Logs

We log all proxy requests, authorization events, and administrative actions. Logs include the target hostname, HTTP method, status codes, and timestamps. Logs do not contain request bodies or secret values.

### Analytics (Landing Page Only)

On our public landing page at **getsesame.dev**, we use [PostHog](https://posthog.com/privacy) to collect anonymous product analytics — pageviews, button clicks, referring domain, and approximate country (from IP, which is then discarded). PostHog is configured in anonymous mode: no user profiles are created, no session recording is performed, and your IP address is stripped server-side. A non-identifying browser cookie is used to count distinct visitors. Analytics are **not** collected on authenticated pages (dashboard, secrets, agents, settings). You can opt out of analytics entirely by enabling “Do Not Track” in your browser.

## How We Use Your Information

- Authenticate your identity and manage your account
- Proxy API requests on behalf of your AI agents with credential injection
- Send approval notifications via push notifications, Telegram, or web
- Enforce access policies and time-limited authorizations
- Maintain audit trails for security and transparency

## Data Storage & Security

- Secret values are stored in AWS Secrets Manager with encryption at rest
- Application data is stored in Supabase (PostgreSQL) with row-level security — users can only access their own data
- All connections use TLS encryption in transit
- The broker service runs on AWS infrastructure in the US East region

## Data Sharing

We do not sell, rent, or share your personal information with third parties. Your data is only transmitted to:

- **AWS** — for secret storage (encrypted)
- **Supabase** — for authentication and application data
- **Expo / Google FCM** — for push notification delivery
- **Telegram** — only if you configure Telegram notifications
- **PostHog** — anonymous landing page analytics only (see Analytics section above)
- **Target API providers** — when proxying requests on behalf of your agents

## Data Retention

Account data and secrets are retained as long as your account is active. Audit logs are retained for 90 days. Push notification tokens are removed when you sign out of the mobile app.

## Your Rights

- **Access** — View all your data through the web dashboard or mobile app
- **Deletion** — Delete your account and all associated data from Settings
- **Portability** — Export your secret metadata and audit logs
- **Revocation** — Revoke any agent's access or delete any secret at any time

## Children's Privacy

Sesame is not intended for use by children under 13. We do not knowingly collect personal information from children.

## Changes to This Policy

We may update this policy from time to time. Changes will be posted on this page with an updated date. Continued use of Sesame after changes constitutes acceptance of the updated policy.

## Contact

For questions about this privacy policy or your data, contact us at [hi@getsesame.dev](mailto:hi@getsesame.dev).
# Source: https://github.com/getsesame/skills/blob/main/README.md

[getsesame](https://github.com/getsesame) / **[skills](https://github.com/getsesame/skills)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fskills) You must be signed in to change notification settings
- [Fork 1](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
 

 

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

[History](https://github.com/getsesame/skills/commits/main/README.md)

History

38 lines (26 loc) · 1.79 KB

 main

/

# README.md

Copy path

Top

## File metadata and controls

- Preview
 
- Code
 
- Blame
 

38 lines (26 loc) · 1.79 KB

[Raw](https://github.com/getsesame/skills/raw/refs/heads/main/README.md)

Copy raw file

Download raw file

Outline

Edit and raw actions

# Sesame Skills

Agent skills for [Sesame](https://github.com/getsesame) — a user-controlled broker that proxies authenticated HTTP API calls, so agents don't need to handle auth material directly.

## Install

```shell
npx skills add getsesame/skills
```

This auto-detects your agent platform (Claude Code, Codex, Cursor, etc.) and installs the skill to the right location.

> **Note on a global install:** `skills add --global` writes the skill for _every_ supported agent. You may see a line like `PromptScript does not support global skill installation` — this is **harmless**. PromptScript only supports project-level installs, so it is skipped while the skill installs successfully for every other agent (the command still exits 0). For a fully clean run, install from inside a project directory (scope is then project-level and every adapter succeeds).

## What it does

When installed, the Sesame skill teaches your AI agent to:

1. Route authenticated HTTP requests through `sesame request` instead of `curl`
2. Check which API hostnames are configured via `sesame hostnames`
3. Handle the approval flow the first time an agent reaches a new hostname
4. Leave auth headers to the broker — the agent never needs to construct them

## Prerequisites

- **sesame** CLI installed — see [https://getsesame.dev](https://getsesame.dev) for install instructions
- Agent registered with your Sesame broker: `sesame login`
- At least one hostname configured in the Sesame dashboard

## Available skills

| Skill | Description |
| --- | --- |
| [sesame](https://github.com/getsesame/skills/blob/main/skills/sesame) | Proxy authenticated API calls through the Sesame broker via `sesame` |
| [sesame-onboard](https://github.com/getsesame/skills/blob/main/skills/sesame-onboard) | Walk a user through deploying a self-hosted Sesame broker to their own AWS (AWS CLI + login, Google setup with links, interactive dry-run, deploy) |
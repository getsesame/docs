# Source: https://github.com/getsesame/skills

[getsesame](https://github.com/getsesame) / **[skills](https://github.com/getsesame/skills)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fskills) You must be signed in to change notification settings
- [Fork 1](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
 

 

 main

[Branches](https://github.com/getsesame/skills/branches) [Tags](https://github.com/getsesame/skills/tags)

Go to file

Code

Open more actions menu

## Folders and files

| Name | Name | 
Last commit message

 | 

Last commit date

 |
| --- | --- | --- | --- |
| 

## Latest commit

## History

[15 Commits](https://github.com/getsesame/skills/commits/main/)

15 Commits

 |
| 

[.github/workflows](https://github.com/getsesame/skills/tree/main/.github/workflows 'This path skips through empty directories')

 | 

[.github/workflows](https://github.com/getsesame/skills/tree/main/.github/workflows 'This path skips through empty directories')

 | 

 | 

 |
| 

[scripts](https://github.com/getsesame/skills/tree/main/scripts 'scripts')

 | 

[scripts](https://github.com/getsesame/skills/tree/main/scripts 'scripts')

 | 

 | 

 |
| 

[skills](https://github.com/getsesame/skills/tree/main/skills 'skills')

 | 

[skills](https://github.com/getsesame/skills/tree/main/skills 'skills')

 | 

 | 

 |
| 

[README.md](https://github.com/getsesame/skills/blob/main/README.md 'README.md')

 | 

[README.md](https://github.com/getsesame/skills/blob/main/README.md 'README.md')

 | 

 | 

 |
| 

View all files

 |

## Repository files navigation

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

## About

Agent skills for Sesame. Teach your AI agent (Claude Code, Codex, Cursor, +42 more) to call APIs through your Sesame broker via \`sesame request\` — install with: npx skills add getsesame/skills

[skills.sh/getsesame/skills](https://skills.sh/getsesame/skills 'https://skills.sh/getsesame/skills')

### Topics

[authentication](https://github.com/topics/authentication 'Topic: authentication') [skills](https://github.com/topics/skills 'Topic: skills') [sesame](https://github.com/topics/sesame 'Topic: sesame') [cursor](https://github.com/topics/cursor 'Topic: cursor') [codex](https://github.com/topics/codex 'Topic: codex') [ai-agents](https://github.com/topics/ai-agents 'Topic: ai-agents') [secrets-management](https://github.com/topics/secrets-management 'Topic: secrets-management') [agent-skills](https://github.com/topics/agent-skills 'Topic: agent-skills') [claude-code](https://github.com/topics/claude-code 'Topic: claude-code')

### Resources

[Readme](https://github.com/#readme-ov-file)

### Uh oh!

There was an error while loading. [Please reload this page]().

[Activity](https://github.com/getsesame/skills/activity)

[Custom properties](https://github.com/getsesame/skills/custom-properties)

### Stars

[**0** stars](https://github.com/getsesame/skills/stargazers)

### Watchers

[**0** watching](https://github.com/getsesame/skills/watchers)

### Forks

[**1** fork](https://github.com/getsesame/skills/forks)

[Report repository](https://github.com/contact/report-content?content_url=https%3A%2F%2Fgithub.com%2Fgetsesame%2Fskills&report=getsesame+%28user%29)

## [Releases](https://github.com/getsesame/skills/releases)

[4 tags](https://github.com/getsesame/skills/tags)

## [Packages 0](https://github.com/orgs/getsesame/packages?repo_name=skills)

### Uh oh!

There was an error while loading. [Please reload this page]().

## [Contributors 3](https://github.com/getsesame/skills/graphs/contributors)

- [![@lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?s=64&v=4)](https://github.com/lavanpuri1999)[**lavanpuri1999** lavanpuri](https://github.com/lavanpuri1999)
- [![@kkumar30](https://avatars.githubusercontent.com/u/12945097?s=64&v=4)](https://github.com/kkumar30)[**kkumar30**](https://github.com/kkumar30)
- [![@claude](https://avatars.githubusercontent.com/u/81847?s=64&v=4)](https://github.com/claude)[**claude** Claude](https://github.com/claude)

## Languages

- [Python 100.0%](https://github.com/getsesame/skills/search?l=python)
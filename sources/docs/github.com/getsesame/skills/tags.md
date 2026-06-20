# Source: https://github.com/getsesame/skills/tags

[getsesame](https://github.com/getsesame) / **[skills](https://github.com/getsesame/skills)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fskills) You must be signed in to change notification settings
- [Fork 1](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
 

# Tags: getsesame/skills

Tags

## [v0.5.1](https://github.com/getsesame/skills/releases/tag/v0.5.1)

Toggle v0.5.1's commit message

Verified

# Verified

This commit was created on GitHub.com and signed with GitHub’s **verified signature**.

GPG key ID: B5690EEEBB952194

Verified

[Learn about vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits)

docs: fix stale secretctl->sesame in README + note harmless PromptScr…

…ipt global-install message ([#8](https://github.com/getsesame/skills/pull/8))

- Jun 15, 2026
- [9a5cd9d](https://github.com/getsesame/skills/commit/9a5cd9d46a7ec4b61d74c13aa00f3a9eae9b54fa)
- [zip](https://github.com/getsesame/skills/archive/refs/tags/v0.5.1.zip)
- [tar.gz](https://github.com/getsesame/skills/archive/refs/tags/v0.5.1.tar.gz)

## [v0.5.0](https://github.com/getsesame/skills/releases/tag/v0.5.0)

Toggle v0.5.0's commit message

Verified

# Verified

This commit was created on GitHub.com and signed with GitHub’s **verified signature**.

GPG key ID: B5690EEEBB952194

Verified

[Learn about vigilant mode](https://docs.github.com/github/authenticating-to-github/displaying-verification-statuses-for-all-of-your-commits)

rename \`sesame doctor\` to \`sesame police\` ([#7](https://github.com/getsesame/skills/pull/7))

The CLI command was renamed ([getsesame/sesame-core#88](https://github.com/getsesame/sesame-core/pull/88)). Update the skill to
match: \`doctor\` → \`police\` in the subcommand surface and the command
reference, and correct the description — it audits this machine for plaintext
secrets an agent could read, it does not "diagnose config/connectivity".

- Jun 14, 2026
- [d970ef8](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425)
- [zip](https://github.com/getsesame/skills/archive/refs/tags/v0.5.0.zip)
- [tar.gz](https://github.com/getsesame/skills/archive/refs/tags/v0.5.0.tar.gz)

## [v0.4.0](https://github.com/getsesame/skills/releases/tag/v0.4.0)

Toggle v0.4.0's commit message

rename: secretctl → sesame across SKILL.md and references

Mirrors the CLI rename in getsesame/sesame (was getsesame/secretctl).
Hard cut — no alias.

- SKILL.md: 41 references updated; allowed-tools is now
 Bash(sesame:\*) (was Bash(secretctl:\*)). Skill version bumped
 0.3.1 → 0.4.0 to signal the breaking allow-list change.
- references/examples.md: 22 references in API-call examples.
- references/troubleshooting.md: 14 references in error-recovery copy.

Skills harnesses that previously approved Bash(secretctl:\*) will
re-prompt because the allow-list is the only safety surface here.
That's intentional — it gives the user a chance to acknowledge
the new binary name.

- Apr 25, 2026
- [daa3d58](https://github.com/getsesame/skills/commit/daa3d583c719e75e13575bf0faa27acd5a6b0fe1)
- [zip](https://github.com/getsesame/skills/archive/refs/tags/v0.4.0.zip)
- [tar.gz](https://github.com/getsesame/skills/archive/refs/tags/v0.4.0.tar.gz)

## [v0.3.1](https://github.com/getsesame/skills/releases/tag/v0.3.1)

Toggle v0.3.1's commit message

rename: secretctl → sesame across SKILL.md and references

Mirrors the CLI rename in getsesame/sesame (was getsesame/secretctl).
Hard cut — no alias.

- SKILL.md: 41 references updated; allowed-tools is now
 Bash(sesame:\*) (was Bash(secretctl:\*)). Skill version bumped
 0.3.1 → 0.4.0 to signal the breaking allow-list change.
- references/examples.md: 22 references in API-call examples.
- references/troubleshooting.md: 14 references in error-recovery copy.

Skills harnesses that previously approved Bash(secretctl:\*) will
re-prompt because the allow-list is the only safety surface here.
That's intentional — it gives the user a chance to acknowledge
the new binary name.

- Apr 25, 2026
- [daa3d58](https://github.com/getsesame/skills/commit/daa3d583c719e75e13575bf0faa27acd5a6b0fe1)
- [zip](https://github.com/getsesame/skills/archive/refs/tags/v0.3.1.zip)
- [tar.gz](https://github.com/getsesame/skills/archive/refs/tags/v0.3.1.tar.gz)
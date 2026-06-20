# Source: https://github.com/getsesame/skills/commits/main

[getsesame](https://github.com/getsesame) / **[skills](https://github.com/getsesame/skills)** Public

- [Notifications](https://github.com/login?return_to=%2Fgetsesame%2Fskills) You must be signed in to change notification settings
- [Fork 1](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
- [Star 0](https://github.com/login?return_to=%2Fgetsesame%2Fskills)
 

 

## Branch selector

 main

## User selector

All users

## Datepicker

All time

## Commit History

### Commits on Jun 15, 2026

- #### [docs: fix stale secretctl->sesame in README + note harmless PromptScript global-install message (](https://github.com/getsesame/skills/commit/9a5cd9d46a7ec4b61d74c13aa00f3a9eae9b54fa 'docs: fix stale secretctl->sesame in README + note harmless PromptScript global-install message (#8)') [#8](https://github.com/getsesame/skills/pull/8) [)](https://github.com/getsesame/skills/commit/9a5cd9d46a7ec4b61d74c13aa00f3a9eae9b54fa 'docs: fix stale secretctl->sesame in README + note harmless PromptScript global-install message (#8)')
 
 [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
 
 authoredJun 15, 2026
 
 [9a5cd9d](https://github.com/getsesame/skills/commit/9a5cd9d46a7ec4b61d74c13aa00f3a9eae9b54fa)
 
 Copy full SHA for 9a5cd9d
 
- #### [docs(readme): use the current](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)
 
 The CLI is `sesame`; the README still referenced the old `secretctl` name in
 5 places (request/hostnames/login examples, the prerequisite, and the skills
 table). The skill files themselves were already correct.') ``[sesame](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)  The CLI is `sesame`; the README still referenced the old `secretctl` name in 5 places (request/hostnames/login examples, the prerequisite, and the skills table). The skill files themselves were already correct.')`` [CLI name (was](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)
    
    The CLI is `sesame`; the README still referenced the old `secretctl` name in
    5 places (request/hostnames/login examples, the prerequisite, and the skills
    table). The skill files themselves were already correct.') ``[secretctl](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)  The CLI is `sesame`; the README still referenced the old `secretctl` name in 5 places (request/hostnames/login examples, the prerequisite, and the skills table). The skill files themselves were already correct.')``[) (](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)
    
    The CLI is `sesame`; the README still referenced the old `secretctl` name in
    5 places (request/hostnames/login examples, the prerequisite, and the skills
    table). The skill files themselves were already correct.') [#10](https://github.com/getsesame/skills/pull/10) [)](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190 'docs(readme): use the current `sesame` CLI name (was `secretctl`) (#10)
    
    The CLI is `sesame`; the README still referenced the old `secretctl` name in
    5 places (request/hostnames/login examples, the prerequisite, and the skills
    table). The skill files themselves were already correct.')
    
    Show description for b01aec9
    
    [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
    
    authoredJun 15, 2026
    
    [b01aec9](https://github.com/getsesame/skills/commit/b01aec91cf77ea056287b41ebf418a79ff2bc190)
    
    Copy full SHA for b01aec9
    
-   #### [fix(sesame-onboard): resolve Snyk W007/W021 + add skill-security audit CI (](https://github.com/getsesame/skills/commit/222f3fb6fff46437bd7f0a9b5d4811535c4b8157 'fix(sesame-onboard): resolve Snyk W007/W021 + add skill-security audit CI (#9)
    
    * fix(sesame-onboard): resolve Snyk W007/W021 + add skill-security audit CI
    
    The published security audit flagged sesame-onboard:
    - W007 (HIGH): the skill let the agent take the Google client secret in chat
      and inject it into `--google-client-secret`, forcing the model to output the
      secret.
    - W021 (MEDIUM): an invisible U+FE0F variation selector.
    
    Fixes:
    - The agent never accepts or emits the client secret. The client *ID* is
      public (passed via `--google-client-id`); the secret reaches the deploy only
      through the CLI's hidden prompt when the **user** runs the Google deploy
      themselves. The `--google-client-secret` flag still exists for a user's own
      non-interactive deploy — documented as such, never used by the agent.
    - Stripped the U+FE0F characters.
    - Added a `sesame --version` prerequisite (Step 0) and an inline "the user runs
      this, not the agent" guard on the Google deploy command, plus an explicit
      ask to paste the deploy output back (it prints in the user's terminal).
    
    Prevention:
    - scripts/skill_audit.py: a local/CI approximation of the audit — deterministic
      for W021, heuristic for W007. Reproduces the exact two findings on the old
      file and passes on the fix.
    - .github/workflows/skill-audit.yml: runs it on every PR/push (pure stdlib).
    
    Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
    
    * docs(sesame-onboard): agent-run Google deploy errors out, not hangs
    
    The CLI gates the hidden 'Google client secret' prompt on sys.stdin.isatty();
    with no TTY (agent run) it skips the prompt and exits with an error asking for
    --google-client-secret, rather than hanging. Match the doc to the behavior.
    
    ---------
    
    Co-authored-by: Claude Fable 5 <noreply@anthropic.com>') [#9](https://github.com/getsesame/skills/pull/9) [)](https://github.com/getsesame/skills/commit/222f3fb6fff46437bd7f0a9b5d4811535c4b8157 'fix(sesame-onboard): resolve Snyk W007/W021 + add skill-security audit CI (#9)
    
    * fix(sesame-onboard): resolve Snyk W007/W021 + add skill-security audit CI
    
    The published security audit flagged sesame-onboard:
    - W007 (HIGH): the skill let the agent take the Google client secret in chat
      and inject it into `--google-client-secret`, forcing the model to output the
      secret.
    - W021 (MEDIUM): an invisible U+FE0F variation selector.
    
    Fixes:
    - The agent never accepts or emits the client secret. The client *ID* is
      public (passed via `--google-client-id`); the secret reaches the deploy only
      through the CLI's hidden prompt when the **user** runs the Google deploy
      themselves. The `--google-client-secret` flag still exists for a user's own
      non-interactive deploy — documented as such, never used by the agent.
    - Stripped the U+FE0F characters.
    - Added a `sesame --version` prerequisite (Step 0) and an inline "the user runs
      this, not the agent" guard on the Google deploy command, plus an explicit
      ask to paste the deploy output back (it prints in the user's terminal).
    
    Prevention:
    - scripts/skill_audit.py: a local/CI approximation of the audit — deterministic
      for W021, heuristic for W007. Reproduces the exact two findings on the old
      file and passes on the fix.
    - .github/workflows/skill-audit.yml: runs it on every PR/push (pure stdlib).
    
    Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>
    
    * docs(sesame-onboard): agent-run Google deploy errors out, not hangs
    
    The CLI gates the hidden 'Google client secret' prompt on sys.stdin.isatty();
    with no TTY (agent run) it skips the prompt and exits with an error asking for
    --google-client-secret, rather than hanging. Match the doc to the behavior.
    
    ---------
    
    Co-authored-by: Claude Fable 5 <noreply@anthropic.com>')
    
    Show description for 222f3fb
    
    ![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)![claude](https://avatars.githubusercontent.com/u/81847?v=4&size=32)
    
    [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
    
    and
    
    [claude](https://github.com/getsesame/skills/commits?author=claude)
    
    authoredJun 15, 2026
    
    [222f3fb](https://github.com/getsesame/skills/commit/222f3fb6fff46437bd7f0a9b5d4811535c4b8157)
    
    Copy full SHA for 222f3fb
    

### Commits on Jun 14, 2026

-   #### [rename](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)
    
    The CLI command was renamed (getsesame/sesame-core#88). Update the skill to
    match: `doctor` → `police` in the subcommand surface and the command
    reference, and correct the description — it audits this machine for plaintext
    secrets an agent could read, it does not "diagnose config/connectivity".') ``[sesame doctor](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)  The CLI command was renamed (getsesame/sesame-core#88). Update the skill to match: `doctor` → `police` in the subcommand surface and the command reference, and correct the description — it audits this machine for plaintext secrets an agent could read, it does not "diagnose config/connectivity".')`` [to](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)
    
    The CLI command was renamed (getsesame/sesame-core#88). Update the skill to
    match: `doctor` → `police` in the subcommand surface and the command
    reference, and correct the description — it audits this machine for plaintext
    secrets an agent could read, it does not "diagnose config/connectivity".') ``[sesame police](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)  The CLI command was renamed (getsesame/sesame-core#88). Update the skill to match: `doctor` → `police` in the subcommand surface and the command reference, and correct the description — it audits this machine for plaintext secrets an agent could read, it does not "diagnose config/connectivity".')`` [(](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)
    
    The CLI command was renamed (getsesame/sesame-core#88). Update the skill to
    match: `doctor` → `police` in the subcommand surface and the command
    reference, and correct the description — it audits this machine for plaintext
    secrets an agent could read, it does not "diagnose config/connectivity".') [#7](https://github.com/getsesame/skills/pull/7) [)](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425 'rename `sesame doctor` to `sesame police` (#7)
    
    The CLI command was renamed (getsesame/sesame-core#88). Update the skill to
    match: `doctor` → `police` in the subcommand surface and the command
    reference, and correct the description — it audits this machine for plaintext
    secrets an agent could read, it does not "diagnose config/connectivity".')
    
    Show description for d970ef8
    
    [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
    
    authoredJun 14, 2026
    
    [d970ef8](https://github.com/getsesame/skills/commit/d970ef812abc54fa74663c38a2bda1231a6e4425)
    
    Copy full SHA for d970ef8
    

### Commits on Jun 13, 2026

-   #### [sesame skill: add per-command reference + command discovery (](https://github.com/getsesame/skills/commit/c7816c02e9d6855447d8b3dd90fa6e0dfad532f7 'sesame skill: add per-command reference + command discovery (#6)') [#6](https://github.com/getsesame/skills/pull/6) [)](https://github.com/getsesame/skills/commit/c7816c02e9d6855447d8b3dd90fa6e0dfad532f7 'sesame skill: add per-command reference + command discovery (#6)')
    
    [![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)](https://github.com/lavanpuri1999) [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
    
    authoredJun 13, 2026
    
    [c7816c0](https://github.com/getsesame/skills/commit/c7816c02e9d6855447d8b3dd90fa6e0dfad532f7)
    
    Copy full SHA for c7816c0
    

### Commits on Jun 8, 2026

-   #### [sesame skill: add](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)
    
    The skill enumerated request/status/hostnames/login/refresh as the fixed
    subcommand surface and omitted `sesame switch` (multi-agent device switching),
    leading agents to assume it didn't exist. Add `switch`, and note the list is a
    subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.') ``[switch](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)  The skill enumerated request/status/hostnames/login/refresh as the fixed subcommand surface and omitted `sesame switch` (multi-agent device switching), leading agents to assume it didn't exist. Add `switch`, and note the list is a subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.')`` [to the command surface + point to](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)
    
    The skill enumerated request/status/hostnames/login/refresh as the fixed
    subcommand surface and omitted `sesame switch` (multi-agent device switching),
    leading agents to assume it didn't exist. Add `switch`, and note the list is a
    subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.') ``[sesame --help](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)  The skill enumerated request/status/hostnames/login/refresh as the fixed subcommand surface and omitted `sesame switch` (multi-agent device switching), leading agents to assume it didn't exist. Add `switch`, and note the list is a subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.')`` [(](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)
    
    The skill enumerated request/status/hostnames/login/refresh as the fixed
    subcommand surface and omitted `sesame switch` (multi-agent device switching),
    leading agents to assume it didn't exist. Add `switch`, and note the list is a
    subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.') [#5](https://github.com/getsesame/skills/pull/5) [)](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300 'sesame skill: add `switch` to the command surface + point to `sesame --help` (#5)
    
    The skill enumerated request/status/hostnames/login/refresh as the fixed
    subcommand surface and omitted `sesame switch` (multi-agent device switching),
    leading agents to assume it didn't exist. Add `switch`, and note the list is a
    subset — the full CLI is `sesame --help` — so agents don't treat it as exhaustive.')
    
    Show description for 44bd705
    
    [![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)](https://github.com/lavanpuri1999) [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
    
    authoredJun 8, 2026
    
    [44bd705](https://github.com/getsesame/skills/commit/44bd705a92ec5d48327f5cdcfea49cd8593bc300)
    
    Copy full SHA for 44bd705
    

### Commits on Jun 5, 2026

-   #### [Onboarding skills: agent-led self-host deploy + first-run broker URL (](https://github.com/getsesame/skills/commit/85e993698291af7e3d0c0fc5fa6e66f23b0043b3 'Onboarding skills: agent-led self-host deploy + first-run broker URL (#4)
    
    Adds the `sesame-onboard` skill — an agent walks a user through `sesame deploy
 aws`: checks/installs the AWS CLI and verifies login, collects the required
    values, gives click-by-click Google OAuth setup (with the Workspace-vs-External
    branch), runs a dry-run to confirm, then deploys. Secrets are injected as flags
    or typed into the CLI's hidden prompts, never pasted into chat.
    
    Also updates the `sesame` runtime skill: on first run it asks the user for the
    broker URL (cloud getsesame.dev vs a company self-hosted URL) and registers with
    `sesame login --broker-url <url>`, which persists it for later calls.') [#4](https://github.com/getsesame/skills/pull/4) [)](https://github.com/getsesame/skills/commit/85e993698291af7e3d0c0fc5fa6e66f23b0043b3 'Onboarding skills: agent-led self-host deploy + first-run broker URL (#4)
    
    Adds the `sesame-onboard` skill — an agent walks a user through `sesame deploy
 aws`: checks/installs the AWS CLI and verifies login, collects the required
    values, gives click-by-click Google OAuth setup (with the Workspace-vs-External
    branch), runs a dry-run to confirm, then deploys. Secrets are injected as flags
    or typed into the CLI's hidden prompts, never pasted into chat.
    
    Also updates the `sesame` runtime skill: on first run it asks the user for the
    broker URL (cloud getsesame.dev vs a company self-hosted URL) and registers with
    `sesame login --broker-url <url>`, which persists it for later calls.')
 
 Show description for 85e9936
 
 [![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)](https://github.com/lavanpuri1999) [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 authoredJun 5, 2026
 
 [85e9936](https://github.com/getsesame/skills/commit/85e993698291af7e3d0c0fc5fa6e66f23b0043b3)
 
 Copy full SHA for 85e9936
 

### Commits on Apr 25, 2026

- #### [rename: secretctl → sesame across SKILL.md and references](https://github.com/getsesame/skills/commit/daa3d583c719e75e13575bf0faa27acd5a6b0fe1 'rename: secretctl → sesame across SKILL.md and references
 
 Mirrors the CLI rename in getsesame/sesame (was getsesame/secretctl).
 Hard cut — no alias.
 
 - SKILL.md: 41 references updated; allowed-tools is now
 Bash(sesame:*) (was Bash(secretctl:*)). Skill version bumped
 0.3.1 → 0.4.0 to signal the breaking allow-list change.
 - references/examples.md: 22 references in API-call examples.
 - references/troubleshooting.md: 14 references in error-recovery copy.
 
 Skills harnesses that previously approved Bash(secretctl:*) will
 re-prompt because the allow-list is the only safety surface here.
 That's intentional — it gives the user a chance to acknowledge
 the new binary name.')
 
 Show description for daa3d58
 
 [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
 
 committedApr 25, 2026
 
 [daa3d58](https://github.com/getsesame/skills/commit/daa3d583c719e75e13575bf0faa27acd5a6b0fe1)
 
 Copy full SHA for daa3d58
 

### Commits on Apr 24, 2026

- #### [sesame: tighten audit-visible framing for Gen Trust Hub (](https://github.com/getsesame/skills/commit/b649365ecdf143bdba82fc84489aaf491a192e0b 'sesame: tighten audit-visible framing for Gen Trust Hub (#2)
 
 Address the three findings still cited by Gen Agent Trust Hub:
 
 - REMOTE_CODE_EXECUTION: Gen was hallucinating '/install.sh' from bare
 references to getsesame.dev. Remove the domain from install-instruction
 prose (kept a negative Scope line calling out that the skill never runs
 shell-piped downloads).
 - PROMPT_INJECTION: already addressed in 883c87e; explicit Scope section
 now adds redundant framing so the auditor can't miss it.
 - COMMAND_EXECUTION: inherent to the skill. Reframe description and
 capability block to bound the scope to a fixed 'secretctl' subcommand
 vocabulary ('request', 'status', 'hostnames', 'login', 'refresh'), in
 the pattern of find-skills / npx skills which pass SAFE.
 
 Also bumps metadata version 0.3.0 -> 0.3.1 to signal a new scan window.') [#2](https://github.com/getsesame/skills/pull/2) [)](https://github.com/getsesame/skills/commit/b649365ecdf143bdba82fc84489aaf491a192e0b 'sesame: tighten audit-visible framing for Gen Trust Hub (#2)
 
 Address the three findings still cited by Gen Agent Trust Hub:
 
 - REMOTE_CODE_EXECUTION: Gen was hallucinating '/install.sh' from bare
 references to getsesame.dev. Remove the domain from install-instruction
 prose (kept a negative Scope line calling out that the skill never runs
 shell-piped downloads).
 - PROMPT_INJECTION: already addressed in 883c87e; explicit Scope section
 now adds redundant framing so the auditor can't miss it.
 - COMMAND_EXECUTION: inherent to the skill. Reframe description and
 capability block to bound the scope to a fixed 'secretctl' subcommand
 vocabulary ('request', 'status', 'hostnames', 'login', 'refresh'), in
 the pattern of find-skills / npx skills which pass SAFE.
 
 Also bumps metadata version 0.3.0 -> 0.3.1 to signal a new scan window.')
 
 Show description for b649365
 
 [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
 
 authoredApr 24, 2026
 
 [b649365](https://github.com/getsesame/skills/commit/b649365ecdf143bdba82fc84489aaf491a192e0b)
 
 Copy full SHA for b649365
 

### Commits on Apr 23, 2026

- #### [Replace curl-pipe-sh installer; add response-handling guidance](https://github.com/getsesame/skills/commit/883c87e5c2c7ccb349dee63c60d6679d9ccb5e57 'Replace curl-pipe-sh installer; add response-handling guidance
 
 Kills the Gen/Snyk CRITICAL "suspicious download URL" finding by
 removing the curl | sh pattern from the skill and pointing users to
 getsesame.dev for install. Adds a "Handling Responses" section that
 tells the agent to treat upstream API response bodies as untrusted
 data, addressing the PROMPT_INJECTION finding. Softens broker wording
 (user-controlled / self-hostable) for the DATA_EXFILTRATION framing.
 
 Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>')
 
 Show description for 883c87e
 
 ![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)![claude](https://avatars.githubusercontent.com/u/81847?v=4&size=32)
 
 [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 and
 
 [claude](https://github.com/getsesame/skills/commits?author=claude)
 
 committedApr 23, 2026
 
 [883c87e](https://github.com/getsesame/skills/commit/883c87e5c2c7ccb349dee63c60d6679d9ccb5e57)
 
 Copy full SHA for 883c87e
 

### Commits on Mar 29, 2026

- #### [Merge pull request](https://github.com/getsesame/skills/commit/932b0962c5c7091e47706e1b8236bbb141b3d1d4 'Merge pull request #1 from kkumar30/main
 
 Update skill to v0.3.0') [#1](https://github.com/getsesame/skills/pull/1) [from kkumar30/main](https://github.com/getsesame/skills/commit/932b0962c5c7091e47706e1b8236bbb141b3d1d4 'Merge pull request #1 from kkumar30/main
 
 Update skill to v0.3.0')
 
 Show description for 932b096
 
 [![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)](https://github.com/lavanpuri1999) [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 authoredMar 29, 2026
 
 [932b096](https://github.com/getsesame/skills/commit/932b0962c5c7091e47706e1b8236bbb141b3d1d4)
 
 Copy full SHA for 932b096
 
- #### [Update skill to v0.3.0: new installer, login flow, hostnames check](https://github.com/getsesame/skills/commit/5b66bf0f00233f8c3a517b17d22ad497a7aa3fe3 'Update skill to v0.3.0: new installer, login flow, hostnames check')
 
 [![kkumar30](https://avatars.githubusercontent.com/u/12945097?v=4&size=32)](https://github.com/kkumar30) [kkumar30](https://github.com/getsesame/skills/commits?author=kkumar30)
 
 committedMar 29, 2026
 
 [5b66bf0](https://github.com/getsesame/skills/commit/5b66bf0f00233f8c3a517b17d22ad497a7aa3fe3)
 
 Copy full SHA for 5b66bf0
 

### Commits on Mar 27, 2026

- #### [Add README with install instructions and overview](https://github.com/getsesame/skills/commit/9139d66208a6ad6ff3843f817005fe2c7092be63 'Add README with install instructions and overview
 
 Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>')
 
 Show description for 9139d66
 
 ![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)![claude](https://avatars.githubusercontent.com/u/81847?v=4&size=32)
 
 [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 and
 
 [claude](https://github.com/getsesame/skills/commits?author=claude)
 
 committedMar 27, 2026
 
 [9139d66](https://github.com/getsesame/skills/commit/9139d66208a6ad6ff3843f817005fe2c7092be63)
 
 Copy full SHA for 9139d66
 
- #### [Add hostnames check step to skill instructions](https://github.com/getsesame/skills/commit/a46f2f3af5c0132ec1a7fa97a37fdcfd562f20b0 'Add hostnames check step to skill instructions
 
 Agents now check secretctl hostnames --json before making requests,
 and fall back to curl for unconfigured hostnames.
 
 Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>')
 
 Show description for a46f2f3
 
 ![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)![claude](https://avatars.githubusercontent.com/u/81847?v=4&size=32)
 
 [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 and
 
 [claude](https://github.com/getsesame/skills/commits?author=claude)
 
 committedMar 27, 2026
 
 [a46f2f3](https://github.com/getsesame/skills/commit/a46f2f3af5c0132ec1a7fa97a37fdcfd562f20b0)
 
 Copy full SHA for a46f2f3
 
- #### [Add Sesame skill for AI agent secret brokering](https://github.com/getsesame/skills/commit/368b2019dfd586171b04f7c2f2f29c578628c337 'Add Sesame skill for AI agent secret brokering
 
 Teaches AI agents (Claude Code, Codex, Cursor, etc.) to route
 authenticated HTTP requests through secretctl instead of using
 direct curl/httpx with hardcoded credentials.
 
 Install: npx skills add getsesame/skills
 
 Co-Authored-By: Claude Opus 4.6 (1M context) <noreply@anthropic.com>')
 
 Show description for 368b201
 
 ![lavanpuri1999](https://avatars.githubusercontent.com/u/34393448?v=4&size=32)![claude](https://avatars.githubusercontent.com/u/81847?v=4&size=32)
 
 [lavanpuri1999](https://github.com/getsesame/skills/commits?author=lavanpuri1999)
 
 and
 
 [claude](https://github.com/getsesame/skills/commits?author=claude)
 
 committedMar 27, 2026
 
 [368b201](https://github.com/getsesame/skills/commit/368b2019dfd586171b04f7c2f2f29c578628c337)
 
 Copy full SHA for 368b201
---
name: agent-rate-limits
description: Inspect provider-reported AI coding-agent quota and rate-limit state for Codex, Claude Code, and GitHub Copilot. Use for remaining quota, rolling/session limits, weekly limits, reset times, and entitlement checks. Never estimate from tokens or read credentials.
---

# Agent rate limits

Use this project only to report provider-reported quota state. Do not infer limits from token counts, message counts, context-window usage, or elapsed time.

## Run

```bash
bash scripts/rate-limits.sh auto
```

Optional override:

```bash
bash scripts/rate-limits.sh codex
bash scripts/rate-limits.sh claude
bash scripts/rate-limits.sh copilot
bash scripts/rate-limits.sh all
```

## Rules

- Prefer provider-reported values and state the source plus `observed_at`.
- Keep these separate: rolling/session limits, weekly limits, model-specific limits, account/monthly entitlement, and context-window usage.
- If a value is missing, report `unknown` instead of inventing a percentage.
- Label stale values as `fresh`, `stale`, or `expired` and include the age.
- Never print OAuth tokens, API keys, cookies, auth headers, or credential files.
- Do not call undocumented authenticated quota endpoints.

## Output

Return a compact summary like:

```text
Claude Code — provider-reported, observed 4m ago
5h: 42% used, resets 18:00
7d: 67% used, resets Fri 08:00
Model-specific weekly quota: not exposed by the status-line cache
```

If nothing reliable is available:

```text
Copilot — rolling quota unknown programmatically.
Native fallback: run /usage in Copilot CLI.
Account/monthly entitlement is separate and should not be substituted.
```

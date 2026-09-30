# agent-rate-limits

A minimal agent skill for checking provider-reported AI coding-agent quota and rate-limit state without guessing from token usage or reading credentials.

## Purpose

This skill helps answer questions about:

- remaining quota
- rolling or session limits
- weekly limits
- reset times
- account or monthly entitlement
- whether a run is likely to hit a provider throttle

## Included files

- [SKILL.md](SKILL.md) — importable skill definition
- [LICENSE](LICENSE) — project license
- [README.md](README.md) — project summary

## Notes

- Prefer provider-reported values over local estimates.
- Keep entitlement, model quotas, and context-window usage separate.
- Never print credentials or read auth material.

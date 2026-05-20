---
name: reference-claude-routines
description: "Setup details and gotchas for Bart's claude.ai/code remote routines that operate on the wiki repo"
metadata: 
  node_type: memory
  type: reference
  originSessionId: f94b2896-6ab1-42cd-9fa4-4e9e006b35b9
---

Remote scheduled routines at https://claude.ai/code/routines operate on the wiki repo `https://github.com/Bart8405/wiki`.

## Active routines (as of 2026-05-17)

- `trig_01SSBgFTdTQAU3Siu23GwZZE` — "Box for Claude — nightly autonomous processor" (cron `0 0 * * *` = 2AM Amsterdam in CEST)
- `trig_01WpcgJy9haRRXtYLc7KnGk5` — "Box for Claude — 7AM fallback" (cron `0 5 * * *` = 7AM Amsterdam in CEST, checks if 2AM finished, exits cheaply if so)
- `trig_017zwd6JPwMw4Z5qsHrcVDZX` — "extract-highlights-wed-noon" (cron `0 10 * * 3`, scans `==highlights==` and enriches `concepts/_index.md`)
- `trig_016LosKGwG1wYv5yrneRmXiM` — "extract-highlights-wed-fallback" (cron `0 14 * * 3`)

All four are configured with `model: claude-sonnet-4-6`, environment `env_01TPYo4zf7AhU6M5PEEZdJYX`, and tools `[Bash, Read, Write, Edit, Glob, Grep, WebFetch, WebSearch]`.

## GitHub auth gotcha

The Claude GitHub App must be **INSTALLED** on the wiki repo (not just authorized) with **read & write access to Contents**. Just authorizing the OAuth app gives read-only access — the agent can clone but not push.

Verify install at: https://github.com/settings/installations → "Configure" the Claude app → ensure `Bart8405/wiki` is selected and "Contents" is set to "Read and write".

If a routine fails with "GitHub repository access check failed — re-authorize GitHub in settings", the install is missing or has the wrong permissions.

**Why:** flipping the repo between public/private can disable routines. When that happens, re-enabling via the UI sometimes strips the `sources` field from `session_context` — restore it via the API update endpoint. See [[reference_wiki]] for the repo location.

## Sandbox network limits

The remote agent sandbox often blocks binary file downloads (PDFs). Strategy: agent tries `curl` with `-L --max-time 60 -A 'Mozilla/5.0'`, verifies the result is a real PDF with `file`, and falls back to flagging `⚠️ manual download needed` in source catalogs when blocked. Realistic success rate is 30-60% on openly-accessible sources (arXiv, WB, ADB, government PDFs).

## Cron timezones

All cron expressions are in UTC. Current schedule assumes CEST (UTC+2). When DST ends (last Sunday of October), Amsterdam becomes CET (UTC+1) and all routines fire 1 hour earlier in local time. Update cron expressions then if it matters.

Manage at: https://claude.ai/code/routines

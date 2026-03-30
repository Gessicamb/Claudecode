---
step: 4
name: publish
title: "Publish to Instagram"
agent: publisher
execution: inline
model_tier: fast
checkpoint: true
---

# Step 04 — Publish to Instagram

## Goal
Publish the approved carousel to Instagram using the instagram-publisher skill.

## Pre-conditions
- User approved content in Step 03
- `.env` file exists with `INSTAGRAM_ACCESS_TOKEN`, `INSTAGRAM_USER_ID`, `IMGBB_API_KEY`
- JPEG images are in `squads/instagram/output/images/`

## Process
Delegate to the Publisher agent (`squads/instagram/agents/publisher.agent.md`).

The publisher will:
1. Check images directory
2. Validate caption constraints
3. Present final preview and ask for confirmation
4. Execute publish script (or dry-run)
5. Report permalink on success

## Output
- Post permalink saved to `squads/instagram/pipeline/data/publish-result.md`
- Run logged in `squads/instagram/_memory/runs.md`

## Done When
- Post published successfully with permalink returned
- OR dry-run completed successfully
- OR user cancelled

## Setup Reminder
If `.env` is not configured, remind user:
```
⚠️  Instagram credentials not found.
Copy .env.example to .env and add:
  INSTAGRAM_ACCESS_TOKEN=...
  INSTAGRAM_USER_ID=...
  IMGBB_API_KEY=...

See skills/instagram-publisher/SKILL.md for setup instructions.
```

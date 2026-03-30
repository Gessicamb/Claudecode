---
step: 2
name: write
title: "Write Content"
agent: copywriter
execution: subagent
model_tier: powerful
checkpoint: false
format: instagram-feed
---

# Step 02 — Write Content

## Goal
Transform the research brief into a complete Instagram carousel (8-10 slides) and caption.

## Input
- `squads/instagram/pipeline/data/research-output.md` (from Step 01)
- `_opensquad/_memory/company.md` (brand voice)
- Tone choice from user (copywriter will ask)

## Process
Delegate to the Copywriter agent (`squads/instagram/agents/copywriter.agent.md`).

The copywriter will:
1. Present tone options and wait for user selection
2. Write all carousel slides (8-10 slides, 40-80 words each)
3. Write the full caption with hashtags and CTA
4. Save to `squads/instagram/pipeline/data/content-draft.md`

## Output
File: `squads/instagram/pipeline/data/content-draft.md`

## Done When
- content-draft.md exists with all slides written
- Caption is within 2200 character limit
- 8-15 hashtags included
- CTA present on final slide and in caption

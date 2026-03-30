---
step: 3
name: review
title: "Review & Approve Content"
agent: copywriter
execution: inline
model_tier: fast
checkpoint: true
---

# Step 03 — Review & Approve Content

## Goal
Present the complete content draft to the user for review and approval before publishing.

## Process

1. Display the full content draft from `squads/instagram/pipeline/data/content-draft.md`

2. Present slide-by-slide summary:
   ```
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   📋 Content Review — Instagram Post
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   Topic: {topic}
   Slides: {N} | Caption: {chars}/2200 | Hashtags: {N}

   SLIDE 1 (Hook): {headline}
   SLIDE 2: {headline}
   [...]
   SLIDE {N} (CTA): {headline}
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   ```

3. Ask user:
   - **Approve** → proceed to publishing
   - **Edit** → ask what to change, update content-draft.md, re-display
   - **Cancel** → stop pipeline

## Checkpoint
This is a mandatory checkpoint. Do NOT proceed to Step 04 without explicit user approval.

## Done When
User confirms approval to proceed to publishing.

---
step: 1
name: research
title: "Research Topic"
agent: researcher
execution: subagent
model_tier: powerful
checkpoint: false
---

# Step 01 — Research Topic

## Goal
Research the post topic thoroughly and compile a brief with trends, facts, content angles, and hashtag recommendations.

## Input
- Ask user: "What topic should this Instagram post be about?"
- Optionally ask: "Do you have a specific angle or goal for this post?"

## Process
Delegate to the Researcher agent (`squads/instagram/agents/researcher.agent.md`).

The researcher will:
1. Search for current trends and viral content on the topic
2. Extract key facts, statistics, and angles
3. Compile hashtag recommendations
4. Write output to `squads/instagram/pipeline/data/research-output.md`

## Output
File: `squads/instagram/pipeline/data/research-output.md`

## Done When
- research-output.md exists and contains facts, angles, and hashtags
- At least 3 content angles identified
- At least 8 hashtag recommendations

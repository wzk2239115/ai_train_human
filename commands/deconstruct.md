---
description: Break down complex problems into first principles
argument-hint: <complex-problem> [granularity]
allowed-tools: [WebSearch, Read]
model: sonnet
---

# /deconstruct

Cut through complexity. See the structure underneath.

## Usage

```
/deconstruct <problem> [detail-level]
```

**Examples:**
- `/deconstruct "how to scale a web app to 1M users"`
- `/deconstruct "why did this startup fail"`
- `/deconstruct "should I quit my job" high-detail`

**Detail levels:**
- `overview` - Key components only
- `standard` (default) - Main factors + interactions
- `exhaustive` - Every relevant variable

## What This Command Does

Unlike "break down this problem," this command:

1. **Identifies core variables** - What actually matters
2. **Maps relationships** - How variables interact
3. **Finds leverage points** - Where to intervene
4. **Surface assumptions** - What are you taking for granted
5. **Suggests experiments** - How to test your understanding

## Output Format

```
## Core Variables
[The 3-7 key factors]

## Variable Map
[How they relate (causal, correlated, independent)]

## Leverage Points
[Where small changes have big effects]

## Hidden Assumptions
[What you're assuming without realizing]

## Next Actions
[What to do first]
```

## Philosophy

> "Give me a lever long enough and I shall move the world."

Most people are pushing at the wrong place. Find the lever.

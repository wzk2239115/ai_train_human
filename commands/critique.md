---
name: critique
description: Ruthlessly critique your work and find blind spots
argument-hint: <your-work-url-or-description> [focus-area]
allowed-tools: [Read, Glob, Grep, WebSearch]
model: sonnet
---

# /critique

Make AI your toughest critic. Find what you're missing.

## Usage

```
/critique <file> [focus]
/critique "<paste your content>" [focus]
/critique https://example.com [focus]
```

**Focus areas:**
- `logic` - Fallacies, weak reasoning, missing angles
- `clarity` - Confusion points, jargon, structure
- `completeness` - What's missing, edge cases
- `users` - UX, accessibility, user perspective
- `business` - Assumptions, viability, competition
- (no focus) - General critique across all dimensions

## What This Command Does

AI will:

1. **Attack from multiple angles** - Logic, user experience, business viability
2. **Find your blind spots** - Things you're too close to see
3. **Ask hard questions** - Challenge your assumptions
4. **Suggest improvements** - Not just problems, but solutions

## Output Format

```
## Strengths
[What works well - don't throw away]

## Critical Issues
[Must-fix problems]

## Blind Spots
[Things you didn't consider]

## Hard Questions
[Challenge your assumptions]

## Next Steps
[Actionable improvements]
```

## Philosophy

> "Your best teacher is your last mistake."

If everyone agrees with your idea, you're not asking the right people.

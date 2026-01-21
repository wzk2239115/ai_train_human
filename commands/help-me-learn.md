---
description: Help you learn a concept deeply, not just give an answer
argument-hint: <topic> [depth-level]
allowed-tools: [Read, Glob, Grep]
model: sonnet
---

# /help-me-learn

Make AI your learning partner, not your answer generator.

## Usage

```
/help-me-learn <topic> [depth]
```

**Examples:**
- `/help-me-learn recursion` - Learn recursion fundamentals
- `/help-me-learn "react hooks" deep` - Deep dive with context and trade-offs
- `/help-me-learn "first-principles thinking"` - Learn mental models

## What This Command Does

Unlike asking "explain X", this command makes AI help you:

1. **Diagnose your level** - Ask what you already know
2. **Build from first principles** - Start with fundamentals, not rote answers
3. **Show multiple perspectives** - Compare approaches, trade-offs
4. **Test understanding** - Ask you questions to verify learning
5. **Connect to your knowledge** - Link to what you already understand

## Depth Levels

- **basic** (default): Core concepts, simple examples
- **intermediate**: Underlying mechanics, when to use/avoid
- **deep**: First principles, history, alternatives, edge cases

## Output Format

```
## 1. What You Already Know
[Assessment]

## 2. First Principles
[Core fundamentals]

## 3. Mental Model
[How to think about this topic]

## 4. Common Pitfalls
[What beginners get wrong]

## 5. Practice Questions
[Test your understanding]
```

## Philosophy

> "Don't just get the answer. Learn how to think about the problem."

This command is inspired by Gemini's "help me learn" feature. It's not about quick answers—it's about building permanent understanding.

# Balls Mode

> Credit: Based on the original concept by [@typememetics](https://x.com/typememetics/status/2012821469009465487)

Decomposed reasoning with explicit confidence scoring for AI coding assistants.

## What is this?

Standard prompting gives you an answer. Balls Mode gives you:
- Multiple reasoning paths
- Explicit uncertainty
- Clear points of failure

## Installation

### Claude Code

```bash
/plugin marketplace add gbasin/balls-mode
/plugin install balls-mode
```

### Codex

Copy the skill file to your Codex skills directory:

```bash
mkdir -p ~/.codex/skills/balls-mode
cp plugins/balls-mode/skills/balls/SKILL.md ~/.codex/skills/balls-mode/
```

### Manual

Copy `plugins/balls-mode/skills/balls/SKILL.md` to your tool's skills directory.

## Usage

```
/balls Should I rewrite this service in Go?
```

## The Protocol

1. **CLASSIFY** - Is this trivial or complex?
2. **DECOMPOSE** - Break into verifiable units (balls)
3. **SOLVE & VERIFY** - Answer each independently
4. **SCORE** - Assign confidence (0.0-1.0)
5. **SYNTHESIZE** - Combine with uncertainty tracking

## Example Output

```
## Decomposition

| # | Ball | Why it matters |
|---|------|----------------|
| 1 | What's the current pain point? | Determines if rewrite addresses real issue |
| 2 | Team's Go experience? | Affects timeline and quality |
| 3 | Service complexity? | Rewrite effort estimation |

## Analysis

| Ball | Answer | Confidence | Notes |
|------|--------|------------|-------|
| Current pain point | Memory usage in Python | 0.7 | Based on user context |
| Team Go experience | Unknown | 0.2 | Need to ask |
| Service complexity | ~5k LOC, moderate | 0.8 | Reviewed codebase |

## Synthesis

**Answer**: Possibly worth it if the team has Go experience. Memory improvements would be significant.

**Overall Confidence**: 0.45

**Weakest Link**: Team experience unknown - this determines feasibility.

**To increase confidence**: Clarify team's Go background.
```

## When to Use

- Architectural decisions
- Debugging complex issues
- Code review concerns
- Technology choices
- Any question where you want to see the reasoning, not just the answer

## When NOT to Use

- "What's 2 + 2?"
- "How do I install npm?"
- Simple factual questions

## Confidence Score Guide

| Score | Meaning |
|-------|---------|
| 0.9-1.0 | Verifiable fact or logical certainty |
| 0.7-0.89 | Strong evidence, established patterns |
| 0.5-0.69 | Reasonable inference, some uncertainty |
| 0.3-0.49 | Educated guess, significant unknowns |
| 0.0-0.29 | Speculation, insufficient information |

## Philosophy

> "What if a system could check its own work from multiple angles before giving you an answer? Not just 'think step by step.' Actually decompose. Actually verify. Actually flag uncertainty."

## License

MIT

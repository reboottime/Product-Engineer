# Why I Need a Personal CLAUDE.md

## The Problems I Had

### 1. AI Misunderstood My English

As a non-native English speaker, my messages sometimes have typos or unconventional phrasing. Without context, AI would:

- Misinterpret what I meant
- Over-correct or ask unnecessary clarifications
- Miss the actual intent behind my words

### 2. AI Did Too Much

When I asked for something small, AI would:

- Add features I didn't request
- Refactor surrounding code "while it was there"
- Create extra files, documentation, tests I didn't need
- "Improve" things that were working fine

I wanted minimal changes. AI defaulted to comprehensive changes.

### 3. AI Made Things Up

When AI didn't know something, it would:

- Guess instead of researching
- Present uncertain information as fact
- Fabricate plausible-sounding but wrong answers

This wasted time debugging AI's confident mistakes.

## What Fixed It

A personal config file at `~/.claude/CLAUDE.md`:

```markdown
# Personal Context

## Communication Context

- Human is Chinese, English may have typos
- Default to minimal scope: When uncertain, do LESS not more

## Accuracy & Research

Never fabricate information. If confidence < 90%, research first.
- **Don't know**: Use WebSearch, read docs, investigate codebase
- **Never**: Guess, assume, or present uncertainty as fact
```

Now AI understands my communication style, does less by default, and researches instead of guessing.

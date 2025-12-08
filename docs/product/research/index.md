# Product Research - Structure Guide

## Folder Purpose

**`/interviews/`** - Raw customer interview notes
- One file per interview
- Format: `YYYY-MM-DD-[name-role].md`
- See `_example.md` for template

**`/insights/`** - Synthesized learnings across multiple sources
- Cross-interview themes and patterns
- Validated/invalidated assumptions
- Format: `[topic-area].md`
- See `_example.md` for template

**`/validated/`** - Confirmed insights ready for handoff
- High-confidence learnings only
- Evidence-backed decisions
- Created during phase transitions

**`/learnings/`** - General observations and notes
- Exploratory research
- Market insights
- Competitive analysis notes

## Workflow

1. **Interview** → Save raw notes to `/interviews/`
2. **Pattern emerges** (3+ interviews) → Create insight doc in `/insights/`
3. **Insight validated** (evidence + confidence) → Reference in requirements
4. **Phase transition** → Move to `/validated/` for handoff

## Tips for Founding PM

- Write interviews immediately (memory fades fast)
- Look for patterns across 3+ interviews before creating insights
- Direct quotes > summaries (capture exact words)
- Tag everything (segments, problems, confidence levels)
- Kill insights that don't validate (move to archive, note why)

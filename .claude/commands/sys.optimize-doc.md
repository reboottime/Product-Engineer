---
description: Optimize documentation for LLM consumption (reduce tokens, increase signal)
argument-hint: [file-path]
---

## Workflow

1. Read file at $ARGUMENTS
2. Read framework at `docs/technical/doc-preference.md`
3. Audit → Apply framework → Output optimized version

## Audit Output Template

```sh
File: [name]
Current: [X] lines ([Y%] generic, [Z%] project-specific)
Target: ~[N] lines ([R%] reduction)
```

## Optimized Output Template

```sh
BEFORE: [X] lines ([Y%] generic)
AFTER: [N] lines ([Z%] generic)
Reduction: [R%]
Signal-to-noise: [before] → [after]
```

## User Choice

After showing optimized version, ask:

1. Overwrite original
2. Save to new file
3. Review changes first

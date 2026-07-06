# Etapa Product Brain

LLM-maintained knowledge base for the Etapa product team. Maintained
automatically by Rezonant's Product Brain.

> **All brain work happens on this `brain` branch.** The repo's default branch
> (`main`) holds only a placeholder. `brain` is intentionally not the default so
> the brain can be written directly without bumping into org-level rulesets that
> protect the default branch.

## Layout philosophy

The synthesized knowledge layer lives under `wiki/` and can be opened as a
self-contained Obsidian vault. Raw inputs, archived sources, and operational
files sit outside the vault at the repo root.

## Layout

```
README.md                # this file — repo-level orientation
wiki/                    # the Obsidian vault — synthesized knowledge layer
  index.md               # auto-generated index; regenerated each run
  Charter.md             # hand-authored orientation
  Principles.md          # hand-authored product principles
  articles/              # synthesized articles by topic
  technical_context/     # code-derived technical reference docs
sources/                 # archived inputs that have been incorporated
inputs/                  # active queue (cleared by the processor each run)
```

## What you can (and cannot) edit

### Edit freely

- `wiki/Charter.md` — foundational product orientation
- `wiki/Principles.md` — durable product principles
- Anything in `inputs/manual/` — drop files here; they will be processed

### Do NOT edit by hand

- `wiki/index.md` — auto-generated; regenerated every processing run
- Any synthesized article under a `wiki/` subdirectory
- Anything in `sources/` — archived inputs, treat as read-only history

---
name: onboard-repo
description: Use at the start of work in an unfamiliar repository — produces a fast, accurate mental model (stack, architecture, entry points, conventions, risks) before any code changes.
---

# Onboard a repository

Goal: in one pass, understand a repo well enough to make safe changes — without reading every file.

## Steps

1. **Shape.** Read `README*`, `CLAUDE.md`/`AGENTS.md`, `package.json`/`pyproject.toml`/`go.mod`, and any `/docs`. Note stack, scripts, and stated conventions.
2. **Entry points.** Find where execution starts (`main`, `server.*`, `index.*`, CLI bin, route registration). Trace one request/command end to end.
3. **Map layers.** Identify the boundaries: entry → routing/handlers → business logic → storage/external. Write them down as a 5-line map.
4. **Conventions.** Skim 3–4 representative source files. Capture naming, error handling, test style, and module organization — match these later.
5. **Risks.** Note the fragile/critical paths (payments, auth, data writes, deploys) and anything marked TODO/FIXME/HACK.
6. **Verify how.** Find the test/build/lint commands and which one is the *smallest relevant gate* for a typical change.

## Output

Produce a short brief:

```
STACK: ...
RUN/TEST/BUILD: ...
ARCHITECTURE (5 lines): ...
CONVENTIONS: ...
DO-NOT-TOUCH / ASK-FIRST: ...
SMALLEST GATE: ...
```

Stop here. Do not change code during onboarding — the brief is the deliverable.

# Ballgame

**Public name:** **Ballgame** (full: **Agent Office Ballgame**)  
**By:** [Quik Nation](https://quiknation.com) / [Imagination Everywhere](https://github.com/imaginationeverywhere)  
**Locked:** 2026-09-22 (Mo)

> The end-to-end contract for moving an AI Agent Office from chat into paid, scoped work — so other AI engineers can adopt the same loop and cite Quik Nation.

```text
Chat
  → grill-me          (gather until shared understanding)
  → estimate          (ready only when gather is done)
  → spend gate        (monthly usage OR wallet ≥ estimate)
  → user APPROVES
  → mode work         (plan → build → deliverable)
  → money close       (usage burn and/or Stripe test/live charge)
```

That full path is the win condition. Chat-only, plan-only, or “fail-closed money forever” is not Ballgame.

## Why it exists

Most agent UIs jump from chat straight into plans or dollars. Ballgame forces:

1. **Shared understanding first** (grill-me) before any estimate.
2. **Explicit estimate approval** before plan / build / generate.
3. **Spend coverage** — monthly usage allotment **or** wallet balance — before Start.
4. **Real deliverable + money close** on the develop path (test-mode Stripe when wallet/top-up is needed).

## Seat formulas

| Seat | After grill-me + approved estimate |
|------|-------------------------------------|
| **PO** | plan · research · generate · build (PO-first) |
| **FE / BE** | **build only** (tasks usually from PO plan handoff) |

## Spec

Canonical public specification: [`SPEC.md`](./SPEC.md)

Internal platform standard (private herus): Auset Platform → `AGENT_OFFICE_GRILL_ME_ESTIMATE_MODE_STANDARD.md`

## Cite us

If you implement Ballgame (or a compatible loop), please cite:

```text
Quik Nation (2026). Ballgame — Agent Office Grill → Estimate → Mode.
https://github.com/imaginationeverywhere/agent-office-ballgame
```

Or use [`CITATION.cff`](./CITATION.cff) / GitHub’s “Cite this repository”.

## Prior art

The gather phase uses **grill-me** ([aihero.dev/skills-grill-me](https://www.aihero.dev/skills-grill-me)) — one question at a time, recommend an answer, explore the codebase before asking. Ballgame wraps grill-me into estimate, spend gate, seat formulas, deliverable, and money close.

## License

Apache-2.0 — see [`LICENSE`](./LICENSE). Copyright © 2026 Imagination Everywhere / Quik Nation.

## Maintainers

Quik Nation council (product lock). Issues and PRs welcome for clarifications that keep the hard order intact.

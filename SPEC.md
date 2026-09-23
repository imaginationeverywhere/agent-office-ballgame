# Ballgame — Specification

**Status:** Public canonical · **Name lock:** 2026-09-22  
**Owner:** Quik Nation / Imagination Everywhere  
**Repo:** https://github.com/imaginationeverywhere/agent-office-ballgame

## 0. Name

| Form | Use |
|------|-----|
| **Ballgame** | Short / public brand |
| **Agent Office Ballgame** | Formal title |
| Tagline | Chat → grill-me → estimate → spend gate → mode → deliverable → money close |

Do not invent a parallel estimate/plan flow under another name when adopting this contract.

## 1. Hard order (non-negotiable)

```text
Chat
  → mode_suggestion (no auto-switch; user confirms mode intent)
  → grill-me (gather until shared understanding)
  → estimate (readyForApproval=true only when gather is done)
  → spend gate: monthly usage available OR wallet ≥ estimate
  → user APPROVES estimate
  → mode work (plan → FE/BE build → deliverable → money close)
```

| Forbidden | Required |
|-----------|----------|
| Estimate while still clarifying / gathering | Withhold estimate until grill-me resolves |
| Plan / research / generate / build before estimate approval | Execute only after approve |
| Auto-switch mode without confirmation | Mode suggestion + confirm |
| Chat mode emitting a dollar estimate | Chat = not applicable for estimate |
| Start paid work with no usage and empty wallet | Monthly usage remaining **or** wallet ≥ estimate |

### grill-me (gather)

[grill-me](https://www.aihero.dev/skills-grill-me): one question at a time, recommend an answer, explore the codebase before asking, stop when the decision tree is resolved. Do **not** write a plan, file list, or tasks until the user confirms shared understanding.

## 2. Spend gate — usage OR wallet

Before estimate **Start** / approval can begin paid mode work, the user must have **either**:

1. **Usage available** — included **monthly** usage allotment remaining, **or**
2. **Enough money in their wallet** — prepaid balance covering the estimate / projected spend

| Rule | Detail |
|------|--------|
| Monthly usage | Users **get usage each month** (allotment resets on the billing cycle) |
| Gate | `usage_remaining ≥ estimate` **OR** `wallet_balance ≥ estimate` |
| Fail-closed | If neither — **block Start**; offer top-up / wait for next period — never silent charge |
| Preference | Burn included usage first when available; else wallet / card top-up |

## 3. Seat formulas

### 3.1 PO agent — wire and use first

After grill-me + approved estimate:

| Formula | After approve |
|---------|----------------|
| chat = grill-me + estimate + plan | Numbered plan; PO may use a subagent to author the plan |
| chat = grill-me + estimate + research | Research ladder |
| chat = grill-me + estimate + generate | Artifact (doc / image / video) |
| chat = grill-me + estimate + build | Build when PO owns build |

After **plan**: PO assigns FE + BE tasks; those seats execute.

### 3.2 FE and BE agents — after PO path

```text
chat → grill-me → estimate(approve) → build
```

FE/BE do **not** lead with plan / research / generate as their default mode set.

## 4. Acceptance bar (the whole Ballgame)

A reference environment (e.g. develop) must demonstrate:

1. Chat → grill-me → estimate (withheld until ready) → approve  
2. Spend gate enforced (usage **or** wallet)  
3. Mode work produces a **real deliverable** (not a chat summary)  
4. Money close when needed (usage burn and/or visible Stripe test-mode charge on develop)

Missing any step → add the feature, then re-walk. Soft-passing money/usage rows is not Ballgame.

## 5. Implementation notes (portable)

Adopters should implement equivalent semantics:

| Concept | Intent |
|---------|--------|
| Withhold until gather done | No client-facing estimate body until grill-me resolves |
| Ready for approval | Explicit flag / receipt before Start/Cancel UI |
| Estimate accepted gate | Executor runs mode work only after approve |
| Spend gate | Server-side check: usage OR wallet before Start succeeds |

Reference forge inside Quik Nation platforms uses Agent Office router contracts and estimate receipts; public adopters may map these to their own host.

## 6. Citation

```
Quik Nation (2026). Ballgame — Agent Office Grill → Estimate → Mode.
https://github.com/imaginationeverywhere/agent-office-ballgame
```

See `CITATION.cff`.

# PROJECT_FOUNDATION.md — [Project Name]
<!--
SCOPE: Vision, purpose, stack, roadmap, roles, key decisions, design system, doc registry.
       This is the ONE-PAGER+ that answers "what are we building and why?"
NOT HERE: Implementation specs → specs/[module]/spec.md
NOT HERE: Database schemas → DATA_MODEL.md
NOT HERE: API details → INTEGRATIONS.md
NOT HERE: Rules/constraints → CONSTITUTION.md
NOT HERE: Failures/fixes → LESSONS_LEARNED.md

TARGET LENGTH: 3-5 pages max. If it's longer, you're putting spec-level detail here.
-->

**Last updated:** YYYY-MM-DD

---

## 1. What This Is

<!-- 2-3 sentences max. If you can't explain it concisely, you don't understand it yet. -->


## 2. What Problem It Solves

<!-- Be specific. Not "improve communication" but "there is no tool that does X for Y people." -->


## 3. What This Is NOT (Anti-Goals)

<!-- Explicit exclusions prevent scope creep. List 3-5 things you will NOT build/become. -->

1. **NOT a [thing]** — because [reason]
2. **NOT a [thing]** — because [reason]
3. **NOT a [thing]** — because [reason]

## 4. Who It's For

<!-- Primary users/personas. Keep brief — detailed personas go in marketing docs, not here. -->

| Role | Who they are | What they need from this product |
|------|-------------|--------------------------------|
| | | |

## 5. Competitive Differentiators

<!-- 3-5 things that make this different from alternatives. Be honest — if it's not different, say so. -->

1. **[Differentiator]**: [why it matters]
2. **[Differentiator]**: [why it matters]

---

## 6. Tech Stack

| Layer | Technology | Why this one |
|-------|-----------|-------------|
| Frontend | | |
| Backend | | |
| Database | | |
| AI/ML | | |
| Auth | | |
| State Management | | |
| Hosting/Deploy | | |
| CI/CD | | |

## 7. Key Decisions

<!-- Decisions that affect the ENTIRE project. Module-specific decisions go in module specs. -->

| Decision | Choice | Date | Why | Alternatives Rejected |
|----------|--------|------|-----|----------------------|
| | | | | |

---

## 8. Module Roadmap

### MVP (Build NOW)

| # | Module/Workflow | Type | Purpose | Status | Depends On |
|---|----------------|------|---------|--------|------------|
| 1 | | app / workflow | | ⬜🟡✅ | — |
| 2 | | app / workflow | | ⬜🟡✅ | #1 |
| 3 | | app / workflow | | ⬜🟡✅ | #1, #2 |

### Post-MVP (ONE LINE each — spec when ready to build)

| Phase | Module | One-line purpose | Priority |
|-------|--------|-----------------|----------|
| 2 | | | |
| 3 | | | |
| 4 | | | |

---

## 9. Roles & Permissions Summary

<!-- Only if your product has multiple user roles. -->

| Role | Can do | Cannot do |
|------|--------|-----------|
| | | |

## 10. Design System Summary

<!-- Keep minimal. Only what's needed for visual consistency. -->

### Colors
| Role | Hex | Usage |
|------|-----|-------|
| Primary | | |
| Secondary | | |
| Background | | |
| Text | | |

### Typography
- **Headings:** [font]
- **Body:** [font]

### UI Principles (3-5 max)
- [Principle]
- [Principle]

---

## 11. Monetization Model

<!-- Even if free now. How will it make money? -->

| Tier | Price | What's included | Target user |
|------|-------|----------------|-------------|
| Free | $0 | | |
| Paid | $X/mo | | |

---

## 12. Cross-Cutting Concerns

<!-- Things that apply to EVERY module/workflow. Keep to one line each. -->

- **i18n:** [languages, approach]
- **Security:** [auth approach, data access philosophy]
- **Cost control:** [budget, monitoring approach]
- **Testing:** [strategy — unit/integration/manual]
- **Error handling:** [standard approach]
- **Observability:** [what you monitor, how you know it works]

---

## 13. Document Registry

<!-- CANONICAL INDEX. If a doc is not here, it doesn't exist for this project. -->

| Document | Purpose | Location | Last Updated |
|----------|---------|----------|-------------|
| PROJECT_FOUNDATION | This file — vision, stack, roadmap | docs/ | |
| CONSTITUTION | Immutable rules + AI agent rules | ./ | |
| DATA_MODEL | Database schemas | docs/ | |
| INTEGRATIONS | External APIs | docs/ | |
| LESSONS_LEARNED | Failures + fixes | docs/ | |
| spec: [module] | Module spec | specs/[name]/ | |

### Anti-Duplication Rules
1. **Reference, never copy.** Use "See [DOC.md §section]" format.
2. **One concept, one location.** If two docs cover the same topic, merge and delete one.
3. **Check registry before creating.** If a doc for this topic exists, update it.
4. **No code in docs.** Code lives in src/. Docs describe intent.
5. **No API keys in docs.** Keys live in .env only.

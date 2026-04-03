# LESSONS_LEARNED.md — [Project Name]
<!--
SCOPE: ALL failures, fixes, anti-patterns, and operational incidents.
       Single canonical source. No other file contains lessons.
NOT HERE: Project vision → PROJECT_FOUNDATION.md
NOT HERE: Implementation details → specs/

UPDATE FREQUENCY: Continuously. Every significant issue gets logged.
NAMESPACE: LL-[CATEGORY]-[XXX] (3-digit, zero-padded)

CATEGORIES:
  PLAN  — Planning failures (wrong scope, missing requirements)
  ARCH  — Architecture decisions that were wrong
  CODE  — Code-level bugs and patterns
  COST  — Cost surprises and budget issues
  INFRA — Infrastructure, WSL, networking, deployment
  AI    — AI/LLM behavior, prompts, model issues
  DATA  — Database, schema, migration issues
  SEC   — Security and auth issues
  OPS   — Operational incidents and recovery
  PROC  — Process failures (workflow, git, docs)

TRIGGER POLICY (when to write a lesson):
  - Any bug that took >1 hour to fix
  - Any task that had to be redone
  - Any cost surprise (actual > 2x estimated)
  - Any architectural assumption that proved wrong
  - Any AI/model behavior that was unexpected
  - Any incident that affected users/production
-->

**Last updated:** YYYY-MM-DD
**Total entries:** [X]

---

## Lessons

### LL-PLAN-001: [Short title]
- **Date:** YYYY-MM-DD
- **Severity:** 🔴 Critical / 🟡 Moderate / 🟢 Minor
- **Problem:** [What went wrong — specific]
- **Evidence:** [How you know — logs, cost, time lost, error message]
- **Root Cause:** [Why it happened]
- **Fix:** [What you did to resolve it]
- **Prevention Rule:** [One sentence — what to do differently. This is the "lesson."]
- **Enforced by:** [Script, validator, test, or process that prevents recurrence. "Manual discipline" is NOT enforcement.]
- **Time/Cost Lost:** [e.g., "~4 hours + $12 in API calls"]
- **Applies to:** [apps / workflows / both]
- **Verified:** ⬜ Not yet / ✅ YYYY-MM-DD [enforcement confirmed working]

---

### LL-[CAT]-[XXX]: [Short title]
<!-- Copy this block for each new lesson -->
- **Date:**
- **Severity:** 🔴 / 🟡 / 🟢
- **Problem:**
- **Evidence:**
- **Root Cause:**
- **Fix:**
- **Prevention Rule:**
- **Enforced by:**
- **Time/Cost Lost:**
- **Applies to:** apps / workflows / both
- **Verified:** ⬜ / ✅

---

## Anti-Patterns

<!-- Collected from all lessons. "Never do these" — fast reference. -->

### Content & Quality
- Never accept stub/placeholder data in outputs — validate all fields have real content
- Never accept generic descriptions ("Reveals something about X") — require specifics

### Operations
- Never retry with identical parameters — always include failure diagnosis
- Never batch-run untested changes — test ONE item end-to-end first

### Architecture
- Never let different phases use different naming for the same entity — normalize IDs
- Never split a spec across multiple files if one consumer needs all of it — self-contained per consumer

### Cost
- Never start work without a budget alarm set
- Never assume orchestrator overhead is zero — track it separately

### Documentation
- Never copy content between docs — reference with "See [DOC §section]"
- Never start an AI chat by re-explaining the project — load existing docs

<!-- Add anti-patterns as you discover them. Each should trace to a LL-XXX entry. -->

---

## Pre-Flight Checklist (Master)

<!-- Run this before starting ANY new module or workflow build.
     Reference specific lessons that justify each check. -->

### Planning
- [ ] Spec complete and approved (See README.md §Process)
- [ ] Data flow clear: every input has a source, every output has a consumer (LL-PLAN-001)
- [ ] Budget set with monitoring plan (LL-COST-XXX)
- [ ] V1 scope defined — ugliest functional version (LL-PLAN-XXX)
- [ ] Edge cases / failure modes documented (spec §7)

### Architecture
- [ ] Schemas defined for all new data (spec §4)
- [ ] Integration points identified (INTEGRATIONS.md)
- [ ] Model selection documented with fallbacks (if AI) (spec §4)
- [ ] Cost tracking built into every script from day 1 (LL-COST-XXX)

### Development
- [ ] Single-item end-to-end test planned BEFORE batch (LL-PLAN-XXX)
- [ ] File I/O verified for all agents/scripts (LL-ARCH-XXX)
- [ ] Deterministic tasks use scripts, not LLMs (LL-ARCH-XXX)
- [ ] Structural validators run before quality checks (LL-ARCH-XXX)

---

## Escalation Chains

<!-- Reusable recovery patterns discovered from incidents. -->

### Pattern: Large AI Output Failure
```
1. Monolithic generation fails → split by domain/section
2. Domain-split fails → identify failing block, retry only that block
3. Per-block still fails → compact mode (schema + required only)
4. JSON parse failure → auto-repair before declaring failure
5. Auto-retry up to 2 times before surfacing to human
RULE: Always save raw output on failure before retrying
```

### Pattern: [Name]
```
1. [Step]
2. [Step]
RULE: [Key rule]
```

---

## Model Notes

<!-- AI/LLM-specific behaviors worth remembering. Only for projects using AI. -->

| Model | Note | Source |
|-------|------|--------|
| | | LL-AI-XXX |

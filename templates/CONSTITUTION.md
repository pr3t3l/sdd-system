# CONSTITUTION.md — [Project Name]
<!--
SCOPE: Immutable rules, constraints, forbidden patterns, product principles.
       These apply to EVERY module, workflow, and AI agent in the project.
NOT HERE: Project vision/roadmap → PROJECT_FOUNDATION.md
NOT HERE: Module-specific decisions → specs/[module]/spec.md
NOT HERE: Database schemas → DATA_MODEL.md

UPDATE FREQUENCY: Rarely. Only when a fundamental constraint changes.
-->

**Last updated:** YYYY-MM-DD

---

## 1. Product Principles

<!-- 3-7 rules that define HOW this product behaves. Not features — principles.
     E.g., "Transparency: every score is explainable" or "Privacy: AI never reveals data sources" -->

1. **[Principle name]:** [What it means in practice]
2. **[Principle name]:** [What it means in practice]
3. **[Principle name]:** [What it means in practice]

---

## 2. Environment & Infrastructure

### Runtime
<!-- Hardware, OS, paths, usernames — the physical reality. -->

| Item | Value |
|------|-------|
| OS | |
| Username | |
| Home directory | |
| Project root | |

### Services
<!-- What runs, on what port, how it starts. -->

| Service | Port | Start command | Health check |
|---------|------|--------------|-------------|
| | | | |

### Networking & API Routing
<!-- Proxy, API routing, auth patterns. -->

- **API proxy:** [e.g., LiteLLM at :4000, or direct calls]
- **API keys location:** [e.g., .env file path — NEVER in docs]

---

## 3. Architecture Rules

<!-- Rules that affect how ALL modules/workflows are built. -->

1. **[Rule]:** [Why]
2. **[Rule]:** [Why]
3. **[Rule]:** [Why]

---

## 4. Code Standards

### [Primary Language]
<!-- E.g., Python, Dart, TypeScript — whatever the project uses. -->

- [Standard 1]
- [Standard 2]
- [Standard 3]

### File Structure
```
project-root/
├── docs/
├── specs/
├── src/ (or lib/)
├── tests/
├── configs/
└── CONSTITUTION.md
```

### Git
- **Commits:** `[TASK-XX] short description`
- **Branches:** `feature/module-name` from `main`
- **Never commit:** .env, API keys, cache files

---

## 5. Testing Requirements

- [Minimum testing rule — e.g., "every function gets 1 happy-path test"]
- [When tests run — e.g., "before every commit"]
- [What blocks merge — e.g., "all tests must pass"]

---

## 6. Cost Guardrails

- **Default model:** [cheapest that meets quality bar]
- **Budget alert:** [flag any single operation > $X]
- **Tracking:** [how costs are logged]
- **Review cadence:** [when you check actual vs estimated]

---

## 7. Forbidden Patterns

<!-- Things you learned the hard way. Each should reference a LESSONS_LEARNED entry. -->

- ❌ [Pattern] — [Why. See LL-XXX-XXX]
- ❌ [Pattern] — [Why. See LL-XXX-XXX]
- ❌ [Pattern] — [Why. See LL-XXX-XXX]

---

## 8. Documentation Rules

1. **Every doc must be in PROJECT_FOUNDATION.md §Doc Registry** — unregistered docs don't exist
2. **Reference, never copy** — use "See [DOC.md §section]" format
3. **One concept, one canonical location** — if it's in two places, merge
4. **No code in docs** — docs describe intent, code lives in src/
5. **No API keys in docs** — keys live in .env ONLY
6. **Spec before code** — no implementation without an approved spec
7. **Lessons are mandatory** — every significant issue gets a LL entry with evidence

### When to write a Lesson Learned
- Any bug that took >1 hour to fix
- Any task that had to be redone
- Any cost surprise (actual > 2x estimated)
- Any architectural assumption that proved wrong
- Any AI/model behavior that was unexpected

---

## 9. For AI Agents (CLAUDE.md)

<!-- This section IS the CLAUDE.md content. Copy it to CLAUDE.md in your repo root.
     Maintain it HERE as canonical source. CLAUDE.md is a derived copy. -->

```markdown
# CLAUDE.md — [Project Name]

## Before ANY implementation
1. Read CONSTITUTION.md for project-wide rules
2. Read the relevant specs/[module]/spec.md
3. Read specs/[module]/plan.md for implementation order
4. Identify which TASK-XX you are implementing — do NOT do multiple tasks at once

## Rules
- [Copy key rules from sections 3-7 above that an AI agent needs]
- Implement ONE task at a time
- Run tests after each task
- If a task fails 2x: STOP and report what's failing
- If requirements are ambiguous: ASK, don't assume

## Forbidden (from §7)
- [Copy forbidden patterns relevant to code generation]
```

---

## Change Log

| Date | Section | Change | Reason |
|------|---------|--------|--------|
| | | Initial version | — |

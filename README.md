# SDD — Spec-Driven Development System
## Master Process Guide
<!--
SCOPE: How to use this template system. Process steps. Session protocols.
NOT HERE: Project-specific content → PROJECT_FOUNDATION.md
NOT HERE: Rules/constraints → CONSTITUTION.md
-->

---

## What Is This?

A documentation and process system for planning, building, and shipping
software (apps, workflows, pipelines) without doing things 10+ times.

The core idea: **specify before you build, one task at a time, stop if it breaks twice.**

---

## File Structure

```
project-root/
│
├── docs/
│   ├── PROJECT_FOUNDATION.md    ← Vision, stack, roadmap, decisions, doc registry
│   ├── DATA_MODEL.md            ← All database/collection schemas
│   ├── INTEGRATIONS.md          ← External APIs, endpoints, limits, costs
│   └── LESSONS_LEARNED.md       ← All failures + fixes + anti-patterns
│
├── specs/
│   └── [module-or-workflow-name]/
│       ├── spec.md              ← What to build and why (MODULE_SPEC or WORKFLOW_SPEC)
│       ├── plan.md              ← How to build it (phases + gates)
│       └── tasks.md             ← Atomic tasks with "done when"
│
├── CONSTITUTION.md              ← Immutable rules (includes AI agent rules)
└── src/                         ← Code lives here, never in docs
```

---

## Session Protocols

### Starting a BUILD session (implementing code)

```
1. Load into AI context:
   - CONSTITUTION.md
   - specs/[current-module]/spec.md
   - specs/[current-module]/plan.md
   - specs/[current-module]/tasks.md

2. Say: "Read the spec and plan. Implement TASK-XX."

3. After task completes:
   - Run tests
   - Commit: "[TASK-XX] description"
   - Move to next task

4. If a task fails 2x → STOP → Review spec → Fix spec first
```

### Starting a PLANNING session (new module/workflow)

```
1. Load into AI context:
   - PROJECT_FOUNDATION.md
   - LESSONS_LEARNED.md (scan for relevant entries)
   - DATA_MODEL.md (if module touches database)

2. Copy the appropriate template:
   - MODULE_SPEC.md (for app features)
   - WORKFLOW_SPEC.md (for pipelines/automations)

3. Say: "I want to build [description]. Ask me questions
   until we have a complete spec."

4. Iterate until spec is complete.
   GATE: Can you explain it in 2 minutes using only the spec?

5. Generate plan.md from spec.
   GATE: Does every phase have a "done when"?

6. Generate tasks.md from plan.
   GATE: Is every task completable in <30 minutes?
```

### Starting an AI chat about an EXISTING project

```
❌ NEVER: "Let me explain everything about my project..."
   (This recreates docs and causes duplication)

✅ ALWAYS: "Read these files: [list]. Now help me with [specific thing]."
   (Uses existing docs as context)
```

---

## Process: New Module or Workflow

```
Step 1: SPEC ──────────────────────────────────────────
  Copy MODULE_SPEC.md or WORKFLOW_SPEC.md → specs/[name]/spec.md
  Fill via iterative Q&A with AI
  GATE: Explainable in 2 min?

Step 2: PLAN ──────────────────────────────────────────
  Generate from spec. Max 5 phases. Each has validation gate.
  GATE: Every phase has "done when"?

Step 3: TASKS ─────────────────────────────────────────
  Generate from plan. Each task <30 min. Each has "done when."
  GATE: Every "done when" verifiable in <1 min?

Step 4: BUILD ─────────────────────────────────────────
  One task at a time. Tests after each. Commit after each.
  RULE: Fails 2x → STOP → fix spec, don't force.

Step 5: VALIDATE ──────────────────────────────────────
  Full test suite. Manual checklist from spec.
  Verify cost vs estimate.

Step 5.5: REVIEW ──────────────────────────────────────
  What took longer than expected? → LESSONS_LEARNED
  What did the spec get wrong? → Update spec template
  Did data model change? → Update DATA_MODEL.md
  Actual cost vs estimated? → Log in spec

Step 6: CLOSE ─────────────────────────────────────────
  Update spec status → ✅ Complete
  Update PROJECT_FOUNDATION.md roadmap
  Update DOC_REGISTRY section
  Merge branch → main
```

---

## Rules

1. **Spec before code** — no exceptions
2. **One task, one commit** — atomic progress
3. **Fails 2x = spec is incomplete** — go back to planning
4. **No code in docs** — specs describe WHAT, code implements HOW
5. **No future specs** — only spec the module you're building NOW
6. **Reference, never copy** — link to canonical doc, don't duplicate content
7. **Every doc in the registry** — if it's not in PROJECT_FOUNDATION §Doc Registry, it doesn't exist
8. **Lessons are mandatory** — every significant issue gets logged with evidence

---

## What Goes WHERE

| Content | Where | Why |
|---------|-------|-----|
| "Why does this project exist?" | PROJECT_FOUNDATION.md | Rarely changes |
| Database schemas + JSON examples | DATA_MODEL.md | Updates per module |
| External API endpoints + limits | INTEGRATIONS.md | Updates per module |
| "What should module X do?" | specs/[module]/spec.md | Written once |
| "How to implement module X?" | specs/[module]/plan.md | Written once |
| "What broke and how we fixed it" | LESSONS_LEARNED.md | Updated continuously |
| Immutable rules + constraints | CONSTITUTION.md | Rarely changes |
| AI prompts / prompt templates | Code: configs/prompts/ | Changes frequently |
| Security rules | Code: firestore.rules or RLS | Changes per module |
| API keys | .env files ONLY | NEVER in docs |
| UI component code | Code: src/ or lib/ | Changes frequently |
| Color palette, fonts, design | PROJECT_FOUNDATION.md §Design | Rarely changes |
| Competitive analysis, GTM | Separate marketing docs | Not in dev docs |

---

## Anti-Patterns That Cause 10+ Iterations

| Anti-Pattern | What Happens | Do This Instead |
|---|---|---|
| Vibe coding (no spec) | Rebuild 10+ times | Spec → Plan → Tasks → Build |
| Monolith doc (everything in one) | Can't find anything, AI loses context | One doc per concern |
| Code in docs | Docs desync after first commit | Code in code, docs describe intent |
| Speccing future modules in detail | Wasted effort, false progress | One-line roadmap entry |
| Skipping edge cases | Discover them in production | Section 6 of spec template |
| Copy-paste between docs | Docs desync within days | Reference with "See [DOC §section]" |
| Starting AI chat without loading docs | Recreate everything from memory | Load existing docs as context |
| No lessons learned | Repeat same mistakes | Log every issue with evidence |
| Huge tasks (>30 min) | Can't measure progress | Split until each is <30 min |
| No validation gates | Ship broken things | Every phase has "done when" |

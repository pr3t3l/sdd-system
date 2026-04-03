# WORKFLOW_SPEC.md — [Workflow Name]
<!--
SCOPE: Complete specification for ONE workflow, pipeline, or automation.
NOT HERE: App module specs → use MODULE_SPEC.md
NOT HERE: Full database schemas → DATA_MODEL.md
NOT HERE: Vision/roadmap → PROJECT_FOUNDATION.md
NOT HERE: Code → src/

WHEN TO USE: For anything that runs as a pipeline, automation, or orchestrated
sequence of steps — whether in OpenClaw, n8n, Cloud Functions, cron jobs,
or any other execution engine.

PROCESS: Same as MODULE_SPEC — fill via Q&A, resolve questions, then plan → tasks → build.
-->

**Workflow:** [Name]
**Date:** YYYY-MM-DD
**Status:** ⬜ Draft → 🔍 Review → ✅ Approved → 🔨 Building → ✅ Complete
**Depends on:** [other workflows/modules that must exist]
**Execution engine:** [OpenClaw / n8n / Cloud Functions / cron / manual scripts]
**Trigger:** [What starts this workflow — e.g., Telegram command, webhook, schedule, event]

---

## 1. Purpose & Scope

### What problem does this workflow solve?
<!-- Be specific. "Manual process X takes Y hours and has Z error rate." -->


### What does it produce?
<!-- Concrete output. "A packaged ZIP with 15-25 PDF documents" or "A weekly email campaign with 12 scripts" -->


### Success Criteria
- [ ] [Measurable outcome — e.g., "produces valid output in <10 minutes"]
- [ ] [Measurable outcome — e.g., "cost per run < $8"]

### In Scope
- [ ] [What this workflow does]

### Out of Scope
- ❌ [What it does NOT do — with pointer to where it's handled]

### Relationship to Other Workflows

| Workflow | Relationship |
|----------|-------------|
| | [e.g., "Provides input to this workflow" or "Receives output from this"] |
| | |

---

## 2. Input / Output Contracts

### Input
<!-- What does this workflow receive to start? -->

**Source:** [Where the input comes from — API, file, user input, upstream workflow]

```json
{
  "field": "type — description",
  "field": "type — description"
}
```

**Validation rules:**
- [e.g., "field X is required, reject if missing"]
- [e.g., "field Y must be > 0"]

### Output
<!-- What does this workflow produce when complete? -->

**Destination:** [Where output goes — file system, database, API, downstream workflow]

```json
{
  "field": "type — description"
}
```

**Quality criteria:**
- [e.g., "all required fields populated with non-stub values"]
- [e.g., "output validates against schema X"]

---

## 3. Phases & Agents

<!-- The heart of the workflow. Each phase = one step in the pipeline. -->

```
[Phase 1] → [Phase 2] → [Phase 3] → ... → [Output]
```

| Phase | What it does | Executor | Model (if AI) | Input | Output | Est. Cost |
|-------|-------------|----------|--------------|-------|--------|-----------|
| 1 | | script / agent / manual | | | | $X.XX |
| 2 | | | | | | $X.XX |
| 3 | | | | | | $X.XX |
| **Total** | | | | | | **$X.XX** |

### Gate Criteria (between phases)

| Gate | After Phase | Pass Condition | Fail Action |
|------|------------|----------------|-------------|
| G1 | Phase 1 → 2 | [e.g., "output validates against schema"] | [e.g., "retry with diagnosis, max 2x"] |
| G2 | Phase 2 → 3 | | |
| G3 | Final | [e.g., "all outputs present + quality score > 80%"] | |

---

## 4. Model Selection

<!-- Only for workflows that use AI/LLM. Delete if N/A. -->

| Task | Model | Why this one | Fallback | Cost/call |
|------|-------|-------------|----------|-----------|
| | | | | |

### Model Rules
- [e.g., "Use cheapest model that passes quality gate"]
- [e.g., "Reasoning models for creative tasks, standard for formatting"]
- [e.g., "Never use Model X for task Y — see LL-XXX"]

---

## 5. Failure & Recovery

<!-- What happens when things break? This section prevents 80% of debugging time. -->

| Failure Mode | Detection | Recovery | Max Retries |
|-------------|-----------|----------|-------------|
| [e.g., API timeout] | [e.g., subprocess exit code ≠ 0] | [e.g., retry with backoff 2s/5s/10s] | 2 |
| [e.g., Output schema invalid] | [e.g., validate_schema.py fails] | [e.g., retry with failure diagnosis in prompt] | 2 |
| [e.g., Budget exceeded] | [e.g., cost tracker > threshold] | [e.g., STOP, alert human] | 0 |
| [e.g., Upstream data missing] | [e.g., input validation fails] | [e.g., reject with clear error message] | 0 |

### Escalation Chain
<!-- What happens after max retries? -->
1. [e.g., "Log error with full context"]
2. [e.g., "Save partial output for inspection"]
3. [e.g., "Alert human via Telegram"]
4. [e.g., "Human decides: retry with changes or abort"]

### State Persistence
<!-- How does the workflow save progress so you don't restart from scratch? -->
- [e.g., "manifest.json updated after each phase with status + cost"]
- [e.g., "Intermediate outputs saved to phase_X/ directory"]
- [e.g., "Can resume from any phase by running: script --resume --from-phase X"]

---

## 6. Cost Tracking

### Budget
| Metric | Target |
|--------|--------|
| Cost per run | $X.XX |
| Cost per day/week | $X.XX |
| Hard limit (stop if exceeded) | $X.XX |

### How costs are tracked
- [e.g., "Each spawn script logs tokens + cost to manifest.json"]
- [e.g., "LiteLLM /spend endpoint for orchestrator overhead"]
- [e.g., "cost_tracker.py aggregates after each run"]

---

## 7. Operational Playbook

<!-- Exact commands to run this workflow. Copy-paste ready. -->

### Run the workflow
```bash
# Full run
[command]

# Resume from phase X
[command]

# Dry run (no API calls)
[command]
```

### Verify results
```bash
# Check output
[command]

# Validate quality
[command]

# Check cost
[command]
```

### Common fixes
```bash
# If [problem]:
[fix command]

# If [problem]:
[fix command]
```

---

## 8. Open Questions

- [ ] [Question?]
- [ ] [Question?]

---

## 9. Pre-Flight Checklist

- [ ] Input contract defined (§2) — I know exactly what goes in
- [ ] Output contract defined (§2) — I know exactly what comes out
- [ ] All phases have gate criteria (§3) — no phase passes without evidence
- [ ] Failure modes documented (§5) — I know what to do when it breaks
- [ ] Budget set with hard limit (§6)
- [ ] Single-item test planned BEFORE batch run (See LL-PLAN-003)
- [ ] File I/O verified for all agents/scripts (See LL-ARCH-006)
- [ ] Cost tracking built into every script from day 1 (See LL-COST-014)
- [ ] Relevant lessons from LESSONS_LEARNED.md reviewed:
  - [ ] [LL-XXX: how it applies]
  - [ ] [LL-XXX: how it applies]

---

## 10. Definition of Done

- [ ] All phases execute successfully end-to-end
- [ ] Output meets quality criteria (§2)
- [ ] Cost per run within budget (§6)
- [ ] Operational playbook tested (§7) — commands actually work
- [ ] Failure recovery tested — at least 1 failure mode triggered and handled
- [ ] DATA_MODEL.md updated (if schemas changed)
- [ ] LESSONS_LEARNED.md updated (if issues hit)
- [ ] PROJECT_FOUNDATION.md §Doc Registry updated
- [ ] This spec status → ✅ Complete

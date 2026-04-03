# MODULE_SPEC.md — [Module Name]
<!--
SCOPE: Complete specification for ONE app module/feature.
NOT HERE: Workflow/pipeline specs → use WORKFLOW_SPEC.md
NOT HERE: Full database schemas → DATA_MODEL.md (reference specific fields here)
NOT HERE: Vision/roadmap → PROJECT_FOUNDATION.md
NOT HERE: Code → src/

PROCESS:
1. Fill sections 1-8 via iterative Q&A with AI
2. Resolve ALL Open Questions (§9)
3. Pass Pre-Flight Checklist (§10)
4. Generate plan.md → tasks.md
5. ONLY THEN start coding
-->

**Module:** [Name]
**Date:** YYYY-MM-DD
**Status:** ⬜ Draft → 🔍 Review → ✅ Approved → 🔨 Building → ✅ Complete
**Depends on:** [modules that must be complete first]
**Modifies DATA_MODEL.md:** Yes/No — [which collections/tables]

---

## 1. Purpose & Scope

### What problem does this module solve?
<!-- Be specific. "Users can't do X because Y doesn't exist." -->


### What does this module do?
<!-- 2-3 sentences. Concrete, not aspirational. -->


### Success Criteria
- [ ] [Specific, measurable outcome]
- [ ] [Specific, measurable outcome]

### In Scope
- [ ] [Feature/behavior included]
- [ ] [Feature/behavior included]

### Out of Scope (explicit)
- ❌ [Thing] — will be in [future module/phase]
- ❌ [Thing] — not needed for MVP

---

## 2. User Stories

<!-- As [role], I want [action], so that [benefit].
     Keep stories SMALL. If >8 criteria, split the story. -->

### US-[MOD]-001: [Title]
**As** [role], **I want** [action], **so that** [benefit].

**Acceptance Criteria:**
- [ ] [Criterion — specific, testable]
- [ ] [Criterion]
- [ ] UI text available in [languages]

### US-[MOD]-002: [Title]
**As** [role], **I want** [action], **so that** [benefit].

**Acceptance Criteria:**
- [ ] [Criterion]
- [ ] [Criterion]

---

## 3. Business Rules

<!-- The "gold" — rules that govern behavior beyond UI.
     These are the things AI and developers get WRONG if not explicit. -->

1. **[Rule name]:** [Exact behavior expected. E.g., "A family account cannot exist without a realtor_id."]
2. **[Rule name]:** [Exact behavior]
3. **[Rule name]:** [Exact behavior]

---

## 4. Data Model (Module-Specific)

<!-- Only what THIS module creates or modifies. Full schemas → DATA_MODEL.md -->

### New Collections/Tables
```json
{
  "field": "type — description"
}
```

### Modified Collections/Tables
**`/existing_collection`** — adds:
```json
{
  "newField": "type — description"
}
```

### Data Flow
```
[User Action] → [Frontend] → [Service/API] → [Database]
                                    ↓
                              [Side effects]
```

---

## 5. Technical Decisions

<!-- Lock these BEFORE coding. Don't let AI improvise. -->

| Decision | Choice | Why | Alternatives Rejected |
|----------|--------|-----|----------------------|
| | | | |

---

## 6. UI Screens & Navigation

<!-- NO code here. Descriptions only. -->

| Screen | Purpose | Key Elements | Who sees it |
|--------|---------|-------------|-------------|
| | | | |

### Navigation Flow
```
[Entry] → [Screen A] → [Screen B]
                ↓
          [Screen C] (conditional)
```

---

## 7. Edge Cases & Error Handling

<!-- THIS SECTION PREVENTS 80% OF REWORK. Think about EVERY "what if." -->

| # | Scenario | Expected Behavior | Severity |
|---|----------|-------------------|----------|
| 1 | | | High/Med/Low |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |

---

## 8. Cost & Monitoring

### Cost Implications
| Operation | Est. Cost | Frequency | Monthly Est. |
|-----------|----------|-----------|-------------|
| | | | |

### How will you know it works? (Observability)
<!-- 2-3 metrics max. What tells you this module is healthy in production? -->
- **SLI 1:** [What you measure — e.g., "successful family creations / total attempts"]
- **SLI 2:** [What you measure]
- **Acceptable threshold:** [e.g., ">95% success rate"]

---

## 9. Open Questions

<!-- Resolve ALL before generating plan.md -->
- [ ] [Question?]
- [ ] [Question?]

---

## 10. Pre-Flight Checklist

<!-- Before building, verify these. Reference LESSONS_LEARNED.md entries. -->

- [ ] Data flow is clear: every input has a source, every output has a consumer
- [ ] Schemas defined for all new data (in §4 above)
- [ ] Budget/cost estimated (§8) and within acceptable range
- [ ] Edge cases documented (§7) — at least 5
- [ ] Open questions (§9) are ALL resolved
- [ ] Relevant lessons from LESSONS_LEARNED.md reviewed and applied:
  - [ ] [LL-XXX: lesson title — how it applies here]
  - [ ] [LL-XXX: lesson title — how it applies here]

---

## 11. Testing & Definition of Done

### Tests
| Test | Validates |
|------|----------|
| | |
| | |

### Manual Validation
- [ ] [Check]
- [ ] i18n: all strings render in [languages]
- [ ] Security: unauthorized users cannot [action]

### Definition of Done (module is COMPLETE when)
- [ ] All tasks in tasks.md marked complete
- [ ] All tests pass
- [ ] Cost within budget estimate (§8)
- [ ] DATA_MODEL.md updated (if schemas changed)
- [ ] LESSONS_LEARNED.md updated (if issues were hit)
- [ ] PROJECT_FOUNDATION.md §Doc Registry updated
- [ ] This spec status → ✅ Complete

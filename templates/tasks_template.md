# tasks.md — [Module/Workflow Name]
<!--
GENERATED from plan.md. Do not write from scratch.
Process: Load plan.md into AI → "Convert to atomic tasks. Each <30 min."

RULES:
- Each task completable in ONE AI session (<30 min)
- Each task has a "Done when" verifiable in <1 minute
- Each task lists files it touches
- Tasks are executed IN ORDER (dependencies are sequential)
-->

**Source plan:** `specs/[name]/plan.md`
**Date:** YYYY-MM-DD
**Total tasks:** [X]

---

## Phase 1: [Name]

### TASK-01: [Short title]
- **Files:** [files this task creates or modifies]
- **Depends on:** none
- **Done when:** [specific, verifiable in <1 min — e.g., "file exists and parses without error"]
- **Prompt for AI:**
  ```
  Read specs/[name]/spec.md.
  [Exact instruction for what to implement]
  After implementing, run [test command].
  ```

### TASK-02: [Short title]
- **Files:** [files]
- **Depends on:** TASK-01
- **Done when:** [criterion]
- **Prompt for AI:**
  ```
  [Instruction]
  ```

---

## Phase 2: [Name]

### TASK-03: [Short title]
- **Files:** [files]
- **Depends on:** TASK-02
- **Done when:** [criterion]
- **Prompt for AI:**
  ```
  [Instruction]
  ```

---

<!-- Continue for all phases -->

## Progress Tracker

| Task | Status | Commit | Notes |
|------|--------|--------|-------|
| TASK-01 | ⬜🟡✅ | | |
| TASK-02 | ⬜🟡✅ | | |
| TASK-03 | ⬜🟡✅ | | |

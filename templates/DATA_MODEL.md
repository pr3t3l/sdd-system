# DATA_MODEL.md — [Project Name]
<!--
SCOPE: ALL database schemas, relationships, indexes, security rules.
       Single canonical source for data structure.
NOT HERE: Why we chose this database → PROJECT_FOUNDATION.md §Tech Stack
NOT HERE: Module-specific data flow → specs/[module]/spec.md §4
NOT HERE: API endpoints → INTEGRATIONS.md

UPDATE FREQUENCY: Every time a module adds or modifies collections/tables.
-->

**Last updated:** YYYY-MM-DD
**Database:** [Firestore / PostgreSQL / Supabase / etc.]

---

## Conventions

| Convention | Standard |
|-----------|----------|
| ID format | [e.g., Firestore auto-gen, UUID v4, serial] |
| Timestamps | [e.g., Firestore Timestamp, ISO 8601, Unix] |
| Field naming | [e.g., camelCase, snake_case] |
| Soft delete | [e.g., `isActive: false` vs actual deletion] |
| Null handling | [e.g., "omit field" vs "set to null"] |

---

## Collections / Tables

### [collection_name]

**Purpose:** [One sentence]
**Path/Table:** `[/collection/{id}` or `schema.table_name]`
**Created by module:** [module name]
**Read by modules:** [module names]

```json
{
  "id": "string — auto-generated",
  "field1": "string — description of what this stores",
  "field2": 0,
  "nestedObject": {
    "subField": "string — description"
  },
  "arrayField": ["string — what these contain"],
  "createdAt": "Timestamp",
  "updatedAt": "Timestamp"
}
```

**Indexes:**
- [field] + [field] — composite, for [query description]

**Security/Access:**
- Read: [who can read — e.g., "owner only", "family members", "admin"]
- Write: [who can write]
- Delete: [who can delete]

---

### [next_collection]

<!-- Repeat structure for each collection/table -->

---

## Relationships

```
[users] 1──N [child_collection]      (subcollection / FK)
[users] N──N [other_collection]      (via junction or array)
```

---

## Migration Log

| Date | Collection | Change | Breaking? | Status |
|------|-----------|--------|-----------|--------|
| | | Initial schema | No (new) | ✅ Deployed |

# INTEGRATIONS.md — [Project Name]
<!--
SCOPE: ALL external APIs, services, and third-party integrations.
       Endpoints, rate limits, costs, auth method.
NOT HERE: API keys → .env file ONLY (NEVER in this doc)
NOT HERE: Internal database schemas → DATA_MODEL.md
NOT HERE: How modules use these APIs → specs/[module]/spec.md

UPDATE FREQUENCY: When adding a new integration or when limits/pricing change.
-->

**Last updated:** YYYY-MM-DD

---

## API Key Management

**Location:** `[path to .env file]`
**Rule:** API keys are NEVER written in documentation files. This doc describes endpoints and limits only.

---

## Integrations

### [Service Name] (e.g., Zillow, Mapbox, OpenAI)

**Purpose:** [What it does for your project — one sentence]
**Auth method:** [API key / OAuth2 / JWT / etc.]
**Base URL:** `[https://api.example.com/v1]`
**Docs:** [link to official documentation]

| Endpoint | Method | What it does | Rate Limit | Cost/Call | Used by Module |
|----------|--------|-------------|------------|-----------|---------------|
| `/endpoint` | GET | [description] | [X/min] | [$X.XX] | [module name] |
| `/endpoint` | POST | [description] | [X/min] | [$X.XX] | [module name] |

**Gotchas / Known Issues:**
- [e.g., "Returns 429 after 100 calls/min — implement backoff"]
- [e.g., "Response format changed in v3 — we use v2"]

**Caching strategy:**
- [e.g., "Cache responses for 7 days" or "No caching — always fresh"]

---

### [Next Service]

<!-- Repeat structure -->

---

## Cost Summary

| Service | Est. Cost/Month | What drives cost | Optimization |
|---------|----------------|------------------|-------------|
| | | | |

**Monthly budget target:** $[X]
**Alert threshold:** $[X] (notify when 80% consumed)

---

## Health Checks

<!-- How to verify integrations are working -->

| Service | Health Check | Expected |
|---------|-------------|----------|
| [Service] | `[curl command or check]` | [expected response] |

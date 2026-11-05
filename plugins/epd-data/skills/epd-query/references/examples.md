# Worked examples and recovery

These are instruction examples, not executed queries or real result records. No key, numerical factor, candidate name or source URL is fabricated. Use only actual responses when completing a user request.

## Swiss C24 technically dried and planed timber

Known: construction solid timber, C24, technical drying, planing, Switzerland. Reference time is unknown. Do not ask these known facts again or invent a year. Distinguish production in Switzerland from delivery/use there if that distinction is needed for the requested final value; initial candidate search can proceed while keeping it explicit.

This program can search declarations for this product, not background datasets. Explain that domain if the user specifically needs a background process. Do not invoke another program as a scope bypass. Search the product requirements as declarations:

```bash
epd-data search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --limit 5 --json
```

Use actual epd_key values for authenticated lookup, then inspect product coverage, declared unit, geography, validity and modules. The declaration title alone does not establish the full requested product specification.

A complete response reports one of the evidence-supported outcomes: a match with citations; a conditional proxy with named gaps; or no supported match. Example answer structure (replace with actual facts, not invented records): “The returned evidence [supports/does not establish] C24, technical drying and planing. Geography is [returned evidence]; reference time remains [evidence or unknown]. [Retrieved value with method/unit/boundary, or reason it is unavailable]. [Exact returned links].” For zero candidates, report the query/scope and no match for this request; retain hard constraints and ask before any material relaxation.

## EPD declaration workflow

Search published declarations with an actual publisher subset if requested, --limit 1..100 and a complete query. Follow only a returned cursor with the same conditions. Before lookup, ensure product authentication; use exact epd_key values. Present declaration identity/link, product, declared unit, validity and method/modules actually found. If the summary lacks a validity or requested module, retrieve available details or mark unknown; do not imply certification.

## Fixed-scope comparison

Compare only candidates returned within this program's compiled publisher scope. If the user requests another database or domain, explain this program's boundary; do not call a wider client to bypass it. Candidate comparison is evidence analysis, not a new service statistics endpoint.

## Failure and continuation decisions

| Evidence | Next action |
| --- | --- |
| Missing/untrusted command | Read preparation.md and installation.json; install the checksum-verified pinned program within host permissions. Preserve unknown same-name entries. |
| Permission-check unavailable / HTTP 503 / DATASET_PERMISSION_UNAVAILABLE | Report a service failure, preserve its actual error code/requestId, and do not interpret it as denied entitlement. The code alone does not identify which upstream directory, transport or permission stage failed. Do not relogin, change accounts or invent numerical results; one transient retry is enough before reporting the blocker. |
| Missing credential or endpoint explicitly rejects credential | Manage one product login, browser/clickable link, original process result and query continuation; do not inspect credential files. |
| Pending approval | Keep the original task ID/request; rely on CLI polling and host completion. User approval text alone is not final success. |
| Login expired/denied/network error | Report actual error and keep pending request; retry only after original attempt ends and conditions warrant it. |
| Query timeout/transport failure | No successful empty result. Preserve error; a transient failure may warrant one deliberate retry, not parallel or unbounded requests. |
| Search not_found/empty | No match for this request, not proof the source is empty. Retain hard conditions and identify any proposed relaxation. |
| found=false or missingKeys | Missing requested identity; preserve row-level and business coverage evidence. Do not invent a replacement record. |
| restricted/accessDecision denial | Retain visible metadata and exact links; state unavailable numbers. Do not repeat login, purchase, change identity or use a literature factor as the restricted value. |
| Source/publisher outside scope or unverifiable response | Treat as an error; do not strip provenance or accept contaminated rows. |
| Missing method/unit/technology/time evidence | Obtain permitted lookup details or mark unknown; do not present an unsupported recommendation or comparison. |

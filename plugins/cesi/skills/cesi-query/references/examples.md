# Worked examples and recovery

These are instruction examples, not executed queries or real result records. No key, numerical factor, candidate name or source URL is fabricated. Use only actual responses when completing a user request.

## Swiss C24 technically dried and planed timber

Known: construction solid timber, C24, technical drying, planing, Switzerland. Reference time is unknown. Do not ask these known facts again or invent a year. Distinguish production in Switzerland from delivery/use there if that distinction is needed for the requested final value; initial candidate search can proceed while keeping it explicit.

After preparing cesi and completing required login, discover source versions/models if the user needs a specific coordinate, then search:

```bash
cesi search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --json
```

Read status/summary and actual datasets. Check src/ver/model, loc, unit and ref_product; fit alone does not demonstrate C24/drying/planing. Select exact returned keys for lookup when details or a numerical value are needed. Pass them as one safely quoted positional argument (comma-separated for multiple keys); do not manufacture example keys. If preview omitted descriptions, use --full before judging the covered processes. Check whether drying/planing are included and avoid double counting.

A complete response reports one of the evidence-supported outcomes: a match with citations; a conditional proxy with named gaps; or no supported match. Example answer structure (replace with actual facts, not invented records): “The returned evidence [supports/does not establish] C24, technical drying and planing. Geography is [returned evidence]; reference time remains [evidence or unknown]. [Retrieved value with method/unit/boundary, or reason it is unavailable]. [Exact returned links].” For zero candidates, report the query/scope and no match for this request; retain hard constraints and ask before any material relaxation.


## Fixed-scope comparison

Compare only candidates returned within this program's compiled source scope. If the user requests another database or domain, explain this program's boundary; do not call a wider client to bypass it. Candidate comparison is evidence analysis, not a new service statistics endpoint.

## Failure and continuation decisions

| Evidence | Next action |
| --- | --- |
| Missing/untrusted command | Read preparation.md and installation.json; install the checksum-verified pinned program within host permissions. Preserve unknown same-name entries. |
| Missing credential or endpoint explicitly rejects credential | Manage one product login, browser/clickable link, original process result and query continuation; do not inspect credential files. |
| Pending approval | Keep the original task ID/request; rely on CLI polling and host completion. User approval text alone is not final success. |
| Login expired/denied/network error | Report actual error and keep pending request; retry only after original attempt ends and conditions warrant it. |
| Query timeout/transport failure | No successful empty result. Preserve error; a transient failure may warrant one deliberate retry, not parallel or unbounded requests. |
| Search not_found/empty | No match for this request, not proof the source is empty. Retain hard conditions and identify any proposed relaxation. |
| found=false or missingKeys | Missing requested identity; preserve row-level and business coverage evidence. Do not invent a replacement record. |
| restricted/accessDecision denial | Retain visible metadata and exact links; state unavailable numbers. Do not repeat login, purchase, change identity or use a literature factor as the restricted value. |
| Source/publisher outside scope or unverifiable response | Treat as an error; do not strip provenance or accept contaminated rows. |
| Missing method/unit/technology/time evidence | Obtain permitted lookup details or mark unknown; do not present an unsupported recommendation or comparison. |

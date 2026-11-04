# Worked examples and recovery

These are instruction examples, not executed queries or real result records. No key, numerical factor, candidate name or source URL is fabricated. Use only actual responses when completing a user request.

## Swiss C24 technically dried and planed timber

Known: construction solid timber, C24, technical drying, planing, Switzerland. Reference time is unknown. Do not ask these known facts again or invent a year. Distinguish production in Switzerland from delivery/use there if that distinction is needed for the requested final value; initial candidate search can proceed while keeping it explicit.

After preparing environmental-data and completing required login, discover source versions/models if the user needs a specific coordinate, then search:

```bash
environmental-data search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --json
```

Read status/summary and actual datasets. Check src/ver/model, loc, unit and ref_product; fit alone does not demonstrate C24/drying/planing. Select exact returned keys for lookup when details or a numerical value are needed. Pass them as one safely quoted positional argument (comma-separated for multiple keys); do not manufacture example keys. If preview omitted descriptions, use --full before judging the covered processes. Check whether drying/planing are included and avoid double counting.

A complete response reports one of the evidence-supported outcomes: a match with citations; a conditional proxy with named gaps; or no supported match. Example answer structure (replace with actual facts, not invented records): “The returned evidence [supports/does not establish] C24, technical drying and planing. Geography is [returned evidence]; reference time remains [evidence or unknown]. [Retrieved value with method/unit/boundary, or reason it is unavailable]. [Exact returned links].” For zero candidates, report the query/scope and no match for this request; retain hard constraints and ask before any material relaxation.

## EPD declaration workflow

Search published declarations with --kind epd and an actual publisher subset if requested, --limit 1..100 and a complete query. Follow only a returned cursor with the same conditions. Before lookup, ensure product authentication; use exact epd_key values and --kind epd again. Present declaration identity/link, product, declared unit, validity and method/modules actually found. If the summary lacks a validity or requested module, retrieve available details or mark unknown; do not imply certification.

## Cross-source comparison

For a request comparing concrete background data from HiQLCD and ecoinvent, first read sources metadata if version/model matters, then:

```bash
environmental-data search 'Compare candidate concrete production data for use in Switzerland; preserve source differences and unknown reference time' --sources 'hiqlcd|ecoinvent' --json
```

The quoted separator is part of the parameter, not a shell pipeline. Look up selected exact dataset keys in the same datasets domain. Show provenance and boundaries separately. Do not rank values unless units, methods, model and boundaries are demonstrably comparable. A denied source is reported, not replaced silently.

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

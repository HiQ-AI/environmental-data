# Read results and justify the conclusion

## Envelopes and coverage

Search/lookup success is stdout JSON {ok:true, command, detail, data, ...}. It says the command completed, not that a candidate is suitable or a numerical value is authorized. Failure exits nonzero and writes stderr {ok:false, kind, message, code} when --json is used; never parse that as successful empty data. Doctor's ok means only local credential presence.

Default detail=preview recursively keeps up to 10 rows per array and omits desc, description, documentation, provenance and classifications fields. Outer coverage.partial and coverage.omitted contain paths, omitted row counts or omitted detail markers. These counts describe the received response only. Run the same necessary request with --full to inspect all returned rows/details, optionally writing to an authorized local file. Do not claim a lookup's missing description is absent at source before checking preview omissions. --full has detail=full and no outer preview coverage; it does not add rights or exhaust server pagination.

Lookup has a separate business coverage under the CLI's data.coverage: requested, returned, missingKeys. Rows live at data.data. found=false is an explicit returned miss; it can count as returned and is not necessarily listed in missingKeys. EPD may omit unknown keys, which appear in missingKeys. Neither a missing key nor a restricted row proves the database has no matching data. sources has its own data.coverage with supported/published/missing source codes, not preview completeness or entitlements.

## Read the actual domain fields

| Response | Fields and interpretation |
| --- | --- |
| Direct search (outer data) | data.data rows with page {cursor, limit, total} and a notice. Each row: datasetRef (the key for lookup/lci/lcia), name and referenceProduct {name, unit, amount} as locale maps (en_US, zh_CN, _ original), location {id, name}, source {code, version, commercial}, systemModel.code, activityUuid, searchEvidence (lexical score only) and webUrl when the source has a public page. |
| Assisted search (outer data) | status/summary and datasets: key, name, link, src/ver/model, loc, unit, ref_product, fit, restricted. Preserve upstream status, including not-found. fit is service matching evidence, not certification. |
| Dataset lookup row | datasetRef, found and source.code establish identity/source. headlineGwp {value, unit, family, method, restricted, reason}; accessDecision {authorized, menus}; webUrl. documentation.source is a citation, not the dataset source coordinate. |
| lci | dataset (identity, coordinate, webUrl), data rows {flow.name, flow.id, amount, unit, direction, flowCategory}, page {cursor, total}, restricted. Amounts are per reference-product unit of the dataset. |
| lcia | dataset, data rows {method {id, impactMethod, impactCategory, indicator}, value, unit}, page, methodIdsWithData, restricted. Batch: data[] items {dataset, datasetRef, total, restricted, items, error}. Contributions: data {total, stages[{code, name, contribution, contributionPct}], attribution complete/partial/unavailable}. |
| EPD search | Outer data contains the upstream data array, page and meta when provided. epd_key and source.pt_source identify declaration and publisher. Read actual returned declaration/product, unit, validity, method/module and link fields; not all summaries supply them. |
| EPD lookup row | epd_key, source.pt_source and actual returned details/restrictions. An EPD summary is not a full declaration review. |

Use only numbers the CLI actually returned. headlineGwp is one method's GWP100, not a full LCIA table; lci is the cumulative inventory, not unit-process exchanges. A restricted row with total > 0 means data exists but this account cannot read it; check the restriction reason (for example the CLI is not enabled for commercial values) rather than inferring absence. attribution partial/unavailable in contributions means the residual bucket is not purely direct emissions. Null/missing/restricted values stay unavailable; numeric 0 is a legitimate value, not a missing-value sentinel. Do not substitute papers or proxies for a restricted database value.

## Professional interpretation

- Check each hard requirement against evidence, not only names: product form/grade, treatment, geography, reference period, technology, model, unit and system boundary. Unknown year stays unknown; database release year is not process reference year.
- Distinguish production geography from use, market supply and transport geography. A market dataset can include a supply mix/transport that a production activity does not. A name cannot establish this boundary; inspect lookup descriptions.
- Distinguish raw feedstock, intermediate, finished product and processing service. C24 strength grading, drying and planing each require evidence; do not assume a broad timber label covers them. Do not add drying/planing again if already included; do not close an unknown boundary gap with a generic factor.
- Reference product/unit is not automatically the user's functional unit. Convert only with evidenced density, moisture, yield or another justified relation. Retain conversion assumptions; never compare kg and m3 directly.
- For GWP/LCIA comparison require value, unit, method/version, relevant modules/boundary and authorization evidence. Different sources/models/methods or incompatible units cannot be directly ranked or combined into a median. An EPD's declared unit, product, validity and module evidence must fit the use; A1-A3 is not automatically whole life.
- Comparing two datasets (for example East China low-voltage electricity across two databases): confirm reference product and unit, location, system model and that both values use the same methodId family before stating a difference. Show the difference with its method, then explain it with lcia --contributions and the greenhouse-gas flows from lci --type output --category air.
- Recomputing per-gas contributions from lci: the service has no characterisation-factor endpoint, so cite the factor table you use (for example IPCC AR6 GWP100) and match its version to the dataset's methodId. Match flows by name and compartment, not by flow id (ids differ between databases). Keep fossil, biogenic and land-use CO2 separate as the method does. Reconcile the sum against the lcia total for the same method; if it does not reconcile, report the gap and do not present a per-gas conclusion.
- No database-wide statistics API is provided. Any optional calculation over accessible comparable candidates must identify the actual sample, exclusions, missing/restricted values and harmonization. Never call a search sample an industry or database distribution.

## User-facing output

Start with the actual outcome: defensible match, conditional proxy, candidates needing evidence, or no supported match. Use the user's language. Include a compact table:

| Candidate | Source / version / model | Region / unit | Match evidence | Missing or conflicting requirements | Access | Link |
| --- | --- | --- | --- | --- | --- | --- |

Populate only actual results. Links must be exact returned link/webUrl values, formatted as clickable Markdown so reviewers can audit the numbers on the dataset page. If no link is returned say so; do not derive a URL from a key. Keep exact keys in a separate traceability field where needed for continuation. Cite details versus search summaries distinctly. Numerical answers also state value/unit/method/boundary, provenance, sample limits and unresolved assumptions. If all candidates fail a hard requirement, say not found rather than silently relaxing it; offer a clearly conditional proxy only with the user's required decision/consent.

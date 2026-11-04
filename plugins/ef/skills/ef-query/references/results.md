# Read results and justify the conclusion

## Envelopes and coverage

Search/lookup success is stdout JSON {ok:true, command, detail, data, ...}. It says the command completed, not that a candidate is suitable or a numerical value is authorized. Failure exits nonzero and writes stderr {ok:false, kind, message, code} when --json is used; never parse that as successful empty data. Doctor's ok means only local credential presence.

Default detail=preview recursively keeps up to 10 rows per array and omits desc, description, documentation, provenance and classifications fields. Outer coverage.partial and coverage.omitted contain paths, omitted row counts or omitted detail markers. These counts describe the received response only. Run the same necessary request with --full to inspect all returned rows/details, optionally writing to an authorized local file. Do not claim a lookup's missing description is absent at source before checking preview omissions. --full has detail=full and no outer preview coverage; it does not add rights or exhaust server pagination.

Lookup has a separate business coverage under the CLI's data.coverage: requested, returned, missingKeys. Rows live at data.data. found=false is an explicit returned miss; it can count as returned and is not necessarily listed in missingKeys. EPD may omit unknown keys, which appear in missingKeys. Neither a missing key nor a restricted row proves the database has no matching data. sources has its own data.coverage with supported/published/missing source codes, not preview completeness or entitlements.

## Read the actual domain fields

| Response | Fields and interpretation |
| --- | --- |
| Background search (outer data) | status/summary and datasets when returned. Preserve upstream status, including not-found states, rather than overriding it with outer ok. |
| Dataset candidate | key, name, link, src/ver/model, loc, unit, ref_product, material, fit, restricted; optional gwp/gwp_unit/dqi. Missing optional fields are unknown. fit is service matching evidence, not a certification or proof all hard requirements match. |
| Dataset lookup row | datasetRef, found and source.code establish identity/source. Preserve actual returned coordinates, descriptions/documentation, accessDecision, restricted flags and numerical fields without assuming a fixed universal payload. documentation.source is a citation, not the dataset source coordinate. |
| EPD search | Outer data contains the upstream data array, page and meta when provided. epd_key and source.pt_source identify declaration and publisher. Read actual returned declaration/product, unit, validity, method/module and link fields; not all summaries supply them. |
| EPD lookup row | epd_key, source.pt_source and actual returned details/restrictions. An EPD summary is not a full declaration review. |

LCI/LCIA are not separate CLI tools. Use only numerical inventories, impacts or headline values actually returned by authorized lookup. A gwp or headlineGwp value does not establish a full LCI, complete LCIA table or every method. Null/missing/restricted values stay unavailable; numeric 0 is a legitimate value, not a missing-value sentinel. Do not substitute papers or proxies for a restricted database value.

## Professional interpretation

- Check each hard requirement against evidence, not only names: product form/grade, treatment, geography, reference period, technology, model, unit and system boundary. Unknown year stays unknown; database release year is not process reference year.
- Distinguish production geography from use, market supply and transport geography. A market dataset can include a supply mix/transport that a production activity does not. A name cannot establish this boundary; inspect lookup descriptions.
- Distinguish raw feedstock, intermediate, finished product and processing service. C24 strength grading, drying and planing each require evidence; do not assume a broad timber label covers them. Do not add drying/planing again if already included; do not close an unknown boundary gap with a generic factor.
- Reference product/unit is not automatically the user's functional unit. Convert only with evidenced density, moisture, yield or another justified relation. Retain conversion assumptions; never compare kg and m3 directly.
- For GWP/LCIA comparison require value, unit, method/version, relevant modules/boundary and authorization evidence. Different sources/models/methods or incompatible units cannot be directly ranked or combined into a median. An EPD's declared unit, product, validity and module evidence must fit the use; A1-A3 is not automatically whole life.
- No database-wide statistics API is provided. Any optional calculation over accessible comparable candidates must identify the actual sample, exclusions, missing/restricted values and harmonization. Never call a search sample an industry or database distribution.

## User-facing output

Start with the actual outcome: defensible match, conditional proxy, candidates needing evidence, or no supported match. Use the user's language. Include a compact table:

| Candidate | Source / version / model | Region / unit | Match evidence | Missing or conflicting requirements | Access | Link |
| --- | --- | --- | --- | --- | --- | --- |

Populate only actual results. Links must be exact returned links, formatted as clickable Markdown. If no link is returned say so; do not derive a URL from a key. Keep exact keys in a separate traceability field where needed for continuation. Cite details versus search summaries distinctly. Numerical answers also state value/unit/method/boundary, provenance, sample limits and unresolved assumptions. If all candidates fail a hard requirement, say not found rather than silently relaxing it; offer a clearly conditional proxy only with the user's required decision/consent.

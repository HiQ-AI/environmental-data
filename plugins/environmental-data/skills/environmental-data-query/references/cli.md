# environmental-data CLI parameters (0.8.3)

Use the verified executable from preparation for all commands. The examples show its bare name only when that entry is trusted. Command arguments must be passed separately through the host's process tool when possible. If using a shell, quote the complete query and every opaque key/source expression. Never concatenate raw user input into a shell command. Single quotes in the examples work in POSIX and PowerShell for these fixed strings; real apostrophes require the shell's actual escaping rules (PowerShell doubles a single quote; POSIX closes/reopens the quoted string). A literal | must remain inside quotes, not become a pipeline.

## Program scope and domains

- Program: environmental-data; protocol: relic-datasets.
- Compiled background source codes: hiqlcd, hiqlcd-al, calcd, hiq-cesi, ecoinvent, carbonminds, agrifootprint, ef, auslci, bafu, bioenergiedat, elcd, needs, ozlci, recycledplastics, usda, uslci, worldsteel.
- Compiled EPD publisher codes: none.
- Default kind is datasets. --kind epd is outside scope. Select one or several supported databases with --sources.

## Argument format and joining rules

Construct arguments as structured values before execution. The executable path is separate from its argv array; quotation marks belong to shell syntax, not to values passed directly in argv.

- Query: pass the complete natural-language request as the single positional argument after search. Do not use --query, split a sentence into several arguments, URL-encode it or pre-escape it for HTTP; the CLI handles transport encoding.
- Lookup: collect exact key values from actual search results and join them with a comma into one positional argument after lookup. The CLI trims surrounding whitespace, removes empty entries and deduplicates; the resulting list must contain 1..200 keys. Keep each opaque key unchanged: do not decode, rebuild, case-normalize or apply source-coordinate formatting to it.
- Sources: format each coordinate as code or code:version, then join coordinates with | into one --sources value. Use canonical source codes and actual advertised version strings; the colon separates source from version, never from model. The parser also accepts comma or semicolon separators and known case-insensitive source aliases, trims coordinate/version whitespace, and normalizes sources to canonical codes joined by |. Prefer the canonical pipe form. An empty version after a colon or more than one colon is invalid.
- Model: pass --model and one of cut_off, consequential or apos as two separate argv elements. One model selector applies to the search; do not append a model to a coordinate or invent per-source model flags. If sources need different model choices, use separate searches and keep their provenance distinct.
- Flags: each flag and its value are separate argv elements. --json and --full are standalone flags. Omit optional selectors when no restriction is intended; do not fill them with placeholders or empty source coordinates.

For example, the following JSON is an argv array, not a shell command. Use the verified executable path separately:

```json
["search","Concrete production for use in Switzerland; reference time unspecified","--sources","hiqlcd|hiqlcd-al","--json"]
```

For lookup, the construction is argv = ["lookup", returnedKeys.join(","), "--json"], with returnedKeys populated only from the actual response. If a shell is necessary, quote each complete value with its real shell escaping rules; the pipe remains inside the quoted source value. Do not interpolate raw user input or use environment variables to carry request parameters.

## Inputs

| Command/input | Meaning and limits |
| --- | --- |
| search '<query>' | Required positional natural-language requirement; not --query. Preserve function, treatment, grade, time/region constraints, preferences and unknowns. |
| lookup '<key1,key2>' | 1..200 exact returned keys, comma-separated and deduplicated by CLI. Never construct or decode keys. Dataset results carry key; declaration results carry epd_key. |
| --kind datasets / epd | Domain selector, not a way to expand compiled scope. Keep the same domain for lookup. |
| --json | Machine-readable command output; login progress still goes to stderr. Search/lookup already emit JSON envelopes. |
| --full | All rows/details of this received response. Does not fetch all database records or automatically follow cursors. |
| info --json | Actual program/version and fixed source/publisher declaration. |
| doctor | Local credential presence only; JSON, exit 0 or 2. |
| login --json | One blocking device authorization process; see preparation.md for background ownership and continuation. |
| logout --json | Deletes this product's stored local credential; not needed for routine login or denied numerical access. |

## Background dataset search

### Discover and select sources

1. Read info --json for the program's compiled source codes. This is the supported scope, not the current published catalog or an entitlement check.
2. When selecting a source/version/model, run sources --json, or reuse valid metadata from this task. In the CLI JSON envelope, metadata rows are at data.data: code, versions[].version and versions[].models[].code. Business data.coverage.supported/published/missing reports compiled versus currently published source codes; it is distinct from outer preview coverage. If preview omits versions or models needed for the choice, use sources --json --full before deciding they are absent.
3. Respect a user-specified source/version. Otherwise choose only when the task requires a restriction; omitting --sources searches the complete compiled source set. Do not assume the latest advertised release is appropriate, invent a version, or block an unrestricted search on an optional source choice.
4. Format selected metadata as code or code:version and join with |. For example, hiqlcd|ecoinvent selects both sources without pinning versions. For versioned selection, construct coordinates from the actual returned code and version strings, not literal sourceA/versionA placeholders. Pass a requested, supported --model separately; catalog visibility does not grant numerical access or guarantee matching results.

| Option | Actual behavior |
| --- | --- |
| --sources 'source[:version]' | Restrict supported sources, optionally an advertised version. Join multiple coordinates into one argument using the pipe separator described above. Only codes in this program's scope are allowed. Defaults to its complete embedded source set. |
| --model cut_off / consequential / apos | Actual CLI enum; forwarded as system_model. Omission uses product default. This is not an LCIA method and does not prove returned candidates satisfy the requested model. |
| sources --json | Published metadata: data entries contain code and versions[].version with versions[].models[].code. Read real versions/models rather than assuming the newest is appropriate. The service may advertise model codes not selectable through the three-value --model enum; do not invent extra flags or coerce them. |

There is no background --limit, --cursor or --publishers; these are rejected. There is no dedicated geography flag. Keep geography and other conditions in the complete query and check results for actual evidence.

```bash
environmental-data sources --json
```

```bash
environmental-data search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --json
```

Select a version or model only from the user's requirements and actual metadata; examples do not imply a mandatory default.



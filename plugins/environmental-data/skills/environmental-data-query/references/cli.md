# environmental-data CLI parameters (0.9.1)

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
- Model: pass --model and one of cut_off, consequential, apos or en15804 as two separate argv elements. One model selector applies to the search; do not append a model to a coordinate or invent per-source model flags. If sources need different model choices, use separate searches and keep their provenance distinct.
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
2. When selecting a source/version/model, run sources --json, or reuse valid metadata from this task. In the CLI JSON envelope, metadata rows are at data.data: code, versions[].version and versions[].models[].code. Business data.coverage.supported/published/missing reports compiled versus currently published source codes. If preview omits versions or models needed for the choice, use sources --json --full.
3. Respect a user-specified source/version. Versions must be exact advertised strings such as 3.13.0; a shortened 3.13 is rejected by the service. Otherwise omit --sources to search the complete compiled source set. Do not assume the latest release is appropriate or block an unrestricted search on an optional source choice.

### Search modes

Default search reads the data service directly and returns within about a second. It is lexical metadata retrieval: put the product/process terms (both English and Chinese names help) in the query and use structured filters for source, model and geography. It does not interpret requirements; you judge each candidate. --assist sends the natural-language requirement to the Cortex matching workflow, which interprets conditions and verifies candidates but takes tens of seconds; use it when the user wants requirement interpretation rather than a targeted lookup.

| Option | Actual behavior |
| --- | --- |
| --sources 'source[:version]' | Restrict to compiled sources, optionally an exact advertised version. Join several coordinates with | in one argument. |
| --model cut_off / consequential / apos / en15804 | System model filter. Not an LCIA method. |
| --location 'CN-ECGC,DE' | Direct mode only. Comma-separated location codes as returned in location.id (e.g. CN, CN-ECGC for the East China grid, DE, RER, GLO). Unknown codes match nothing; they never widen the search. |
| --limit 1..100 / --cursor | Direct mode only. Page size (default 20) and the returned page.cursor to continue with otherwise identical arguments. |
| --collapse | Direct mode only. Group results by activity so one row stands for an activity across locations/versions/models. |
| --assist | Use the Cortex matching workflow instead; rejects --location/--limit/--cursor/--collapse (describe those needs in the query). |

```bash
environmental-data search 'electricity low voltage' --sources 'hiqlcd:1.5.0|ecoinvent:3.13.0' --location CN-ECGC --json
```

```bash
environmental-data search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --assist --json
```

## Numerical reads

lci, lcia and methods require this product's login; QUERYING_LCA_DATASETS_API_KEY cannot run them, so unset it and use login. lookup also works with an API key: its headlineGwp follows that key's own entitlements and API quota. For signed-in users, free databases return values for every signed-in user. Commercial values additionally require that an administrator enabled Environmental Data CLI for the account and remain limited to the user's database entitlements; otherwise rows are restricted with reason GRANT_REQUIRED. The grant is issued at login, so after an administrator enables the account the user must run login once more. Each command first verifies the dataset is in this program's scope and echoes dataset identity and webUrl.

| Command | Behavior |
| --- | --- |
| lookup '<key1,key2>' | Details, webUrl, headlineGwp (GWP100 with method and unit) and accessDecision for 1..200 keys. Enough when only a GWP100 value is needed. |
| lci '<key>' | Cumulative elementary-flow inventory of one dataset (not unit-process exchanges). --type input (resources) or output (emissions), --name keyword, --category compartments such as air, --limit 1..200 (default 200), --cursor, --all to read every page serially. |
| methods '<source[:version]>' | LCIA methods/categories/indicators with methodId and unit for one exact version; without a version the latest release is used and echoed. Use the dataset's own version from lookup. --query text, --limit 1..500, --cursor. |
| lcia '<key>' | LCIA results of one dataset; --method full methodId, --method-prefix method segment, --category / --indicator names, --limit 1..200 (default 50), --cursor. The response lists methodIdsWithData. |
| lcia '<key1,key2,...>' | Several datasets in batches with optional --method only; each item keeps its own restricted/error state. |
| lcia '<key>' --contributions --method '<methodId>' | Process-stage contribution buckets (electricity/heat, fuels, materials, transport, direct, ...). Bucketed by design; no unit-process detail. |

Read methods before choosing --method; do not guess methodIds. Avoid unbounded loops: one --all inventory is about ten pages for a large ecoinvent process, and the gateway rate-limits by address (the CLI backs off on 429).



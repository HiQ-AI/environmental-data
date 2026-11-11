# epd-data CLI parameters (0.9.0)

Use the verified executable from preparation for all commands. The examples show its bare name only when that entry is trusted. Command arguments must be passed separately through the host's process tool when possible. If using a shell, quote the complete query and every opaque key/source expression. Never concatenate raw user input into a shell command. Single quotes in the examples work in POSIX and PowerShell for these fixed strings; real apostrophes require the shell's actual escaping rules (PowerShell doubles a single quote; POSIX closes/reopens the quoted string). A literal | must remain inside quotes, not become a pipeline.

## Program scope and domains

- Program: epd-data; protocol: relic-epd.
- Compiled background source codes: none.
- Compiled EPD publisher codes: eco, epditaly, epdnorge.
- Default kind is epd. --kind datasets is outside scope. sources is not an EPD publisher listing and fails for this program.

## Argument format and joining rules

Construct arguments as structured values before execution. The executable path is separate from its argv array; quotation marks belong to shell syntax, not to values passed directly in argv.

- Query: pass the complete natural-language request as the single positional argument after search. Do not use --query, split a sentence into several arguments, URL-encode it or pre-escape it for HTTP; the CLI handles transport encoding.
- Lookup: collect exact epd_key values from actual search results and join them with a comma into one positional argument after lookup. The CLI trims surrounding whitespace, removes empty entries and deduplicates; the resulting list must contain 1..200 keys. Keep each opaque key unchanged: do not decode, rebuild, case-normalize or apply source-coordinate formatting to it.
- Publishers: join actual compiled publisher codes with commas into one --publishers value. These are not source:version coordinates; no source/model discovery command applies to EPD. Pass an actual returned cursor as one --cursor value unchanged.
- Flags: each flag and its value are separate argv elements. --json and --full are standalone flags. Omit optional selectors when no restriction is intended; do not fill them with placeholders or empty source coordinates.

For example, the following JSON is an argv array, not a shell command. Use the verified executable path separately:

```json
["search","Published EPD for concrete used in Switzerland","--publishers","eco,epditaly,epdnorge","--limit","5","--json"]
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


## Published EPD search

| Option | Actual behavior |
| --- | --- |
| --publishers 'codeA,codeB' | Comma-separated subset of the compiled publisher codes above. Omission uses the compiled set. Use real codes, not guessed publisher names. |
| --limit 20 | Integer 1..100, default 20, declarations per page. |
| --cursor '<returned cursor>' | Continue with the actual service cursor and the same query/publishers/limit. Use the returned page structure; no invented page number or total. |

EPD rejects --sources and --model. Published search is public; lookup requires product authentication.

```bash
epd-data search 'Published EPD for concrete used in Switzerland; identify declared unit, validity and A1-A3 method coverage' --limit 5 --json
```

For lookup substitute an actual epd_key; epd is already the default. Do not copy an illustrative placeholder as a real key.


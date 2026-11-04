# usda CLI parameters (0.7.5)

Use the verified executable from preparation for all commands. The examples show its bare name only when that entry is trusted. Command arguments must be passed separately through the host's process tool when possible. If using a shell, quote the complete query and every opaque key/source expression. Never concatenate raw user input into a shell command. Single quotes in the examples work in POSIX and PowerShell for these fixed strings; real apostrophes require the shell's actual escaping rules (PowerShell doubles a single quote; POSIX closes/reopens the quoted string). A literal | must remain inside quotes, not become a pipeline.

## Program scope and domains

- Program: usda; protocol: relic-datasets.
- Compiled background source codes: usda.
- Compiled EPD publisher codes: none.
- Default kind is datasets. --kind epd is outside scope; sources cannot select another database.

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

| Option | Actual behavior |
| --- | --- |
| --sources 'source[:version]' | Restrict supported sources, optionally an advertised version. Multiple coordinates use quoted |, e.g. sourceA:versionA|sourceB:versionB. Only codes in this program's scope are allowed. Defaults to its complete embedded source set. |
| --model cut_off / consequential / apos | Actual CLI enum; forwarded as system_model. Omission uses product default. This is not an LCIA method and does not prove returned candidates satisfy the requested model. |
| sources --json | Published metadata: data entries contain code and versions[].version with versions[].models[].code. Read real versions/models rather than assuming the newest is appropriate. The service may advertise model codes not selectable through the three-value --model enum; do not invent extra flags or coerce them. |

There is no background --limit, --cursor or --publishers; these are rejected. There is no dedicated geography flag. Keep geography and other conditions in the complete query and check results for actual evidence.

```bash
usda sources --json
```

```bash
usda search 'Find construction solid timber, C24 strength class, technically dried and planed, produced for use in Switzerland. Reference year is unspecified. Preserve these requirements and identify unsupported conditions.' --sources 'usda' --json
```

Select a version or model only from the user's requirements and actual metadata; examples do not imply a mandatory default.



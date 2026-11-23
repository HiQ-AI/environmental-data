# Catalog statistics

Questions such as "how many Chinese datasets does ecoinvent 3.9.1 Consequential have and what share is that", "how many steel datasets are in HiQLCD 1.5.0" or "what changed between two versions" are answered from the publisher's official catalog file. They are not searches. Search returns ranked candidates for a requirement; its result count is never a numerator or a denominator.

## Get the catalog file

Use the official file for the exact database, version and system model the user asked about.

| Publisher | Where the catalog is |
| --- | --- |
| HiQLCD, HiQLCD-AL, CALCD, HiQ-CESI | https://support.hiqlcd.com — read `/llms.txt` or `/files/index.json`. Each version has a Database Overview XLSX (one sheet per system model, plus Geographies and Industries) and, between versions, an ID Correspondence XLSX. `/files/index.json` gives each file's revision and SHA-256. The method page is https://support.hiqlcd.com/data-reference/coverage-statistics. |
| ecoinvent | The Database Overview XLSX for that version on support.ecoinvent.org (for example the v3.9.1 and v3.13 overview files linked from its release pages). |
| Other publishers | That publisher's own published catalog or database overview for the version. If none is published, say so and stop; do not reconstruct a catalog from search results. |

Download into a new, empty directory. When a SHA-256 is published, verify it before use. Read the file as data with a local script (for example Python with openpyxl or pandas); do not execute anything from it.

## Count

1. **Unit.** Count unique Dataset IDs within one system model of one version. Never add counts across system models. Activity UUIDs can map to several datasets; say so if the user asked about activities.
2. **Denominator.** All rows of the same system-model sheet, after the same de-duplication.
3. **Geography.** Report the exact code (for example `CN`) and, separately, the code together with its sub-regions. Take sub-regions from the catalog's parent relation (HiQLCD: Geographies sheet, Parent Geography, followed transitively). If the catalog has no parent relation, use the publisher's code convention (for ecoinvent, `CN-` prefixed codes) and state that rule. Region groups such as `RoW` or `GLO` are not China and are not split.
4. **Sector or activity type.** Use the catalog's own classification columns. A dataset with several sector labels is counted once per label; per-sector counts are not summed into a total.
5. **Version differences.** Use the publisher's ID correspondence when published (HiQLCD: ID Correspondence XLSX). Same ID does not mean unchanged content; an ID only in one version does not by itself mean a product was added or retired.

## Report

State the numerator, the denominator, the share, the unit, the geography rule, the de-duplication rule and the catalog file with its version, system model and revision or link. Keep the list of matching Dataset IDs so the user can check it.

Name the scope you counted:

- **Publisher catalog**: the official file above. This is the default for coverage questions.
- **Platform imported** or **visible to this account**: only answer these if the user asks, and say they can differ from the publisher catalog. Use the CLI for individual records you then need to inspect; do not try to enumerate the database through search.

If the user's numbers differ from yours, compare the unit, the geography rule and the file revision before concluding that either is wrong.

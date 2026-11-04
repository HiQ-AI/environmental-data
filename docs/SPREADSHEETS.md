# Spreadsheet requirements

Ordinary Environmental Data queries do not need spreadsheet tooling. When a task's input or requested deliverable is a workbook, use a suitable spreadsheet capability actually available and properly licensed in the current host.

Anthropic's [official XLSX skill](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md) and [license](https://github.com/anthropics/skills/blob/main/skills/xlsx/LICENSE.txt) are references. A URL does not install a skill or grant redistribution rights. This repository does not copy, redistribute, fetch or auto-install that skill.

If the needed capability is missing, state the specific blocked operation and let the user enable an appropriate capability through their host's supported interface. CSV/JSON may suffice for row-based queries, but does not preserve every formula, format or workbook feature. Do not rename CSV to XLSX or claim a workbook was edited when it was not.

Preserve input-row identity, units and unresolved needs. Use only the fields the service needs, rather than uploading a complete workbook automatically. Editing a local workbook is not a remote model edit or import.

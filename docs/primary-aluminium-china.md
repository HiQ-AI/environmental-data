# Primary aluminium production in China

Ask Environmental Data:

> Which datasets are available for primary aluminium production in China?

## Example dataset

A supplied detail-query field excerpt from 27 November 2026 shows **Aluminum,
unwrought, primary** in HiQLCD 1.5.0, Allocation, cut-off. Its location is China
(CN), its reference product is Aluminum, and its reference amount is 1 kg. The
activity type is `PRODUCT_TYPE`. The technology excerpt describes producing
aluminium metal by electrolysis of alumina extracted from bauxite. This is a
production process, not the similarly named market or supply mix.

[Open the production record](https://query.hiq.earth/dataset/hiqlcd/1.5.0/cut_off/b2fd9097-9e03-472e-b276-a906c80de87c/aluminum-unwrought-primary).
The URL identifies the web record; it is not a CLI key.

![Detail-query field excerpt for Aluminum, unwrought, primary, showing China, reference product, amount, model, activity type and technology description](images/primary-aluminium-china-fields.png)

The image is a supplied field excerpt, not raw CLI output. [Open the raw image](https://raw.githubusercontent.com/HiQ-AI/environmental-data/main/docs/images/primary-aluminium-china-fields.png)
or [raw chapter](https://raw.githubusercontent.com/HiQ-AI/environmental-data/main/docs/primary-aluminium-china.md)
if GitHub's HTML view is unavailable.

## CLI 0.9.2 commands

After [installation and login](INSTALLATION.md), replace the executable path in
these examples with the trusted absolute path to your installed CLI. Installation
alone grants no data access. Numerical reads require product login; commercial
databases also require an administrator-enabled CLI grant and the account's
database entitlement. Log in again after the grant is enabled. The
`QUERYING_LCA_DATASETS_API_KEY` cannot be used for numerical reads; unset it and
use product login.

Search HiQLCD 1.5.0 for China using the cut-off model:

```bash
/absolute/path/to/environmental-data search 'aluminum' --sources 'hiqlcd:1.5.0' --model cut_off --location CN --json --full
```

Inspect the `data.data` rows. The default preview shows at most 10 rows per
array, while the default search page contains up to 20; `--full` shows all rows
in the received page. For further pages, add `--cursor 'RETURNED_CURSOR'` using
`data.page.cursor` and keep the same filters and `--full`. Copy a candidate's
complete `datasetRef` unchanged; do not construct a key from the web URL. Use
full lookup to check its name, China location, reference product and amount,
version, model and technology against the production record above; do not select
the market dataset.

The following commands use the production record's actual `datasetRef`. A
lookup in an authorized environment on 27 November 2026 confirmed Aluminum,
unwrought, primary, HiQLCD 1.5.0, cut-off, China and 1 kg.

```bash
/absolute/path/to/environmental-data lookup 'ZDEfYjJmZDkwOTctOWUwMy00NzJlLWIyNzYtYTkwNmM4MGRlODdjHzEuNS4wH0NVVF9PRkY' --json --full
/absolute/path/to/environmental-data lci 'ZDEfYjJmZDkwOTctOWUwMy00NzJlLWIyNzYtYTkwNmM4MGRlODdjHzEuNS4wH0NVVF9PRkY' --json
/absolute/path/to/environmental-data lcia 'ZDEfYjJmZDkwOTctOWUwMy00NzJlLWIyNzYtYTkwNmM4MGRlODdjHzEuNS4wH0NVVF9PRkY' --json
/absolute/path/to/environmental-data trace 'ZDEfYjJmZDkwOTctOWUwMy00NzJlLWIyNzYtYTkwNmM4MGRlODdjHzEuNS4wH0NVVF9PRkY' --direction up --json
```

`lookup --full` includes descriptions omitted by the default preview. `lci`
returns cumulative elementary flows, not unit-process exchanges. The `lci` and
`lcia` examples show a preview of the received page, with at most 10 rows per
array; use `--full` to see that page in full, and the returned cursor with
`--cursor` to request further server pages. `--full` does not fetch those pages.
`trace` returns one layer of suppliers (`up`) or consumers (`down`), with at
most three neighbours ordered by absolute amount. Results depend on the source
and access.

For process-stage contributions, select an actual `methodId` for the dataset's
version from `methods`, or from `methodIdsWithData` in its `lcia` response.
Replace `ACTUAL_METHOD_ID` with that complete value:

```bash
/absolute/path/to/environmental-data methods 'hiqlcd:1.5.0' --json --full
/absolute/path/to/environmental-data lcia 'ZDEfYjJmZDkwOTctOWUwMy00NzJlLWIyNzYtYTkwNmM4MGRlODdjHzEuNS4wH0NVVF9PRkY' --contributions --method 'ACTUAL_METHOD_ID' --json
```

Contributions are process-stage buckets, not unit-process detail. See the
[CLI reference](../plugins/environmental-data/skills/environmental-data-query/references/cli.md)
for pagination, access and other options.

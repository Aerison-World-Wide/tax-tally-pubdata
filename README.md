# tax-tally-pubdata

Public data for **Tax Tally** — the tool that computes late-filing and
late-payment penalties and interest for a taxing authority, every
figure carrying its code section and its computation. It prices
lateness, and shows its work.

This repo is the public data shelf behind the reports. Anyone may
read it; only authorized commits may change it.

## What's here

- `data/matrix.json` — the rate and rule matrix: federal §6621
  quarterly interest rates (2012–2026), monthly AFR, and the penalty
  rules (failure-to-file, failure-to-pay, accuracy, estimated tax,
  information returns, territory rules), each with its code section.
- `data/tips.json` — the "Did you know?" tip pools the statement
  rotates, per jurisdiction (US, PR, GU, VI, CNMI).
- `data/tip-pool.json` — harvested IRS headlines, the source records
  the US tip pool is built from.
- `data/articles.json` — harvested IRS news releases (Oct–Nov 2026).
- `data/disasters.json` — IRS disaster-relief postponements,
  2025–2026.
- `data/social.json` — share-endpoint templates for the tip box
  (X, Facebook, LinkedIn, Email). Edit links here, not in reports.
- `data/webdata.json` — the bundle reports actually fetch: the
  slim matrix, tip pools, payment map, and social templates in one
  file, generated from the Tax Tally source (`python3 report.py
  webdata.json`). Do not hand-edit; regenerate it whenever any of
  the data above changes.

## How reports use this data

Reports fetch `data/webdata.json` from this repo when they load:
a rate correction or a new tip lands in every outstanding report
the next time it is opened online, without regenerating statements.
The same bundle is also baked into each report at render time as
the fallback, so a statement stays one self-contained file that
works fully offline.

## Updating

Data is regenerated from the Tax Tally skill source and pushed by
authorized committers only. Do not hand-edit the JSON: corrections
belong in the source, and matrix corrections cite the IRS page they
were checked against.

Everything here is public information — IRS rates, rules, and
headlines. No client data ever enters this repo.

## License

The data in this repository is licensed under the GNU General
Public License v3.0 — see `LICENSE`. (The underlying IRS rates and
headlines are public information; the license covers the modeled
matrix, the curation, and the collections as assembled here.)

The Tax Tally code that consumes this data lives in the
`tax-tally` repository under the Tax Tally Noncommercial Copyleft
License v1.0.

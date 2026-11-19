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

## How reports use this data

Today the data is baked into each generated report at render time —
a statement is one self-contained file that works offline. Next,
reports will fetch from this repo at runtime, so a rate correction
or a new tip lands everywhere without regenerating statements.
That fetch step is under development.

## Updating

Data is regenerated from the Tax Tally skill source and pushed by
authorized committers only. Do not hand-edit the JSON: corrections
belong in the source, and matrix corrections cite the IRS page they
were checked against.

Everything here is public information — IRS rates, rules, and
headlines. No client data ever enters this repo.

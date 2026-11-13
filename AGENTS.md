# AGENTS.md — care-evals

Type: reference.

This independent repository owns public caregiver evaluation records, validators
and instrument distribution. Global, workspace and [Safety](../../AGENTS.md)
instructions apply.

## Ownership

- `data/*.jsonl` holds public anonymized splits. `data/all.jsonl` is generated
  only by `scripts/project_gold_cases.py`.
- `data/instruments.json` is a byte copy of the assessment projection;
  `instruments-overlay.json` contains Evals-only packaging fields.
- `scripts/validate.py`, `project_gold_cases.py`, `sync_instruments.py` and
  `read_instruments.py` own validation, projection and reads.
- InvisibleBench owns runners, adapters and judge prompts. Assessment owns
  instrument definitions. Benefits and Mira own their respective domains.
- InvisibleBench Private consumes the gold-case projection for private
  evaluation and held-out disjointness checks. The public runner does not
  consume this projection as a private candidate feed.

## Proof

```bash
scripts/check.sh
python3 scripts/validate.py --tools-commit <full-assessment-commit>
```

Use `docs/evidence.md` for every gold-case edit. A reviewed public-safe edit is
human-gated and additive; each split stays at its shipped baseline. Validate
exact assessment projection parity before handoff. Consumers read the generated
case set only through the Git-addressed projection reference.

## Safety

Do not add private conversations, production traces, raw forum text, usernames,
identifying links, private prompts, benefits catalogs or unlicensed instruments.
This repository contains no runner, scoring implementation or live policy system.
Do not present an evaluation as clinical, legal, eligibility or effectiveness
truth. The assessment licensing wall is in
[tools/assessment](../../../tools/assessment/AGENTS.md); report unsafe material
privately through `SECURITY.md`.

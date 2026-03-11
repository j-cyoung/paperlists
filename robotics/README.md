# Robotics 2025 Paperlists

[简体中文说明](./README.zh-CN.md)

This folder documents the bundled 2025 robotics metadata that is now stored in the main `paperlists` tree.

## Files

- [`../ijrr/ijrr2025.json`](../ijrr/ijrr2025.json): 124 IJRR 2025 records
- [`../icra/icra2025.json`](../icra/icra2025.json): 1604 ICRA 2025 records
- [`../iros/iros2025.json`](../iros/iros2025.json): 1985 IROS 2025 records

## Public Sources

- `IJRR 2025`: Crossref journal works endpoint filtered by ISSN `0278-3649` and publication year 2025
- `ICRA 2025`: DBLP proceedings page for exact DOI enumeration, then OpenAlex batch DOI lookup for title, authors, abstract, and landing page, with Crossref fallback when needed
- `IROS 2025`: DBLP proceedings page for exact DOI enumeration, then OpenAlex batch DOI lookup for title, authors, abstract, and landing page, with Crossref fallback when needed

## Normalization Rules

- Output shape follows the existing `paperlists` style: a flat JSON array with fields such as `id`, `title`, `author`, `abstract`, `site`, and `doi`
- `ICRA` and `IROS` use `track="main"` and `status="Published"` because the public sources used here do not expose poster/oral labels in a stable machine-readable form
- `IJRR` uses `track="journal"` and `status="Published"`

## Known Gaps

- `IJRR 2025`: 3 records do not have public abstracts in the upstream metadata
- `ICRA 2025`: 28 records do not have public abstracts in the upstream metadata
- `IROS 2025`: 4 records do not have public abstracts in the upstream metadata

## Regeneration

Run from the project root:

```bash
./scripts/fetch_robotics_2025_metadata.sh
```

Or call the Python entry point directly:

```bash
python ./scripts/fetch_robotics_2025_metadata.py
```

The script first writes generated files under `./store/robotics_2025_metadata_20260311/`, and those reviewed outputs can then be promoted into `./paperlists/...` as needed.

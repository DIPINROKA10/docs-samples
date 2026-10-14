# ASTRA — setup and data pipeline

## Run locally

```bash
git clone https://github.com/DIPINROKA10/astra.git
cd astra
python -m http.server 8080
# open http://localhost:8080
```

There is no build step today. If a bundler is added later, document it here.

## Data pipeline

ASTRA's input is a KSP incident CSV. The Python script converts it into the JSON the dashboard
reads.

```bash
python scripts/clean_records.py \
  --input data/raw/ksp_incidents.csv \
  --output public/data/incidents.json \
  --validate
```

### What the cleaning step does

1. Drops rows with no incident date or no district.
2. Normalises district and crime-type spellings (lookup table in `scripts/districts.json`).
3. Coerces numeric fields and fills missing counts with `0` (never `null`).
4. Writes `public/data/incidents.json` atomically (temp file + rename) so a half-written
   file can never reach the browser.
5. `--validate` re-reads the output and fails the run on schema mismatch.

### Dashboard JSON schema (`public/data/incidents.json`)

| Field | Type | Required | Notes |
|---|---|---|---|
| `id` | string | yes | stable record id |
| `date` | string (ISO-8601) | yes | incident date |
| `district` | string | yes | normalised spelling |
| `crime_type` | string | yes | controlled vocabulary (see list below) |
| `count` | integer | yes | 0+ |
| `lat`, `lon` | number | no | only when available |
| `notes` | string | no | free text, may be empty |

### Crime-type vocabulary

`theft`, `assault`, `fraud`, `cyber`, `traffic`, `other`. New values must be added to both
the cleaning script and this table.

## Known issues

- **Expired live asset path.** The Slate deploy points at hashed asset filenames; a rebuild
  without cache-busting can serve stale JS. Re-deploy (or add `?v=` query params) on change.
- **No automated tests.** A schema check in CI is the first thing to add.
- **Map accessibility.** Hotspots are colour-only; needs an accessible text fallback.

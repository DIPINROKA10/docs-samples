# CarbonTrace — setup, data model and roadmap

## Run locally

```bash
git clone https://github.com/DIPINROKA10/carbontrace.git
cd carbontrace
# No build step today — a single index.html with inline CSS/JS.
python -m http.server 8080
# open http://localhost:8080
```

## Where things live

| File | Responsibility |
|---|---|
| `index.html` | Shell, styles (CSS tokens in `:root`), scripts, Chart.js calls |
| `assets/` | README screenshots only |

The CSS is organised around design tokens (`--green`, `--amber`, `--red`, `--line`, `--r`)
so a non-developer can re-skin the app by editing the `:root` block.

## Data model

Activities are normalised into one record before charting:

```json
{
  "category": "travel | food | energy | other",
  "label": "string",
  "value": "number",
  "unit": "kg CO2e",
  "date": "YYYY-MM-DD"
}
```

### Emission factors (current)

Currently **hardcoded constants** inside `index.html`. Known limitation: no source citation next
to each factor. Planned fix: move them to `factors.json` and document each factor's source
and the date it was looked up.

Example table to ship with the file (illustrative, verify before publishing):

| Activity | Factor (kg CO2e / unit) | Source (to add) |
|---|---|---|
| Petrol car, 1 km | 0.171 (per km) | (add citation) |
| Electricity, 1 kWh | 0.493 (per kWh, India grid avg) | (add citation) |
| Chicken, 1 kg | 6.9 | (add citation) |

## Documentation conventions applied here

- Every factor change must list source + lookup date in a comment.
- New categories must be added to the table above **before** merging code.
- Screenshots named `carbontrace_<view>_<size>.png` and stored in `assets/`.

## Roadmap

- [ ] Extract emission factors to `factors.json` + document the schema (YAML/Markdown).
- [ ] Add a Python script to regenerate an example dataset for demos.
- [ ] Add a one-screen "what each number means" tooltip for non-technical users.
- [ ] Accessibility pass (colour contrast, keyboard nav, alt text on charts).
- [ ] Add a `CHANGELOG.md` and `CONTRIBUTING.md`.

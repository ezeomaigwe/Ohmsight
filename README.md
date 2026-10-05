# Ohmsight

Pre-check and review assist for PV, energy storage and emergency power submittals.

Ohmsight checks key project data against electrical code rules, ranks the likely deficiencies by risk, gives plan reviewers a risk-ranked checklist, and tracks deficiency trends over time.

> Ohmsight flags likely deficiencies. It does not approve plans. Final code determinations rest with the authority having jurisdiction.

## What's in this repository

| File | What it is |
|---|---|
| `index.html` | Business landing page: the problem, how it works, audiences, plans, FAQ and pilot request form |
| `platform.html` | Product and methodology page with the working MVP: pre-check, reviewer view, analytics dashboard and rule library |
| `samples/` | Example projects to load with the MVP's **Upload JSON or CSV** button |

Both pages are static, self-contained HTML. There is no build step and no server code. The MVP runs entirely in the browser; nothing a user enters is sent anywhere.

## MVP scope

- **Input:** key project data entered in a form, or uploaded as JSON or CSV
- **Output:** likely deficiencies ranked by risk, with the calculation and the required fix
- **Reviewer view:** risk-ranked checklist with Deficiency, Cleared and N/A dispositions, notes, and a generated correction list
- **Analytics:** deficiencies per submittal by month and system type, most frequent rules, and share of submittals with critical findings (synthetic demo data)

### Risk model

`Risk = Severity (1-5) x Likelihood (1-5)`

| Band | Score |
|---|---|
| Critical | 20-25 |
| High | 12-19 |
| Medium | 6-11 |
| Low | 1-5 |

Severity runs from S5 (fire, life safety, or loss of emergency power) down to S2 (labeling and documentation). Likelihood is L5 when calculated from submitted values, L4 when a required item is absent, and L3 when a value is within a few percent of a limit.

### Rules (23)

| Group | Rules | Code basis |
|---|---|---|
| General | GEN-01 single-line diagram | NEC 110.3(B) |
| PV | PV-01 to PV-10: max DC voltage, conductor sizing, 120% busbar rule, backfeed breaker, rapid shutdown, supply-side detail, grounding, spec sheets, labels, structural letter | NEC 690, 705 |
| Energy storage | ES-01 to ES-05: UL 9540 listing, per-unit and aggregate kWh limits, location, disconnect | NEC 706, IRC R328, NFPA 855 |
| Emergency and standby | EM-01 to EM-07: generator capacity, transfer time, selective coordination, transfer equipment listing, wiring separation, fuel duration, load calculation | NEC 700, 701, 702 |

Code references default to NEC 2023 article numbers. Confirm them against the edition and local amendments adopted by each jurisdiction.

## Data format for uploads

JSON uses the same shape as the **Copy as JSON** button in the MVP. See `samples/residential-pv-battery.json`.

CSV uses one `key,value` row per field, with dotted keys for nested values:

```csv
key,value
name,Residential PV + battery
occupancy,R-3
hasPV,true
pv.ns,11
pv.voc,49.5
pv.busA,200
```

Any field left out keeps its default.

## Run locally

Open `index.html` in a browser. To serve it so the links between pages behave exactly as they will online:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

**GitHub Pages:** push to GitHub, then go to Settings > Pages, choose "Deploy from a branch", select `main` and `/ (root)`.

**Netlify:** create a new site from the GitHub repo with no build command and the publish directory set to the repo root. The pilot request form on `index.html` is already marked up for Netlify Forms, so submissions appear under the site's Forms tab after the first deploy. On GitHub Pages the form has nowhere to send, so connect a form service or replace it with a contact email.

## Roadmap

1. **MVP (now):** browser rule engine, form and file input, risk-ranked output, reviewer checklist, demo analytics
2. **Python service:** rules ported to a tested Python package, FastAPI endpoint, disposition history in a database, export to Power BI or the web dashboard, assisted extraction from equipment spec sheets
3. **Pilot:** jurisdiction rule overlays, code edition switching, pilot with plan reviewers, measured change in correction cycles and review time

## Contact

Project lead: Ezeoma Igwe, electrical engineer.

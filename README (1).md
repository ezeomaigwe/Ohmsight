# Ohmsight

Pre-check and review assist for PV, energy storage and emergency power submittals.

Ohmsight ranks electrical design deficiencies by severity and frequency, runs a pre-check on key project data, and gives plan reviewers a risk-ranked checklist with a correction list.

> Ohmsight flags likely deficiencies. It does not approve plans. Final code determinations rest with the authority having jurisdiction.

## What's in this repository

| File | What it is |
|---|---|
| `index.html` | Business landing page: the problem, how it works, audiences, plans, FAQ and pilot request form |
| `platform.html` | The Ohmsight app: About, Pre-check, Review checklist, Taxonomy, Risk model and Method sheets |
| `samples/` | Example projects to load with the app's **Upload JSON or CSV** button |

Both pages are static, self-contained HTML. There is no build step and no server code. The app runs entirely in the browser; nothing a user enters is sent anywhere.

## App sheets

| Sheet | What it does |
|---|---|
| E-0 About | The problem, who it serves, and how the model works |
| E-1 Pre-check | Enter key project data or upload JSON or CSV; likely deficiencies ranked by risk, with the calculation and the fix |
| E-2 Review checklist | Ranked checklist for the project type; record deficiency, cleared or not applicable, then copy the correction list |
| E-3 Taxonomy | 60 known deficiencies across 7 systems, each mapped to code sections |
| E-4 Risk model | Severity x frequency risk matrix and breakdown by system |
| E-5 Method | How severity and frequency are scored, with sources |

Each sheet can be opened directly with a link such as `platform.html#precheck` or `platform.html#taxonomy`.

Code references follow NEC 2023. Confirm them against the edition and local amendments adopted by each jurisdiction.

## Data format for uploads

JSON uses the same shape as the **Copy as JSON** button in the app. See `samples/residential-pv-battery.json`.

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

1. **Now:** deficiency taxonomy and risk model, browser pre-check, form and file input, reviewer checklist and correction list
2. **Python service:** rules ported to a tested Python package, FastAPI endpoint, disposition history in a database, export to Power BI or the web dashboard, assisted extraction from equipment spec sheets
3. **Pilot:** jurisdiction rule overlays, code edition switching, pilot with plan reviewers, measured change in correction cycles and review time

## Contact

Project lead: Ezeoma Igwe, electrical engineer.

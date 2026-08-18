# Milk Run WebGIS Demo

A browser-based demonstration for optimizing inbound automotive-parts pickup operations. 

## Live Demo

After GitHub Pages deployment, the application will be available at:

https://lwb951228.github.io/Milk-Run-WebGIS/

## Features

- Map-based editing of the plant and suppliers, including demand and pickup time windows.
- CSV import for supplier coordinates, weight, volume, time windows, and service time.
- Browser-side route generation with weight, volume, and operating-time constraints.
- Route details covering vehicle assignments, stop sequences, arrival and departure times, distance, workload, cost, and load rate.
- KPI comparison, overall plan scoring, and diagnostics for time-window, capacity, and work-time violations.
- Offline Chongqing road-network visualization and bilingual Chinese-English interface.

## Local Development

```bash
npm install
npm run dev
```

Open the local URL printed by Vite, typically `http://localhost:5173`.

## Production Build

```bash
npm run build -- --base=/Milk-Run-WebGIS/
```

## CSV Schema

```text
id,name,lat,lng,demandKg,demandM3,windowStart,windowEnd,serviceMin
```

- `lat`, `lng`: WGS84 coordinates.
- `demandKg`: pickup demand in kilograms.
- `demandM3`: pickup demand in cubic metres.
- `windowStart`, `windowEnd`: pickup window in `HH:mm` format.
- `serviceMin`: on-site service duration in minutes.

See `sample-suppliers.csv` for an example.

## Deployment

The repository includes a GitHub Actions workflow at `.github/workflows/deploy-pages.yml`. In the repository settings, set **Pages → Build and deployment → Source** to **GitHub Actions**.

## Technical Note

The current solver is a front-end heuristic intended for research communication and demonstration. A production implementation can replace it with an asynchronous optimization API incorporating GA, ALNS, NSGA-II, rolling-horizon optimization, and an enterprise road-distance matrix.

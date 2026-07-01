# MPI — Market Potential Index (Phase 1)

Buying‑power‑adjusted sales‑potential index comparing **10 South‑East Europe markets** across **9 appliance/electronics categories** (+2 premium subsets), built so relative **targets** and **actual sales** can be evaluated fairly against potential — and offices/countries compared regardless of size or wealth.

## Open it

**Double‑click `index.html`.** It's a single self‑contained file — no install, no server, no internet required (works behind a corporate proxy / offline). Live at **https://mpi.er45.com**.

## What's in the folder

| File | What it is |
|---|---|
| `index.html` | The interactive dashboard — open this (also served at the site root). |
| `MPI_Methodology.md` | How the index is built: model, parameters, data sources, limitations, Phase‑2 roadmap. |
| `data/mpi_country_inputs.csv` | Editable country inputs (population, household size, AIC, price level, urbanisation, climate, tourism). |
| `data/mpi_category_parameters.csv` | Editable category parameters (income elasticity β, climate/tourism/urban weights, ASP, scope market size). |

The dashboard's **Assumptions tab** holds the same inputs as live‑editable tables — change any number and everything recomputes instantly. The CSVs are for editing in Excel / sharing; to load changes, update the corresponding `COUNTRIES` / `CATS` block at the top of the `<script>` in the HTML (clearly commented), or edit inline in the Assumptions tab.

## The six tabs

1. **Overview** — country × category intensity heatmap + composite share & intensity rankings.
2. **Category deep‑dive** — per‑category share bars, buying‑power‑vs‑intensity scatter, and the **final table** with a per‑driver transparency block (×Income, ×Climate, ×Tour, ×Urban, ×Share).
3. **Country profiles** — radar of category strengths + full per‑category table for one country.
4. **Authority matrix** — editable country × category mandate grid (1 = full authority, 0 = out of scope). Produces a **strategy‑weighted composite** kept separate from the neutral demand model, and can drive the target split.
5. **Targets & performance** — split a scope target by potential (optionally weighted by authority); paste actuals to score **Perf‑abs** (non‑zero‑sum) and **Perf‑rel**.
6. **Assumptions & method** — editable inputs, methodology, data sources, Phase‑2 roadmap.

Top‑right: toggle **Value (€) / Volume (units)** and **Export master CSV**.

## Three numbers to know

- **Potential share %** → how to split a target.
- **Intensity index** (per household, scope avg = 100) → is a household here worth more/less than the regional average? The fair‑comparison metric.
- **Perf‑abs** (actual ÷ own potential, 100 = at potential) → the headline performance score for cross‑office comparison.

## Status

Phase 1 ships with **indicative real data** (Eurostat 2024 first estimates + 2021–24 censuses + World Bank/EEA), validated by a multi‑expert review (econometric, appliance‑industry, BI). Each country has a **data‑confidence badge**; small/low‑confidence markets are flagged **"thin"** in performance. Replace the data with your internal panels, sell‑out and ASP, and plug in the **product‑authority matrix** and **RPI** in Phase 2 (see `MPI_Methodology.md`).

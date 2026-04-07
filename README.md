# EPA Automotive Trends — Interactive Visualization

An interactive Altair dashboard exploring how new light-duty vehicles in the U.S. have evolved since model year 2010 — across fuel economy, CO₂ emissions, horsepower, and weight. The repo also contains a companion Power BI case study that re-analyzes the same EPA data in a second tool.

## Overview

The U.S. EPA publishes an annual *Automotive Trends Report* tracking fuel economy and emissions for new vehicles sold in the United States. This project takes the manufacturer- and vehicle-type-level slices of that data (model years 2010 and later) and turns them into a linked, interactive dashboard so the user can:

- Compare manufacturers across fuel economy, CO₂, horsepower, and weight
- See how vehicle classes (cars, SUVs, trucks) have shifted year over year
- Spot the trade-offs between performance (HP, weight) and efficiency (MPG, CO₂)

## Dataset

Source: [EPA Automotive Trends Report](https://www.epa.gov/automotive-trends).

| File | Description |
|---|---|
| `data/raw/manufacturer_epa.csv` | Per-manufacturer fuel economy, CO₂ emissions, and performance metrics |
| `data/raw/vehicle_type_epa.csv` | Same metrics aggregated by vehicle class (car, SUV, pickup, etc.) |

Both files are filtered to model years 2010 onward.

## Project structure

```
epa-automotive-trends-viz/
├── analysis/                     # Jupyter notebook with the Altair dashboard
│   └── Interactive Visualization of EPA Data.ipynb
├── data/
│   └── raw/                      # Source CSVs from the EPA report
│       ├── manufacturer_epa.csv
│       └── vehicle_type_epa.csv
├── outputs/                      # Rendered dashboard exports
│   ├── html/
│   │   └── Interactive Visualization of EPA Data.html
│   └── pdf/
│       └── Interactive Visualization of EPA Data.pdf
├── wesco-bi-case-study/          # Companion Power BI case study (see below)
│   ├── case-study.pbix
│   ├── background-images/
│   ├── reference-datasets/
│   └── reference-reports/
├── docs/                         # Assignment brief / reference material
│   └── Assignment 3 - Instructions.pdf
├── .gitignore
└── README.md
```

## Key visualizations

- **Fuel economy trends** — MPG by manufacturer and vehicle class over time
- **Emissions vs. efficiency** — CO₂ g/mi plotted against MPG with manufacturer encoding
- **Performance vs. weight** — horsepower and curb weight trade-offs by class
- **Linked selections** — brushing one chart filters the others, enabling interactive exploration

## How to run

Requires Python 3.9+ and Jupyter.

```bash
pip install pandas altair notebook
jupyter notebook "analysis/Interactive Visualization of EPA Data.ipynb"
```

Run the cells top-to-bottom to render the dashboard inline.

> **Note:** the notebook loads the CSVs by bare filename. When running from `analysis/`, either launch Jupyter from `data/raw/` or update the path strings to `../data/raw/manufacturer_epa.csv`.

## Outputs

Pre-rendered exports of the dashboard live under `outputs/`:

- HTML (interactive): [`outputs/html/Interactive Visualization of EPA Data.html`](outputs/html/Interactive%20Visualization%20of%20EPA%20Data.html)
- PDF (static): [`outputs/pdf/Interactive Visualization of EPA Data.pdf`](outputs/pdf/Interactive%20Visualization%20of%20EPA%20Data.pdf)

## Companion Power BI case study

The `wesco-bi-case-study/` folder contains a Power BI re-analysis of the same EPA data, built as a standalone BI case study. It covers the same questions as the Altair notebook but uses Power BI's visual and interaction model instead of Vega-Lite.

**Report pages (`case-study.pbix`):**

1. **Overview** — landing page with EPA branding and navigation
2. **Heatmap** — correlation heatmap across the full metric set
3. **Emissions & Weight** — CO₂ emissions vs. vehicle weight and model year
4. **Fuel Economy & Weight** — MPG vs. vehicle weight, including MPG-by-weight-bin breakdowns
5. **Fuel Economy & Performance** — real-world MPG vs. horsepower trade-offs
6. **Manufacturer Comparison** — side-by-side manufacturer metrics

**Notable visuals:** correlation heatmap, CO₂ vs. MPG scatter, CO₂ vs. model year trend, MPG vs. vehicle weight scatter, MPG by weight bins, real-world MPG vs. horsepower. Uses the TableHeatMap and Box-and-Whisker (MAQ) custom visuals from AppSource.

**Contents:**

| Path | Description |
|---|---|
| `case-study.pbix` | The Power BI report file |
| `reference-datasets/epa-manufacturer.csv` | Manufacturer-level EPA data (same source as the notebook) |
| `reference-datasets/epa-vehicle-type.csv` | Vehicle-type-level EPA data |
| `reference-datasets/correlation-matrix.xlsx` | Pre-computed correlation matrix used by the heatmap page |
| `reference-reports/epa-interactive-visualization.html` | HTML export of the Altair notebook, kept alongside for cross-reference |
| `reference-reports/epa-interactive-visualization.pdf` | PDF export of the same |
| `background-images/` | Page backgrounds (EPA seal + stock photography) |

**To open:** requires Power BI Desktop (Windows). Open `case-study.pbix` and refresh data sources if prompted.

## Tech stack

- **Python** — pandas for data wrangling
- **Altair** — declarative, interactive visualization (Vega-Lite)
- **Jupyter Notebook** — analysis environment
- **Power BI Desktop** — companion case study report

## Author

**Zainulabidin Adhami**

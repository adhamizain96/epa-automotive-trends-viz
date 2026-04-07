# EPA Automotive Trends — Interactive Visualization

An interactive Altair dashboard exploring how new light-duty vehicles in the U.S. have evolved since model year 2010 — across fuel economy, CO₂ emissions, horsepower, and weight.

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
├── analysis/                # Jupyter notebook with the Altair dashboard
│   └── Interactive Visualization of EPA Data.ipynb
├── data/
│   └── raw/                 # Source CSVs from the EPA report
│       ├── manufacturer_epa.csv
│       └── vehicle_type_epa.csv
├── outputs/                 # Rendered dashboard exports
│   ├── html/
│   │   └── Interactive Visualization of EPA Data.html
│   └── pdf/
│       └── Interactive Visualization of EPA Data.pdf
├── docs/                    # Assignment brief / reference material
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

> **Note:** the notebook loads the CSVs by bare filename (`manufacturter_epa.csv`). When running from `analysis/`, either launch Jupyter from `data/raw/` or update the path strings to `../data/raw/manufacturer_epa.csv`.

## Outputs

Pre-rendered exports of the dashboard live under `outputs/`:

- HTML (interactive): [`outputs/html/Interactive Visualization of EPA Data.html`](outputs/html/Interactive%20Visualization%20of%20EPA%20Data.html)
- PDF (static): [`outputs/pdf/Interactive Visualization of EPA Data.pdf`](outputs/pdf/Interactive%20Visualization%20of%20EPA%20Data.pdf)

## Tech stack

- **Python** — pandas for data wrangling
- **Altair** — declarative, interactive visualization (Vega-Lite)
- **Jupyter Notebook** — analysis environment

## Author

Zainulabidin Adhami

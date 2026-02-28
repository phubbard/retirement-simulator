# Retirement Financial Planner

A comprehensive, interactive retirement planning tool that runs entirely in your browser. Uses Monte Carlo simulation to model thousands of possible futures for your finances, with support for disability scenarios, California Prop 13 property tax, multiple retirement account types, and relocation analysis.

## Privacy

**Your financial data never leaves your browser.** There is no server, no database, no analytics, no tracking, and no cookies beyond `localStorage` on your own machine. The only outbound network request is loading Chart.js from a CDN. You can verify this by opening your browser's Network tab.

## Features

- **Monte Carlo Simulation** — configurable from 100 to 50,000 runs with seeded PRNG for reproducibility
- **Fat-tail crash modeling** — configurable probability, severity, duration, and recovery dynamics
- **Historical data** — bundled VFINX returns (1976-2024), CPI-U, PCE deflator, and Bloomberg Aggregate bond returns from FRED
- **Multiple account types** — 403(b), 457(b), DCP (deferred compensation), Roth IRA, taxable brokerage, HSA
- **Smart withdrawal ordering** — 457(b) first (no 10% early penalty), then DCP, taxable, traditional, HSA, Roth last
- **California Prop 13** — 2% annual cap on assessed value increases, Mello-Roos, local overrides
- **Disability scenario** — LTD income modeling, SSDI with 5-month waiting period, Medicare after 24 months, RSU vesting control
- **ESPP** — IRC Section 423 modeling with discount and $25k annual limit
- **Relocation analysis** — compare staying vs. moving to another state/city with full COL adjustment, state tax comparison, home sale capital gains exclusion, and move-year optimizer
- **Tax engine** — 2025 federal brackets (MFJ/Single), California 10-bracket system with mental health surcharge, plus Oregon, Arizona, and no-income-tax state modeling
- **Expense planning** — monthly, annual, recurring (e.g., "new car every 8 years"), one-time, and healthcare with separate inflation rates
- **Glide path allocation** — automatic equity reduction through retirement
- **Dynamic guardrail withdrawal strategy**
- **CSV export** — full monthly/annual detail with 40+ columns per scenario
- **Print to PDF** — clean light-theme layout with chart color swapping
- **Auto-save** — all inputs persist in localStorage with debounced writes

## Tech Stack

Single self-contained HTML file. No build step, no framework, no dependencies beyond Chart.js (loaded from CDN).

- HTML/CSS/JavaScript (vanilla)
- [Chart.js 4.4](https://www.chartjs.org/) for visualization
- `localStorage` for persistence

## Usage

Open `index.html` in any modern browser. That's it.

Or visit the hosted version (if deployed).

## Data Sources

- **VFINX total returns** (1976-2024): Vanguard 500 Index Fund
- **CPI-U inflation** (1976-2024): Bureau of Labor Statistics via FRED (CPIAUCSL)
- **PCE deflator** (1976-2024): Bureau of Economic Analysis via FRED (PCEPI)
- **Bond returns** (1976-2024): Bloomberg US Aggregate Bond Index proxy
- **Cost-of-living indices**: BLS Regional Price Parities and C2ER Cost of Living Index
- **State tax brackets**: 2025 published rates for CA, OR, AZ, WA (LTCG), NV, TX, FL

## License

Copyright 2026 Paul Hubbard. All rights reserved.

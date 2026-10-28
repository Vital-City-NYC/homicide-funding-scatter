# Methodology: homicide change vs. funding and pandemic surge

## Data

Analysis by Ethan Doshi (University of Pennsylvania), from his working paper "COVID-19 fiscal recovery funding and the American homicide decline" (CrimRxiv, 2026): https://www.crimrxiv.com/pub/bmqcnp64/release/5. His inputs:

- Funding: U.S. Treasury, Coronavirus State and Local Fiscal Recovery Funds, Project and Expenditure Report public data, January 2022 to April 2025 releases: https://home.treasury.gov/policy-issues/coronavirus/assistance-for-state-local-and-tribal-governments/state-and-local-fiscal-recovery-funds/public-data. Metropolitan cities' awards were set by Treasury's allocation formula: https://home.treasury.gov/system/files/136/Allocation-Methodology-for-MetropolitanCities-508A.pdf
- Homicides: Jacob Kaplan's concatenated FBI Uniform Crime Reporting files (Return A), 1960-2024, openICPSR project 100707: https://www.openicpsr.org/openicpsr/project/100707

`data.csv` is exported unchanged from `scatterplot_data.xlsx` (sheet "Scatterplot data"), supplied by the author in October 2026. It covers the 453 cities with complete homicide reporting in 2019, 2021 and 2024, in 39 states, with no missing values and no duplicate city-state pairs.

| Column | Meaning |
|---|---|
| `funding_vs_similar_pct` | The city's American Rescue Plan recovery award above or below what demographically similar cities in the same state received, in percent (left panel, x-axis) |
| `homicide_rate_change_2019_2021` | Change in homicides per 100,000 residents, 2019-2021 (right panel, x-axis) |
| `homicide_rate_change_2021_2024` | Change in homicides per 100,000 residents, 2021-2024 (y-axis, both panels) |

How peer cities were matched is described in the working paper; the chart uses the author's computed comparison as given.

## Trend lines

Each panel's line is an ordinary least-squares fit of the 2021-2024 change on the panel's x variable, computed in the page from `data.csv`. The shaded band is the 95% confidence interval for the fitted mean (t = 1.9652, 451 degrees of freedom).

The fits were recomputed independently and match the workbook's "Fitted lines" sheet:

| Panel | Intercept | Slope | R-squared |
|---|---|---|---|
| Funding | -1.748 | -0.0002 (standard error 0.0091) | 0.000 |
| 2019-2021 rise | -0.353 | -0.6471 (standard error 0.0336) | 0.451 |

## Chart choices

- Both panels share one y-axis scale so the spread is comparable.
- The y-axis runs from below zero to above it and marks zero, so no zero-baseline toggle is needed.
- Gridlines are horizontal only; the vertical line at x = 0 is a reference line (funding equal to peers; no 2019-2021 change).
- Trenton, Rochester and Broomfield are labeled by default as the extreme points. Hovering or tapping any dot shows its values and marks the same city in the other panel.

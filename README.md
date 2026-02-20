# Structural Transformation of India's Wearing Apparel Manufacturing Sector (NIC Division 14, 1973--2024)

## Overview

This repository contains the data, analysis code, and supporting files for an empirical study of India's wearing apparel manufacturing sector (NIC Division 14) spanning five decades (1973--2024). The analysis uses industry-level data from the Annual Survey of Industries (ASI) accessed via the EPWRF India Time Series database, supplemented with official price deflators and international trade statistics.

The study examines long-run growth trajectories, structural breaks, productivity dynamics (including TFP decomposition), employment patterns, wage distribution, regional convergence, export performance, and policy impacts across five distinct industrial eras.

## Repository Structure

### Analysis

| File | Description |
|------|-------------|
| `nic14_analysis.ipynb` | Main Jupyter notebook containing all empirical analysis: data cleaning, deflation, era periodisation, CAGR computation, structural break detection (PELT/Bai-Perron), growth accounting, TFP decomposition, convergence regressions, spatial concentration indices, and all figure/table generation |

### ASI Data Files (EPWRF India Time Series)

These are Annual Survey of Industries datasets for NIC 2-digit Division 14 (Manufacture of Wearing Apparel), extracted from different subsections of the ASI tables available on the EPWRF India Time Series platform. Each pair consists of a `.csv` file containing the wide-format panel data and a `.json` file containing variable metadata and series descriptions.

| File | Description |
|------|-------------|
| `sub02_nic14_wide.csv` | **ASI Subsection 2 (All-India level)**: Principal characteristics of NIC Division 14 at the all-India aggregate level (output, GVA, fixed capital, employment, wages, inputs, etc.) |
| `sub02_nic14_meta.json` | Variable metadata and series descriptions for the Subsection 2 extract |
| `sub07_nic14_wide.csv` | **ASI Subsection 7 (State-level)**: Principal characteristics of NIC Division 14 disaggregated by state/union territory, used for regional analysis, convergence regressions, and spatial concentration indices |
| `sub07_nic14_meta.json` | Variable metadata and series descriptions for the Subsection 7 extract |
| `sub10_nic14_wide.csv` | **ASI Subsection 10 (Employment characteristics)**: Detailed employment data for NIC Division 14 including worker categories, contract workers, women workers, supervisory and managerial staff, and person-days worked |
| `sub10_nic14_meta.json` | Variable metadata and series descriptions for the Subsection 10 extract |

### Price Deflators

| File | Description |
|------|-------------|
| `nic_14_wpi_linked_series.csv` | Linked Wholesale Price Index (WPI) series for NIC Division 14, used to deflate output and material inputs to constant prices |
| `cpi_iw_linked_1960_to_2016base.csv` | Linked Consumer Price Index for Industrial Workers (CPI-IW), rebased to 2016, used to deflate wages and emoluments to real terms |
| `wpi_machinery_and_equipment.xls` | WPI series for Machinery and Equipment, used as the capital goods deflator for constructing real fixed capital stock via the Perpetual Inventory Method |
| `GFCF at Current and Constant Price to get IDP....` | Gross Fixed Capital Formation data at current and constant prices, used to derive the Implicit Deflator for Plant and Machinery investment |

### Trade Data (UN Comtrade)

International merchandise trade data for wearing apparel, sourced from the **United Nations Comtrade** database. Data covers India's apparel exports and imports classified under relevant HS chapters (primarily HS 61 and HS 62).

| File | Description |
|------|-------------|
| `TradeData 1990-2001.csv` | India's apparel export and import data from UN Comtrade (1990--2001) |
| `TradeData 2002-13.csv` | India's apparel export and import data from UN Comtrade (2002--2013) |
| `TradeData 2014-25.csv` | India's apparel export and import data from UN Comtrade (2014--2025), including RMG export values used to compute export intensity ratios |

## Key Variables in ASI Data

The ASI datasets contain (among others) the following variables critical to the analysis:

- **Output and value added**: gross output, total inputs, gross value added (GVA), net value added (NVA)
- **Capital**: fixed capital stock, invested capital, additions to fixed assets, depreciation
- **Labour**: total persons engaged, workers (production), supervisory and managerial staff, contract workers, women workers
- **Wages**: total emoluments, wages to workers, salaries to supervisory staff
- **Materials**: total input costs, fuels consumed
- **Factory count**: number of factories in operation

## Methodology Highlights

- **Deflation**: Dual-deflator method (WPI for output/materials, CPI-IW for wages, machinery WPI for capital stock) with linked series ensuring consistent real values across base-year revisions
- **Era periodisation**: Five eras identified via PELT change-point detection algorithm and validated against known policy events (de-reservation 2001, MFA phase-out 2005, GST 2017, COVID 2020)
- **Growth accounting**: Solow residual TFP decomposition with labour share calibrated from ASI data
- **Convergence**: Cross-sectional beta-convergence and sigma-convergence regressions across Indian states, with leave-one-out robustness checks
- **Spatial concentration**: CR4, Herfindahl-Hirschman Index (HHI), and Gini coefficient computed from state-level GVA shares

## Data Sources

| Source | Description |
|--------|-------------|
| **EPWRF India Time Series** ([epwrfits.in](https://www.epwrfits.in)) | Structured access to Annual Survey of Industries (ASI) data published by the Ministry of Statistics and Programme Implementation (MoSPI), Government of India |
| **UN Comtrade** ([comtrade.un.org](https://comtrade.un.org)) | International merchandise trade statistics; apparel exports/imports under HS Chapters 61 and 62 |
| **Office of the Economic Adviser, DPIIT** | Wholesale Price Index series for manufactured products and machinery |
| **Labour Bureau, Ministry of Labour** | Consumer Price Index for Industrial Workers (CPI-IW) |
| **MoSPI, National Accounts Division** | Gross Fixed Capital Formation at current and constant prices for implicit deflator derivation |

## Requirements

The analysis notebook requires the following Python environment:

- Python 3.9+
- `pandas`, `numpy` for data manipulation
- `matplotlib`, `seaborn` for visualisation
- `scipy`, `statsmodels` for statistical tests and regressions
- `ruptures` for PELT change-point detection
- `scikit-learn` for clustering (if applicable)

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels ruptures scikit-learn
```

## Citation

If using this data or analysis, please cite:

> Structural Transformation of India's Wearing Apparel Manufacturing Sector (NIC Division 14, 1973--2024). Term paper, 2026. Data sourced from EPWRF India Time Series (ASI), MoSPI, Government of India; UN Comtrade.

## License

This repository is for academic and research purposes. The underlying ASI data are published by the Government of India and subject to MoSPI's terms of use. Trade data are from the United Nations Comtrade database and subject to UN data usage terms.

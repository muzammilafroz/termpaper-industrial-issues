# Structural Transformation of India's Wearing Apparel Manufacturing Sector (NIC Division 14, 1973--2024)

## Overview

This repository contains the data, analysis code, and supporting files for an empirical study of India's wearing apparel manufacturing sector (NIC Division 14) spanning five decades (1973--2024). The analysis uses plant-level data from the Annual Survey of Industries (ASI) accessed via the EPWRF India Time Series database, supplemented with official price deflators and trade statistics.

The study examines long-run growth trajectories, structural breaks, productivity dynamics (including TFP decomposition), employment patterns, wage distribution, regional convergence, export performance, and policy impacts across five distinct industrial eras.

## Repository Structure

### Analysis

| File | Description |
|------|-------------|
| `nic14_analysis.ipynb` | Main Jupyter notebook containing all empirical analysis: data cleaning, deflation, era periodisation, CAGR computation, structural break detection (PELT/Bai-Perron), growth accounting, TFP decomposition, convergence regressions, spatial concentration indices, and all figure/table generation |

### ASI Data Files (EPWRF India Time Series)

These are the core Annual Survey of Industries datasets for NIC Division 14, extracted at three different NIC classification revisions. Each `.csv` contains the wide-format panel data and each `.json` contains variable metadata.

| File | Description |
|------|-------------|
| `sub02_nic14_wide.csv` | ASI data under NIC-1998 classification (covers approximately 1998--2007) |
| `sub02_nic14_meta.json` | Variable metadata for the NIC-1998 extract |
| `sub07_nic14_wide.csv` | ASI data under NIC-2004 classification (covers approximately 2004--2013) |
| `sub07_nic14_meta.json` | Variable metadata for the NIC-2004 extract |
| `sub10_nic14_wide.csv` | ASI data under NIC-2008 classification (covers approximately 2008--2024) |
| `sub10_nic14_meta.json` | Variable metadata for the NIC-2008 extract |

### Price Deflators

| File | Description |
|------|-------------|
| `nic_14_wpi_linked_series.csv` | Linked Wholesale Price Index (WPI) series for NIC Division 14, used to deflate output and material inputs to constant prices |
| `cpi_iw_linked_1960_to_2016base.csv` | Linked Consumer Price Index for Industrial Workers (CPI-IW), rebased to 2016, used to deflate wages and emoluments to real terms |
| `wpi_machinery_and_equipment.xls` | WPI series for Machinery and Equipment, used as the capital goods deflator for constructing real fixed capital stock via the Perpetual Inventory Method |
| `GFCF at Current and Constant Price to get IDP....` | Gross Fixed Capital Formation data at current and constant prices, used to derive the Implicit Deflator for Plant & Machinery investment |

### Trade Data

| File | Description |
|------|-------------|
| `TradeData 1990-2001.csv` | India's apparel export and import data (1990--2001) |
| `TradeData 2002-13.csv` | India's apparel export and import data (2002--2013) |
| `TradeData 2014-25.csv` | India's apparel export and import data (2014--2025) |
_sourced from UNCOMTRADE trade statistics_ 

## Key Variables in ASI Data

The ASI panel datasets contain (among others) the following variables critical to the analysis:

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

## Data Source and Access

All ASI data were accessed through the **EPWRF India Time Series** platform ([https://www.epwrfits.in](https://www.epwrfits.in)), which provides structured access to Annual Survey of Industries microdata published by the Ministry of Statistics and Programme Implementation (MoSPI), Government of India.

Trade data were compiled from the Directorate General of Commercial Intelligence and Statistics (DGCIS) and the Apparel Export Promotion Council (AEPC) annual reports.

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

> Structural Transformation of India's Wearing Apparel Manufacturing Sector (NIC Division 14, 1973--2024). S.M. Muzammil Afroz, Term paper, Centre For Development Studies, 2026. Data sourced from EPWRF India Time Series (ASI), MoSPI, Government of India.

## License

This repository is for academic and research purposes. The underlying ASI data are published by the Government of India and subject to MoSPI's terms of use. Trade data are from official government publications.

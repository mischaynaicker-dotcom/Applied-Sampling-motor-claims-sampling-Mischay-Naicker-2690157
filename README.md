# Estimating the Mean Motor Insurance Claim: Stratified Sampling with Neyman Allocation

**Mischay Naicker (2690157)**
STAT4102A Applied  Sampling, Mini Project, Semester Two 2026
University of the Witwatersrand, School of Statistics and Actuarial Science

## Overview

This project estimates the mean claim amount for a motor insurer's portfolio using **stratified random sampling with Neyman allocation**, with **SRSWOR** as the benchmark.

- **Population:** a simulated finite population of 10,000 motor own-damage claims (one insurer, Gauteng, 2026 claim year).
- **Strata (cause of loss):** pothole/road, weather/hail, accident and theft. Claim amounts are lognormal within each stratum.
- **Parameter:** the finite-population mean claim.
- **Precision target:** a 95% confidence interval with a half-width of at most 5% of the baseline mean.
- **Evaluation:** one realised sample analysed with the `survey` package, then 1,000 Monte Carlo repetitions comparing the two designs on bias, RMSE, coverage and interval width.

## Files

| File | Description |
|---|---|
| `Mischay_Naicker_2690157_Applied_Sampling_Project.Rmd` | Full report and reproducible code (Sections A to E) |
| `Mischay_Naicker_2690157_Applied_Sampling_Project.pdf` | Knitted report |
| `population.csv` | Full finite population (10,000 claims): `claim_id`, `stratum`, `claim_amount`, `claimant_age`, `vehicle_age`, `vehicle_value`, `area` |
| `sample.csv` | Realised stratified sample: the same variables plus `stratum_id`, `N_h`, `n_h`, `pi` (inclusion probability) and `weight` (sampling weight) |

## How to run

**Packages used:** `survey`, `ggplot2`, `knitr` and `rmarkdown` (install with `install.packages(c("survey", "ggplot2", "knitr", "rmarkdown"))`).

**To run:** open `Mischay_Naicker_2690157_Applied_Sampling_Project.Rmd` in RStudio and click **Knit**. This runs all the code, saves `population.csv` and `sample.csv` in the same folder, and produces the report. Knitting to PDF needs a LaTeX installation such as TinyTeX.

The results are reproducible because every random step uses a fixed seed.

## Random seeds

| Seed | Used for |
|---|---|
| 4102 | Generating the population |
| 2026 | Drawing the stratified sample |
| 7 | Drawing the SRSWOR benchmark sample |
| 2027 | The 1,000 Monte Carlo repetitions |

## Report structure

| Section | Content |
|---|---|
| Notation | Symbols used throughout |
| A | Survey planning: objectives, parameter, population, design choice, non-sampling errors |
| B | Sample-size determination and sensitivity analysis |
| C | Final sample size, population construction and sample selection |
| D | Design-based estimation with the `survey` package |
| E | Monte Carlo simulation comparing stratified Neyman sampling with SRSWOR |

## Data note

All data are simulated. No real policyholder information is used, and the lognormal parameters are assumptions made for this exercise. The choice of claim types was informed by a published list of common motor claims (see the report's references). No questionnaire or data-collection instrument was used, because the data are simulated.

## Declaration of generative AI use

Claude (Anthropic) was used to help structure the report, draft the R code, write the LaTeX text and equations, and set up the GitHub repository. I verified the code, formulas and results against the course notes. The full declaration is at the end of the report.

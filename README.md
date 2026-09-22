# Fast Calibration of GARCH Models

> Academic research project — ENSAI · 2023–2024

A computational statistics project studying how **Le Cam's one-step estimator** can accelerate the calibration of GARCH models while retaining statistical properties close to quasi-maximum likelihood estimation.

## Research question

Can GARCH estimation be made substantially faster without giving up the consistency and asymptotic behaviour expected from QML-based estimation?

## Method

The project adapts a **one-step estimator** to GARCH(p, q) models.

```text
Time series
    │
    ▼
Initial QML estimate on a fraction δ of the sample
    │
    ▼
Score + Hessian correction
    │
    ▼
One-step estimator
    │
    ▼
Statistical & computational evaluation
```

The theoretical study focuses on consistency and asymptotic normality under the assumptions developed in the report.

## Monte Carlo experiment

The empirical study compares:

- standard QML estimation;
- one-step estimation with **δ = 0.9**;
- one-step estimation with **δ = 0.7**.

The simulation protocol uses **2,000 Monte Carlo replications per sample size**, with sample sizes ranging from **20,000 to 70,000** observations.

Evaluation focuses on estimator distributions, mean squared error and computation time.

## Computational results

For a sample size of **70,000**:

| Estimator | Computation time |
|---|---:|
| QML | 2,422 s |
| One-step · δ = 0.9 | 772 s |
| One-step · δ = 0.7 | **123 s** |

The one-step estimator provides a substantial reduction in computation time in the reported simulations. The trade-off is statistical: its MSE is slightly higher than QML and tends to increase when δ decreases.

## Statistical interpretation

Monte Carlo distributions remain close across the estimators in the experiments, while the one-step estimators show somewhat greater variability, particularly for smaller values of δ.

The objective is therefore not to claim that one-step estimation dominates QML, but to study a **compute–accuracy trade-off**.

## Real-world application

The methodology was also applied to **S&P 500 data from 1950 to 2019**. The analysis identifies volatility clustering and dependence in squared returns, and uses a **GARCH(2,2)** specification for the application.

Rolling comparisons in the report show similar modelling behaviour between QML and one-step estimation while retaining the computational advantage of the latter.

## Limitations

- large samples are required for the asymptotic regime studied in the project;
- some theoretical developments rely on simplifying assumptions;
- reducing δ improves computational efficiency but can increase estimation error;
- the empirical conclusions are tied to the simulation settings and application studied.

## Repository status

This repository currently documents the research methodology and results. Reproducible code and figures will be added only from material that can be shared and validated against the original academic work.

## Portfolio

A visual case study is available in my ML/AI Engineering portfolio.

## Authors

Elie Gislain Sanon · Mahama Stéphane Gbane · Jean Grivo Aboula Edang  
Supervisor: Youssef Esstafa  
ENSAI · 2023–2024

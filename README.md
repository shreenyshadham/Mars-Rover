# AI Based Predictive Battery Monitoring for Rover Mission Operations

This repository contains the code and supporting material for an MSc Data Science dissertation at Newcastle University investigating whether short-horizon machine-learning battery predictions can support safe and effective energy-management decisions in simulated rover missions.

## Project Overview

The project uses NASA lithium-ion battery ageing data to construct physically grounded battery forecasting tasks at an exact 120-second horizon.

Two prediction tasks are evaluated:

- **Regression:** prediction of SOC drop over the next 120 seconds
- **Classification:** prediction of future battery risk as Safe, Warning, or Critical

The selected deployment-oriented models are then integrated into a custom **Gymnasium software-in-the-loop rover environment** and compared with simpler energy-management strategies.

A central aim of the project is to evaluate **prediction accuracy separately from controller performance**.

## Methodology

The final methodology consists of two stages:

### 1. Battery Prediction

- NASA lithium-ion battery discharge data
- 34 unique batteries after duplicate removal
- Physically grounded 120-second SOC targets
- Causal feature engineering and leakage prevention
- Battery-level train/test separation
- 25 development batteries
- 9 completely held-out test batteries
- 4-fold grouped cross-validation

Regression models:

- Ridge Regression
- Histogram Gradient Boosting Regressor

Classification models:

- Logistic Regression
- Histogram Gradient Boosting Classifier

Baselines include:

- Training-mean regression
- Current-risk persistence
- Constant-current physics forecasting

### 2. Rover Controller Evaluation

The trained deployment-oriented battery models are integrated into a custom Gymnasium rover-style simulation.

Five controller strategies are compared:

- No intervention
- Direct SOC threshold
- Constant-current physics forecast
- ML predictive control
- Oracle future-energy reference

Evaluation uses **200 paired randomised missions**, meaning every controller is evaluated under identical mission specifications.

## Main Results

### Battery Prediction

Deployment-oriented Histogram Gradient Boosting regression:

- **MAE:** 0.307 SOC percentage points
- **RMSE:** 1.758
- **R²:** 0.852

Deployment-oriented Histogram Gradient Boosting classification:

- **Macro-F1:** 0.958
- **Critical-state recall:** 0.990
- **Critical-to-safe error:** approximately 0.20%

The regression model clearly outperformed the simple statistical and constant-current physics regression baselines on held-out batteries.

Classification showed a clear improvement over current-risk persistence, while its advantage over the stronger physics-based classifier was smaller.

## Rover Controller Results

Safe mission success across 200 paired randomised missions:

| Controller | Safe Mission Success | Safety Violations |
|---|---:|---:|
| No intervention | 75.5% | 24.5% |
| Direct SOC | 50.0% | 0.0% |
| Constant-current physics | 40.0% | 0.0% |
| ML predictive | 34.5% | 0.0% |
| Oracle future-energy reference | 50.0% | 0.0% |

The ML predictive controller maintained zero observed safety violations but was overly conservative under the adopted control policy, resulting in lower mission completion.

## Key Finding

**Accurate battery prediction does not automatically result in better mission-level control.**

The results demonstrate that predictive accuracy and the decision policy used to act on those predictions should be evaluated separately.

## Repository Structure

```text
data/       Data-related files and supporting resources
docs/       Project documentation
figures/    Figures used in evaluation and reporting
notebooks/  Jupyter / Google Colab notebooks
results/    Model outputs, metrics and evaluation results
src/        Supporting Python code

```
## Author

**Chinmayee Shree Nyshadham Rama Bramha**<br>
MSc Data Science<br>
School of Computing<br>
Newcastle University<br>

# Mars-Rover

This repository contains the code and supporting files for an MSc Data Science dissertation project on AI-based battery monitoring and low-energy risk prediction for rover-style energy systems.

## Project Overview

The project focuses on short-term State-of-Charge forecasting and low-energy risk prediction using public battery data, physics-informed battery modelling, and simulated rover mission telemetry.

## Current Status

The current prototype includes:

- PyBaMM-based lithium-ion battery discharge simulation
- Configurable rover-style mission simulation
- Scenario-based telemetry generation
- Low-energy risk labelling using SoC thresholds
- Preliminary machine learning experiments using Linear Regression, Random Forest, and LSTM

## Repository Structure

```text
data/       Raw, processed, and simulated datasets
docs/       Reports, project documents, and planning material
figures/    Figures used in reports and evaluation
notebooks/  Jupyter/Colab notebooks for experiments
results/    Model outputs, metrics, and predictions
src/        Reusable Python scripts
```

## Data

The project uses the NASA Prognostics Center of Excellence battery dataset. Raw NASA .mat files are not included in this repository and should be downloaded from the official NASA source.

## How to Run

Install the required packages using:

pip install -r requirements.txt

The main interim-stage notebook is available in:

notebooks/01_interim_prototype.ipynb

##Author

Chinmayee Shree Nyshadham Rama Bramha
MSc Data Science, Newcastle University

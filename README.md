# DSAI5207 Final Project

## 1. Project Overview

This project studies a **small-scale multi-label image classification** task using the Pokemon dataset. Each image is associated with one or two Pokemon types, and the prediction target is represented as an **18-dimensional multi-label vector**.

Our goal is to compare three lightweight CNN variants under a controlled setting:

- `Plain + GAP`
- `Residual + GAP`
- `Plain + GMP`

To analyze not only architectural differences but also their sensitivity to optimization time, all three models are evaluated under four training durations:

- `30` epochs
- `60` epochs
- `100` epochs
- `150` epochs

The final submission package organizes experiment outputs by epoch setting and also provides a combined summary file for cross-setting comparison.

---

## 2. Directory Structure

```text
3060100150/
├── 30/
│   ├── 30.ipynb
│   ├── figures/
│   └── model/
├── 60/
│   ├── 60.ipynb
│   ├── figures/
│   └── model/
├── 100/
│   ├── 100.ipynb
│   ├── config.json
│   ├── history_df.csv
│   ├── summary_df.csv
│   ├── summary_raw_df.csv
│   ├── figures/
│   └── model/
├── 150/
│   ├── 150.ipynb
│   ├── config.json
│   ├── history_df.csv
│   ├── summary_df.csv
│   ├── summary_raw_df.csv
│   ├── figures/
│   └── model/
├── images/
├── pokemon.csv
├── summary.xlsx
└── summary_fig.ipynb
```

---

## 3. File Description

### 3.1 Dataset Files

- `pokemon.csv`  
  CSV file containing Pokemon names and type annotations used to construct the multi-label targets.

- `images/`  
  Image folder containing the 809 Pokemon images used in the project.

### 3.2 Per-Epoch Experiment Folders

The folders `30/`, `60/`, `100/`, and `150/` correspond to the four epoch caps used in the final study.

Each folder contains the experiment materials for that training duration.

#### Notebook

- `30/30.ipynb`
- `60/60.ipynb`
- `100/100.ipynb`
- `150/150.ipynb`

These notebooks contain the training and evaluation pipeline for the corresponding epoch setting.

#### figures/

The `figures/` folder stores the main visual outputs for that epoch setting, including:

- validation macro-F1 curve
- validation loss curve
- test metric summary
- precision-recall figure
- class-wise F1 heatmap

#### model/

The `model/` folder stores the trained checkpoints of the three compared variants:

- `plain_gap.pth`
- `residual_gap.pth`
- `plain_gmp.pth`

### 3.3 Additional Exported Files

The `100/` and `150/` folders also include:

- `config.json`  
  Saved experiment configuration.

- `history_df.csv`  
  Training history exported from the run.

- `summary_df.csv`  
  Aggregated summary results for that epoch setting.

- `summary_raw_df.csv`  
  More detailed raw summary records.

### 3.4 Combined Summary Files

- `summary.xlsx`  
  Combined quantitative results across all four epoch settings and all three model variants.

  The table includes columns such as:

  - `Model`
  - `Epoch`
  - `CVMacro`
  - `CVMicro`
  - `CVmAP`
  - `BestEp`
  - `BestThr`
  - `TestMacro`
  - `TestMicro`
  - `Precision`
  - `Recall`
  - `TestmAP`

- `summary_fig.ipynb`  
  Notebook used to generate the cross-epoch summary figures from `summary.xlsx`.

---

## 4. How to Inspect the Results

We recommend reading the submission package in the following order.

### 4.1 Start with `summary.xlsx`

This file gives the most direct quantitative comparison across:

- three model variants
- four epoch settings
- cross-validation metrics
- held-out test metrics
- selected best epoch
- selected best threshold

It is the main entry point for checking the final numerical results.

### 4.2 Then check `summary_fig.ipynb`

This notebook is used to generate combined figures for:

- held-out test performance across epochs
- cross-validation performance across epochs
- CV-test gap
- precision-recall behavior

It provides a convenient overview of the overall trends.

### 4.3 Inspect a specific epoch folder if needed

If more detail is needed for a particular training duration, open the corresponding folder:

- `30/`
- `60/`
- `100/`
- `150/`

Each folder contains:

- notebook for that setting
- figures generated for that setting
- model checkpoints for the three variants

---

## 5. Running Notes

The experiment notebooks use path variables such as:

- `BASE_DIR`
- `CSV_PATH`
- `IMG_DIR`
- `FIG_DIR`
- `MODEL_DIR`

If a notebook is re-run in a different local environment, these paths may need to be adjusted to match the current working directory.

For result inspection, the most important files are:

1. `summary.xlsx`
2. `summary_fig.ipynb`
3. the `figures/` folders inside each epoch directory

---

## 6. Final Remarks

This submission package supports three levels of inspection:

1. **Quantitative comparison**  
   Use `summary.xlsx`

2. **Trend visualization**  
   Use `summary_fig.ipynb`

3. **Per-setting details**  
   Use the corresponding epoch folder (`30/`, `60/`, `100/`, `150/`)

The final study compares the same three lightweight CNN variants under four training durations in a controlled small-scale multi-label setting.

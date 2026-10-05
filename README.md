# Reconsidering Brain Age

Code accompanying the paper:
"Reconsidering Brain Age: Why Age-Prediction Models Fail as Measures of Brain Aging"

This repository provides two complementary analysis tracks:

1. Simulated aging experiments to demonstrate key conceptual issues in brain-age modeling.
2. Empirical validation workflows (real and synthetic data) to reproduce the paper's core analyses and figures.


## Repository Structure

```
Reconsidering-Brain-Age/
|-- simulated_aging/
|   `-- brain_age_simulation.ipynb
|-- empirical_validation/
|   |-- process_data.ipynb
|   |-- synthesize_data.ipynb
|   |-- empirical_analysis_real_data.ipynb
|   |-- empirical_analysis_synthetic_data.ipynb
|   |-- README.md
|-- figures/
|   `-- dynamic_brain_age_figure.svg
`-- README.md
```

## What Each Part Does

- `simulated_aging/brain_age_simulation.ipynb`
	- Simulates a stochastic dynamical system and applies age-prediction models to synthetic trajectories.

- `empirical_validation/process_data.ipynb`
	- Loads raw empirical data and prepares processed analysis data.
	- Produces processed CSV and feature-set JSON files used by downstream notebooks.

- `empirical_validation/synthesize_data.ipynb`
	- Trains tabular generative models and creates a synthetic dataset from processed empirical data.
	- Intended for demonstration/testing when real data cannot be shared.

- `empirical_validation/empirical_analysis_real_data.ipynb`
	- Runs the main empirical analysis pipeline on real processed data.
	- Trains/evaluates models and generates figures and summary outputs.

- `empirical_validation/empirical_analysis_synthetic_data.ipynb`
	- Same analysis logic, but applied to synthetic data.


## Data Availability

The dataset used for the empirical analysis can be accessed by following the instructions in the `empirical_validation/README.md` file.

You can run the synthetic-data analysis notebook after downloading the synthetic data from: [Link](https://uio-my.sharepoint.com/:f:/g/personal/edvardgr_uio_no/IgD6vQYUV_w-QIHNlZBoa3svAc5F66exqF6cYevbAcozxAY?e=GAkZ5e)

The feature-set and hyper-parameters for the brain-age models are also provided in the link above. 

## Prerequisites

- Linux/macOS/Windows with terminal access
- Python 3.8+
- Jupyter Notebook or JupyterLab
- Recommended: `venv` or Conda environment

Python packages used in notebooks:

- numpy
- pandas
- matplotlib
- seaborn
- scikit-learn
- statsmodels
- patsy
- xgboost
- sdv

Notes:

- `json`, `pickle`, `itertools`, `glob`, `pathlib`, `warnings`, and `sys` are from the Python standard library.
- `sdv` is only required for synthetic data generation.

## Setup

### Option A: venv + pip

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install jupyterlab numpy pandas matplotlib seaborn scikit-learn statsmodels patsy xgboost sdv
```

### Option B: Conda

```bash
conda create -n reconsider-brain-age python=3.11 -y
conda activate reconsider-brain-age
pip install jupyterlab numpy pandas matplotlib seaborn scikit-learn statsmodels patsy xgboost sdv
```

## How to Use the Files

### 1. Run the simulation workflow

Open and run:

- `simulated_aging/brain_age_simulation.ipynb`

### 2. Run empirical workflow on real data

Recommended order:

1. `empirical_validation/process_data.ipynb`
2. `empirical_validation/empirical_analysis_real_data.ipynb`

The notebooks currently define a `DATA_DIR` path in setup cells. Update these path variables to match your local environment before running.

Expected key files after preprocessing include:

- `brain_age_data_processed.csv`
- `features.json`

### 3. Run empirical workflow on synthetic data

Run the synthetic data analysis notebook adding the generated `synthetic_data.csv`.

1. `empirical_validation/empirical_analysis_synthetic_data.ipynb`


## Important Path Configuration

Several notebooks include hardcoded absolute paths in initialization cells (for example in `DATA_DIR`/`data_path`).

Before running on your machine:

1. Open each notebook.
2. Locate the first configuration/setup cell.
3. Replace path values with local directories containing your input/output files.





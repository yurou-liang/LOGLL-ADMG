# Likelihood-Based Nonparametric Causal Discovery under Latent Confounding

This repository contains the code for the algorithm LOGLL-ADMG in the paper "Likelihood-Based Nonparametric Causal Discovery under Latent Confounding".

## Structure

```text
src/logll_admg/
    logll_admg.py          # LOGLL-ADMG model 
    nonlinear.py           # DAGMA initialization model
    locally_connected.py   # Locally connected neural network layer
    utils.py               # Utility functions for DAGMA model

experiments/
    run_experiments.py     # Main script for synthetic and real-data experiments
    Analyse.ipynb          # Analysis and plotting synthetic and real-data experiments results
    realData.ipynb         # Real-data set up

figures/                   # Generated figures
requirements.txt           # Python dependencies
admg_environment.yml       # Conda environment file
setup.py                   # Package installation file
```

## Installation

### Option1 (recommended): pip

```
python -m venv venv
source venv/bin/activate 
pip install -r requirements.txt
```

### Option2: conda

```
conda env create -f admg_environment.yml
conda activate admg
```

## Running synthetic experiments

```
python experiments/run_experiments.py
```

### Example commands:

```
python experiments/run_experiments.py -d 4 -g ancestral -a 0 -s 0 -f MLP
python experiments/run_experiments.py -d 8 -g bowfree -a 0 -s 0 -f func
```

### Arguments:

```
-d, --num_nodes       Number of nodes
-g, --graph_type      Graph type: ancestral or bowfree
-a, --admg            Graph seed
-s, --seed            Random seed
-f, --function        Data generation type: MLP, func
-T, --num_iterations  Number of outer optimization iterations
-lambda1              Directed edge sparsity penalty
-lambda_corr          Bidirected edge sparsity penalty
-lambda_nl            Nonlinearity regularization penalty
```

### Running the Sachs real-data experiment

```
python experiments/run_experiments.py -realData y
```

## Outputs

Each run saves a .json file containing the generated data, ground-truth graph, estimated directed and bidirected matrices, optimization values, and runtime information.

For example:

```
result_d4_graphancestral_admg0_seed0_fMLP.json
realData.json
```
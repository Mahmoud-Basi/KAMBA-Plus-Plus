# KAMBA++

Official experimental implementation for the manuscript **“A Normalization-Free APT Detection Scheme Based on Gated Selective State-Space Learning.”**

 In this paper, we propose KAMBA++, a novel normalization-free sequence-learning architecture for APT and network-intrusion detection. KAMBA++ combines Enhanced Dynamic Tanh (EDyT), a Sparse Kolmogorov–Arnold Network (SKAN), a SwiGLU branch, a Dual-Gated Selective State-Space Model (DSSSM), an adaptive controller, and learned adaptive fusion for binary malicious-traffic detection.

## Repository contents

- `notebooks/KAMBA_PP_Experiments.ipynb`: source notebook with stored outputs removed.
- `notebooks/KAMBA_PP_Experiments_Executed.ipynb`: sanitized execution archive containing the reported experimental outputs.
- `requirements.txt`: Python dependencies used by the notebook.

The notebook contains the complete experimental workflow:

- leakage-aware DAPT2020 reconstruction with Flow-ID-disjoint partitions;
- source-file-specific one-minute temporal blocks for CICIDS2017;
- non-overlapping sequence windows of length eight;
- five-seed full-model evaluation;
- six component-ablation variants;
- Random Forest, MLP, CNN, BiLSTM, Transformer, dense KAN, and selective-SSM baselines;
- inference-efficiency and wall-clock-runtime measurements; and
- publication tables and figure source data.

## Environment

The experiments were conducted with Python 3.9 and PyTorch on an NVIDIA GeForce RTX 4060 Laptop GPU. Create an environment and install the dependencies with:

```bash
conda create -n kambapp python=3.9 -y
conda activate kambapp
pip install -r requirements.txt
```

Install the CUDA-enabled PyTorch build appropriate for your system if the default installation is CPU-only.

## Data layout

The datasets are not redistributed by this repository. Place the original CSV files in:

```text
data/
├── DAPT2020/
└── CICIDS2017_Full/
```

Run the notebook from the repository root so that `PROJECT_ROOT = Path.cwd()` resolves the input and output paths correctly. Dataset files, fitted preprocessing objects, checkpoints, predictions, and generated outputs are excluded from version control.

## Reproducing the experiments

The clean notebook is organized in the same order as the original experimental development record. Execute the environment, implementation, preprocessing-verification, and desired experiment sections in order. Pilot and diagnostic sections are retained for transparency but are not part of the final reported comparisons.

The official settings use the predetermined seeds `(13, 27, 41, 55, 69)`, a maximum of 60 epochs, early-stopping patience of 10, and validation-F1 threshold selection. Test labels are not used for preprocessing, checkpoint selection, or threshold optimization.

The executed archive preserves the numerical results used in the manuscript. Machine-specific paths have been replaced with placeholders; no datasets, credentials, or personal files are included.

## Citation

Citation metadata will be added after publication. Until then, please cite the accompanying manuscript and link to this repository.

## License

This project is released under the MIT License. See `LICENSE`.

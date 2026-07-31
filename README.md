# Battery Formation Surrogate Modeling

Code accompanying the paper:

**Multi-Output Sequence-to-Sequence Surrogate Modeling for Battery Formation: A Physics-Guided Study Toward Hybrid Electrochemical Surrogates**

## Repository structure

```text
notebooks/
├── 00_data_generation/
│   └── Dataset_generation_new_18_protocols.ipynb
├── 01_preprocessing/
│   └── 01_data_preparation_seq2seq.ipynb
├── 02_training/
│   ├── 02_train_gru_seq2seq_nonoverlap.ipynb
│   ├── 02_train_gru_allstates_seq2seq.ipynb
│   ├── 03_train_lstm_seq2seq_nonoverlap.ipynb
│   ├── 03_train_lstm_allstates_seq2seq.ipynb
│   ├── 05_train_mlp_seq2seq_nonoverlap.ipynb
│   └── 07_train_tcn_seq2seq_nonoverlap.ipynb
└── 03_evaluation/
    ├── 04_compare_laststate_allstates_results.ipynb
    ├── 04_compare_selected_nonoverlap_models.ipynb
    ├── 08_mlp_feature_ablation_seq2seq_nonoverlap.ipynb
    ├── 09_mlp_sqrtcc_cross_regime_generalization.ipynb
    └── runtime_comparison_dfn_vs_mlp_surrogate_protocolwise.ipynb
```

## Installation

Python 3.11 or later is recommended.

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab
```

## Reproduction order

1. Run the dataset-generation notebook to create the 18 PyBaMM protocol datasets.
2. Run `01_data_preparation_seq2seq.ipynb` to create the processed sequence datasets.
3. Run the model-training notebooks.
4. Run the evaluation notebooks to reproduce:
   - last-state versus all-state comparisons;
   - selected-model comparison;
   - physics-guided feature ablation;
   - cross-regime generalization;
   - DFN-versus-MLP runtime comparison.

The notebooks use relative project paths. Keep the `data`, model-output, result, and figure directories at the repository root, or update the path variables at the beginning of each notebook.

## Main dependencies

The notebooks use NumPy, pandas, Matplotlib, PyTorch, and PyBaMM. The recorded notebook environments include PyTorch 2.10.0 and PyBaMM versions 25.10.2 and 26.4.1.

## Data

Generated datasets and trained model files are not included because they can be reproduced from the notebooks and may be large. Exclude files such as `.csv`, `.npz`, `.pt`, and `.pth` from Git when appropriate.

## Code availability

The repository contains the dataset-generation, preprocessing, training, model-comparison, ablation, cross-regime, and runtime-analysis notebooks used in the study.

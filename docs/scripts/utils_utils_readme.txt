# utils/utils.py

## Purpose
Supplies shared utility functions for data loading, configuration management, and reproducibility across training scripts.

## How it works
- `set_seed` enforces deterministic behavior across Python, NumPy, and PyTorch.
- Data helpers (`read_train_test_index`, `split_data`, `get_phen_snp`, `get_phen_gr`) load phenotype/genotype datasets, apply predefined splits, and optionally fetch precomputed genetic relatedness matrices.
- `calculate_snp_number` and `windows_flag` inspect SNP columns to compute chromosome window sizes for the MeNet architecture.
- `re_set_config` applies command-line overrides to configuration dictionaries.

## Key relationships
- Imported by both `menet.py` and `train_trait_specific_encoder.py` for consistent configuration handling and data preparation.
- Works with `utils.dataset` outputs to align data splits and with `network.menet.MeNet` to determine whether to use chromosome windowing.

# utils/dataset.py

## Purpose
Prepares PyTorch datasets and dataloaders for both triplet-based contrastive learning and dual-input MeNet training.

## How it works
- `MyDataset` extracts genotype features, population labels, and phenotype targets from pandas DataFrames.
- `TripletDataset` samples anchor/positive/negative genotypes for triplet loss, optionally enforcing cross-population negatives when `flag` is set.
- `prepare_tensors` and `create_dual_scale_dataloader` convert phenotype and genetic relatedness DataFrames into tensors compatible with `network.menet.MeNet`.
- Helper functions `_extract_population_labels`, `_extract_phenotype`, and `_build_label_index` manage label bookkeeping for triplet sampling.

## Key relationships
- Used by `train_trait_specific_encoder.py` to build contrastive triplet dataloaders and by `menet.py` to create paired SNP/GR batches.
- Interfaces closely with models defined in `network/contrastive_learning.py` and `network/menet.py`, ensuring tensor shapes match their expected inputs.

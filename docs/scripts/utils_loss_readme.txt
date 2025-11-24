# utils/loss.py

## Purpose
Implements loss functions used across the project for contrastive learning and regression.

## How it works
- `TripletLoss` normalizes embeddings, computes pairwise distances, and applies a phenotype-aware adaptive margin to separate positive and negative pairs.
- `L1Loss` wraps PyTorch's L1 regression loss for predicting continuous phenotypes.

## Key relationships
- `train_trait_specific_encoder.py` and `utils.train.train_trait_specific_encoder` rely on `TripletLoss` during encoder training.
- `menet.py` pairs `L1Loss` with the MeNet model and hands both to `utils.train.train_menet` for optimization.

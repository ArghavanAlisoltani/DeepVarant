# utils/ig.py

## Purpose
Provides integrated gradients utilities to quantify feature importance for the MeNet fusion model.

## How it works
- `integrated_gradients_batch` interpolates between baselines and embeddings, computes gradients of the fusion output, and averages them to estimate attribution scores for VE and RepGeno inputs.
- `ig_analysis` iterates over batches of VE and GR tensors, reuses the model's encoders to obtain embeddings, and aggregates normalized importance scores for reporting.

## Key relationships
- Called inside `utils.train.train_menet` to monitor interpretability during training launched from `menet.py`.
- Relies on the structure of `network.menet.MeNet` to access its `ve`, `repGeno`, and `fusion` components for attribution calculations.

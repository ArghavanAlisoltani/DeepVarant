# utils/relatedness.py

## Purpose
Computes genetic relatedness matrices from encoder outputs to support downstream analyses.

## How it works
- `calculate_genetic_relatedness` runs the trained trait-specific encoder on SNP data in batches to generate embeddings, then aggregates them into a DataFrame.
- `Euclidean` normalizes embeddings, computes pairwise Euclidean distances, converts them to similarity scores, and saves the resulting matrix for reuse.

## Key relationships
- Invoked at the end of `train_trait_specific_encoder.py` to persist relatedness information after training.
- Saved relatedness matrices are later consumed by `utils.utils.get_phen_gr` and used when training `menet.py` via `create_dual_scale_dataloader`.

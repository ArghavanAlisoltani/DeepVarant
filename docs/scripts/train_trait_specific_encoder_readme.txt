# train_trait_specific_encoder.py

## Purpose
Trains a trait-specific encoder for representative genotypes using a triplet-loss contrastive learning setup.

## How it works
- Loads defaults from `configs/contrastive_learning.json` and allows CLI overrides through `utils.utils.re_set_config`.
- Retrieves phenotype/SNP datasets via `utils.utils.get_phen_snp` and builds triplet dataloaders with `utils.dataset.create_triplet_dataloader`.
- Constructs the encoder backbone with `network.contrastive_learning.TraitSpecificEncoderForRepGeno` and pairs it with `utils.loss.TripletLoss`.
- Runs the training/validation loop through `utils.train.train_trait_specific_encoder`, which manages optimizer scheduling and model checkpointing.
- After training, computes and stores a genetic relatedness matrix using `utils.relatedness.calculate_genetic_relatedness`.

## Key relationships
- Shares data-loading utilities with `menet.py`, ensuring phenotype and genotype splits are consistent across workflows.
- The trained encoder can be reused by other components that need trait-aware genotype embeddings or genetic relatedness scores.

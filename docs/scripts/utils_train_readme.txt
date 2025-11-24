# utils/train.py

## Purpose
Provides reusable training loops for the contrastive encoder and the MeNet regression model, including evaluation helpers and optimizer setup.

## How it works
- `setup_training_env` centralizes device placement, optimizer creation, and learning-rate scheduling.
- Triplet-loss utilities (`forward_triplet_loss_step`, `train_trait_specific_encoder_one_epoch`, `evaluate_trait_specific_encoder`) support the encoder workflow driven by `train_trait_specific_encoder`.
- MeNet utilities (`train_menet_one_epoch`, `evaluate_menet`, `train_menet`) handle supervised regression, compute R² metrics, and trigger integrated gradients via `utils.ig.ig_analysis` during training.

## Key relationships
- Invoked by `menet.py` and `train_trait_specific_encoder.py` to encapsulate their training logic.
- Depends on losses in `utils.loss`, dataloaders constructed in `utils.dataset`, and uses `torch`/`sklearn` for optimization and metrics.

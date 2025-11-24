# menet.py

## Purpose
Entry point for training the MeNet model that fuses variant effect (VE) and representative genotype (RepGeno) information to predict phenotypes.

## How it works
- Loads configuration from `configs/MeNet.json` and applies CLI overrides via `utils.utils.re_set_config`.
- Retrieves phenotype/genotype data and genetic relatedness via `utils.utils.get_phen_snp` and `utils.utils.get_phen_gr`.
- Builds dual-scale dataloaders using `utils.dataset.create_dual_scale_dataloader` and prepares tensors for interpretability with `utils.dataset.prepare_tensors`.
- Initializes `network.menet.MeNet` with chromosome windowing determined by `utils.utils.windows_flag` and sets up the L1 regression loss from `utils.loss.L1Loss`.
- Delegates the full training/validation/test loop to `utils.train.train_menet`, which handles optimizer scheduling and integrated gradients logging.

## Key relationships
- Relies on `network/menet.py` for the model architecture and on `utils/train.py` for training routines.
- Uses preprocessing utilities in `utils/utils.py` and dataloader helpers in `utils/dataset.py` to align inputs for the model.
- Integrated gradients analysis during training depends on `utils/ig.py` through `train_menet`.

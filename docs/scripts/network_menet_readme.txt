# network/menet.py

## Purpose
Defines the MeNet architecture for combining variant-effect (VE) features and representative genotype (RepGeno) embeddings to predict phenotypes.

## How it works
- Provides residual convolution blocks (`ResNet`) and VE encoders (`VE`) that map SNP windows to dense embeddings.
- Supplies a `RepGeno` MLP encoder for genotype-relatedness features.
- Implements feature fusion through `CrossInformationFeatureFusion` and `MultiChrInformationFeatureFusion`, enabling interaction between VE and RepGeno streams with optional chromosome windowing.
- Wraps the components in the `Fusion` head and the top-level `MeNet` model, which returns phenotype predictions via a small feedforward network.

## Key relationships
- Instantiated by `menet.py` with configuration from `configs/MeNet.json` and trained via `utils.train.train_menet`.
- Integrated gradients in `utils.ig.integrated_gradients_batch` target the `fusion` module outputs to assess feature importance.
- Accepts tensor batches prepared by `utils.dataset.create_dual_scale_dataloader`, keeping input shapes aligned with its convolutional expectations.

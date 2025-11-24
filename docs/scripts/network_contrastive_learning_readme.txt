# network/contrastive_learning.py

## Purpose
Contains the convolutional backbone and trait-specific encoder used for contrastive learning on genotype data.

## How it works
- `Backbone` provides depthwise separable convolutions with residual connections and max pooling to progressively downsample SNP sequences.
- `TraitSpecificEncoderForRepGeno` stacks multiple `Backbone` blocks, flattens the features, and projects them into a configurable embedding dimension.
- The `forward` method produces embeddings for anchor, positive, and negative samples to support triplet loss training.

## Key relationships
- Instantiated by `train_trait_specific_encoder.py` and optimized using `utils.loss.TripletLoss` inside `utils.train.train_trait_specific_encoder`.
- The trained encoder feeds into `utils.relatedness.calculate_genetic_relatedness` to build genetic relatedness matrices for downstream models.

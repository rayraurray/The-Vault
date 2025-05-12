Adversarial learning methods are a promising approach to training robust deep networks, and can generate complex samples across diverse domains.

It is a technique used in machine learning to fool or misguide a model with malicious input.

For adversarial based domain adaptation, the model is intended to learn a discriminative mapping of target images to the source feature space (target encoder) by fooling a domain discriminator that tries to distinguish the encoded target images from source examples.

![[Adversarial based Domain Adaptation.png]]

# Overview
## Training Phase
1. The feature extractor and the discriminator are both active.
2. The feature extractor learns to generate features (same feature extractor for both source and target data).
3. The discriminator learns to distinguish between the features coming from the source and the target domains.
4. The adversarial training process aims to reach a point where the discriminator can no longer easily tell the difference between features from the two domains, indicating that the feature extractor is generating domain-invariant features.
## Prediction Phase
1. Only the feature extractor is used to process new data.
2. The learned domain-invariant features are fed into the rest of the model (e.g., a classifier) to make predictions.
3. The discriminator is discarded because its job of differentiating between domains is not relevant during the prediction stage.



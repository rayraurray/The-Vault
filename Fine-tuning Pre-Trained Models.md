[[Fine-tuning (Machine Learning)]]
This is a more complex technique, in which we not only replace the last layer (for classification or regression) of the [[Pre-Trained Model]], but we also selectively retrain some of the previous layers.

We use the knowledge in terms of the global architecture of the network and use its states as a starting point for our retraining step.
# Approach
Freeze (fix weights) some layers during retraining, or fine-tune others according to our needs.
Freeze when target data is scarce. It is to avoid overfitting.
Fine-tune when there are more target data
[[Model Freezing]]

![[Fine tuning PTMs.png]]



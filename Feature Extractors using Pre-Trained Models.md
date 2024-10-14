The key idea here is to simply leverage the weighted layers of the [[Pre-Trained Model]] to extract features, but not to update the weights of the model layers during training with new data for the new task.

Approach: Use the output of one or more layers of a network trained for a different task as generic feature extractors. Then, train a new shallow classifier on these features.

![[feature extractors.png]]

CNN off-the-shelf features works well for fine-grained classification, but fine-tuning (the second approach) could lead to improvement through better adaptation.

Off-the-shelf pre-trained models are normally used when the source and target datasets are from the same domain and the target dataset is small.


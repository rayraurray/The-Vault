Batch [[Gradient Descent]] calculates the error for each example in the training dataset, but only updates the model after all training examples have been evaluated.  

One training epoch means one cycle through the entire training dataset.
# Advantage  
- Fewer updates to the model leading to computationally efficient.  
- Produces a stable error gradient and a stable convergence.  
# Disadvantage  
- A stable error gradient can sometimes result in premature convergence of the model to a less optimal set of parameters.  
- Resource exhausted as it requires the entire training set resides in memory.  
- Model updates, and therefore the speed of training, can become very slow for large datasets.
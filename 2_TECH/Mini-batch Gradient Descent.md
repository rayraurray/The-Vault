Mini-batch gradient is a variant of [[Gradient Descent]] descent splits the training dataset into mini batches, and calculates the error and updates the model for each mini batch.
# Advantage  
- Update frequency that is higher than batch gradient descent allows for a more robust convergence, avoiding local minima.  
- Mini-batch size < total training set = adding noise to the learning process, which can help to improve the generalization error.  
- Resource efficiency  
# Disadvantage  
- Additional hyperparameter which is the mini-batch size for the learning algorithm.
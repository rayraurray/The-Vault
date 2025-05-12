An optimization algorithm is **a tool used in deep learning to update model parameters and minimize the defined loss function**, with the aim of improving the performance of combinatorial models by minimizing the objective function value.

The loss function of logistic regression, linear regression and SVM only contain a minima (or a maxima) but no saddle points because the function is convex.  

Saddle points are present in the loss function of Neural Networks because the  function is complex and non-convex.  

Using traditional optimization approach like SGD, if we are stuck with a local minimum or a saddle point, it will be very difficult to escape because the gradient term becomes zero.
![[optimization.jpg]]

# SGD with Momentum
Momentum helps accelerate SGD in the relevant direction and dampens oscillations by adding a fraction of the update vector of the past step to the current update vector.
# Nesterov Accelerated Gradient (NAG)  
Similar to momentum, but the gradient is calculated at the position ahead in the direction of the momentum. This anticipatory update prevents  
overshooting and improves convergence.  
# Adagrad  
This algorithm adapts the learning rate to the parameters, performing smaller updates for parameters associated with frequently occurring features, and larger updates for parameters associated with infrequent features. It's particularly useful for sparse data.
# RMSprop  
RMSprop adjusts the learning rate by dividing by an exponentially decaying average of squared gradients. This allows it to adapt the learning rate for each of the parameters.  
# Adam (Adaptive Moment Estimation)
Combines elements of momentum and RMSprop, maintaining a moving average of both the gradients and their squared values to adjust the learning rate for each parameter. Adam is widely used due to its high performance in a variety of problems.  
# Adadelta
An extension of Adagrad that seeks to reduce its aggressive, monotonically decreasing learning rate by calculating a window of accumulated past gradients.
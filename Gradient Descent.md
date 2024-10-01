Gradient descent is an optimization algorithm which is commonly-used to train [[Machine Learning]] models and [[Neural Network]]s. It trains machine learning models by minimizing errors between predicted and actual results.

- Hypothesis ℎ𝜃 𝑥 is represented as:  
$$\Large
h_\theta(𝑥) = \theta_0 + \theta_1x
$$
- Parameters: 
$\large \theta_0$ and $\large \theta_1$  
- Cost function:
$$\Large
J(\theta_0, \theta_1) = \frac{1}{2N}\sum^N_{n=1}(h_{\theta}(x^{(n)})-y^{(n)})^2
$$
- Goal:
minimize $\large J(\theta_0, \theta_1)$
# How it works
![[Gradient Descent.png]]
![[How Gradient Descent works.png]]

---
# Variants
Gradient descent update a set of parameters in an iterative manner to minimize an error function.  
The behavior of gradient descent varies depending on the quantity of training data utilized during each iteration.  

There are three main types of gradient descent: 
[[Batch Gradient Descent]] 
[[Stochastic Gradient Descent]]
[[Mini-batch Gradient Descent]]

![[Variants of Gradient Descent.png]]






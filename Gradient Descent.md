Gradient descent is an optimization algorithm which is commonly-used to train [[Machine Learning]] models and [[Neural Network]]s. It trains machine learning models by minimizing errors between predicted and actual results.

- Hypothesis ℎ𝜃 𝑥 is represented as:  
ℎ𝜃(𝑥) = 𝜃0 + 𝜃1𝑥  
- Parameters: 
𝜃0 and 𝜃1  
- Cost function:
![[GD Cost Function.png]]
- Goal:
minimize J(𝜃0 , 𝜃1)
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






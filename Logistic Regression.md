Logistic Regression is one of the machine learning algorithms used for classification problems.  
It predicts the probability of a categorical dependent variable 𝑦, which could be represented by binary values, 0 or 1, true or false, yes or no.  
In other words, the logistic regression model predicts $\large P(y = 1 | x; \theta)$ as a function of $\large x$, given parameters of $\large \theta$.

This type of statistical model (also known as _logit model_) is often used for classification and predictive analytics. Since the outcome is a probability, the dependent variable is bounded between 0 and 1. In logistic regression, a logit transformation is applied on the odds—that is, the probability of success divided by the probability of failure. This is also commonly known as the log odds, or the natural logarithm of odds, and this logistic function is represented by the following formulas:

- To ensure hypothesis $\large h_\theta$ lies between 0 and 1:
$$\Large 0 ≤ h_\theta (x) ≤ 1$$
- We have:
$$\Large
z = \theta_0 + \theta_1x
$$
$\large h_\theta (x)$ is represented as:  
$$\Large
h(x) = g(z)
$$
where $\large g$ is a sigmoid function:
$$\Large
g(z)=\frac{1}{1+e^{-z}}
$$
The extended representation of $\large h_\theta (x)$ can be written as:
$$\Large
h_\theta(x) = \frac{1}{1+e^{-(\theta_0+\theta_1x)}}
$$
![[Sigmoid Predict.png]]
# Interpretation of $h_\theta (x)$
$$\Large
h_\theta(x) = g(z) = g(\theta_0 + \theta_1x) = g(\theta_0 + \theta_1.weight)
$$
![[Sigmoid Intepretation.png]]
$$ \large
h_\theta(x) = P(y = 1 | x; \theta) = \frac{1}{1+e^{-(\theta_0+\theta_1x)}}
$$
$$ \large
P(y = 0 | x; \theta) + P(y = 1 | x; \theta) = 1
$$
$$ \large 
P(y = 0 | x; \theta) = 1 - P(y = 1 | x; \theta)
$$

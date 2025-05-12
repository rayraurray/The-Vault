Simple [[Linear Regression]] refers to a method when dealing with a single independent variable $x$.
![[Linear Regression Equation.png]]
For example, from a series of $N$ training set, we want to model the relationship between the height and width of sea bream (a type of fish species).

![[Relationship between Seabream Height and Width.png]]

We assign height as the independent variable, $x$ and width as the dependent variable, $y$.  
If we plot the data, we can see a positive relationship between the two variables.

![[Regression Example.png]]

The relationship between the two variables 𝑥 and 𝑦 can be modeled by a linear equation:
$$\Large
h_\theta(𝑥) = \theta_0 + \theta_1x
$$
given $\large \theta_0$ is the bias (intercept) , $\large \theta_1$ is the weight (coefficient) associated to $x$.
# Optimization Methods
[[Ordinary Least Square (OLS)]]  
[[Gradient Descent]]  

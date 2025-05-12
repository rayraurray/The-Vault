Multiple [[Linear Regression]] refers to a method when dealing with multiple independent variable 𝑥.

Multiple linear regression (MLR) is a method used to model the linear relationship between two or more independent variables and a dependent variable.  
- The price of a house is correlated to its size in square feet and the number of bedrooms.  
MLR based on the assumption that the independent variables are not too highly correlated with each other.  
- The size and number of bedrooms are not highly correlated.

- Hypothesis $\large h_\theta (x)$ is represented as:  
$$
\Large h_\theta (x) = \theta_0x_0 + \theta_1x_1 + \theta_2x_2 +...+\theta_Mx_M
$$
- Parameters: 
$$\large \theta_0, ..., \theta_N$$
- Cost function:
$$ \Large
J(\theta) = \frac{1}{2N}\sum^N_{n=1}(h(x^{(n)}) - y^{(n)})^2
$$
- Goal
minimize $\large J(\theta)$
# Solutions for the MLR  
See all in [[Normal Equation]]  
See all in [[Gradient Descent]]

|      | Normal Equation                                                                                                                                                                          | Gradient Descent                                                                                                                                                    |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Math | $\large \theta = (X^TX)^{-1}X^TY$<br>where: <br>$X$ is a $N \space * (M+1)$ matrix<br>$Y$ is a $N \space * \space 1$ matrix                                                              | Repeat<br>$\Large\theta_j \leftarrow \theta_j - \alpha\frac{\delta J}{\delta \theta_j}$<br>$\large \theta$ is updated simultaneously for $\large j = 0, ..., M$<br> |
| Pros | No need to adjust learning rate<br>No iterative training.                                                                                                                                | Still works efficiently when number of params learned is very large.                                                                                                |
| Cons | Computationally expensive when number of params learned is too large.<br>It is possible that $(X^TX)^{-1}$ is non-reversible if there are **redundant features** or **too many params**. | Need to adjust learning rate.<br>Need iterative learning.                                                                                                           |





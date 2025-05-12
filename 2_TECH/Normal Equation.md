Normal Equation is an analytical approach to Linear Regression with a Least Square Cost Function.  
Normal equation provides a more convenient way to solve the linear regression optimization problem without going through all the long partial derivatives $\Large \frac{\delta}{\delta}$.  

# Equation
Normal equation is as follows:  
$$ \Large
\theta = (X^T X)^{-1} X^T Y
$$
# Example
To optimize two params $\large \theta_0$ and $\large \theta_1$:
$$ \Large
J(\theta_0, \theta_1) = \sum^{N}_{n=1}(y^{(n)}-(\theta_0+\theta_1x^{(n)}))^2
$$

Substitute $X$ and $Y$ into $\large \theta = (X^T X)^{-1} X^T Y$ where:
$$ \large
X = 
\begin{bmatrix} 
x_0^{(1)} & x_1^{(1)} \\ 
x_0^{(2)} & x_1^{(2)} \\
x_0^{(3)} & x_1^{(3)} \\
...
\end{bmatrix}_{(N\space * \space2)}
$$
$$ \large
Y = 
\begin{bmatrix} 
y^{(1)} \\ 
y^{(2)} \\
y_{(3)} \\
...
\end{bmatrix}_{(N\space * \space1)}
$$
- Note: $\large N$ in this example is Number of training data, $\large 2$ is Number of parameters 
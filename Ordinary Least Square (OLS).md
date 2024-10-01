Given N number of data points (training set) =  
($\large x_1$ , $\large y_1$), ($\large x_2$ , $\large y_2$ ),......, ($\large x_N$ , $\large y_N$)  
• Goal: To find a linear model ($\large h_\theta(𝑥) = \theta_0 + \theta_1x$) that best fit all the data.

![[SLR Example.png]]
# Cost Function
The Ordinary Least Square Cost Function is:
$$\Large
J(\theta_0, \theta_1) = \sum^{N}_{n=1}(y^{(n)}-h_\theta(x^{(n)}))^2
$$
which also can be written as:
$$ \Large
J(\theta_0, \theta_1) = \sum^{N}_{n=1}(y^{(n)}-(\theta_0+\theta_1x^{(n)}))^2
$$
Characteristic of least square cost function:  
- Least square is one of the convex optimization problems  
- The convex function have a single global minimum

![[Global Minimum.png]]

Method of least square directly computes the optimal choice of $\large (\theta_0, \theta_1)$ at the global minimum, by taking the derivative.  
$$\large argmin_{\theta_0, \theta_1} J(\theta_0, \theta_1)$$
Setting:
$$\Large \frac{\delta J}{\delta \theta_0}$$
$$\Large \frac{\delta J}{\delta \theta_1}$$
# Normal Equation
[[Normal Equation]]
Regularization is one of the techniques used to deal with overfitting by avoiding the learning of a more complex or flexible model.
[[Linear Regression]]
# Ridge Regression
$$\Large
J(\theta) = \frac{1}{2N}[\sum^N_{n=1}(h(x^{(n)})-y^{(n)})^2+\lambda \sum^M_{j=1}\theta^2_j]
$$
where:
$$\Large
\lambda \sum^M_{j=1}\theta^2_j
$$
is the regularization term.\

This regularization method is called **L2 regularization**.  
A Regression model that uses L2 regularization technique is called **Ridge Regression**.

- Goal: minimize $\large J(\theta)$
- To minimize $\large J(\theta)$, the learned model will try to shrink the regularization term by reducing the 𝜃𝑗 towards zero.  
- The values of  $\large \theta_j$ decrease and become smaller, leading to a simpler hypothesis/model.

When $\large \lambda$ is too large, the learned model will force the  $\large \theta_j$ to shrink to a larger extent towards zero. The hypothesis will become almost linear.

Using a very large value of $\large \lambda$ can lead to underfitting of the training set.\

![[When λ is too large.png]]
# Lasso Regression
$$\Large
J(\theta) = \frac{1}{2N}[\sum^N_{n=1}(h(x^{(n)})-y^{(n)})^2+\lambda \sum^M_{j=1}|\theta_j|]
$$
where:
$$\Large
\lambda \sum^M_{j=1}|\theta_j|
$$
is the regularization term.\

This regularization method is called **L1 regularization**.  
A regression model that uses L1 regularization technique is called **Lasso Regression**.

Lasso has the property that is able to shrink some of the weights to zero. Therefore, that feature can be removed from the model. Lasso can be used to select important features of a dataset.

When $\large \lambda$ is too small, the regularization term has almost no effect in regularizing the $\large \theta_j$.
![[When λ is too small.png]]
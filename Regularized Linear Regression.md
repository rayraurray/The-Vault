Regularization is one of the techniques used to deal with overfitting by avoiding the learning of a more complex or flexible model.
[[Linear Regression]]
# Ridge Regression
![[L2 regularization term.png]]
This regularization method is called L2 regularization.  
A Regression model that uses L2 regularization technique is called Ridge Regression.

- Goal: minimize J(𝜃)  
- To minimize J(𝜃), the learned model will try to shrink the regularization term by reducing the 𝜃𝑗 towards zero.  
- The values of 𝜃𝑗 decrease and become smaller, leading to a simpler hypothesis/model.

When λ is too large, the learned model will force the 𝜃𝑗 to shrink to a larger extent towards zero. The hypothesis will become almost linear.
Using a very large value of λ can lead to underfitting of the training set.\

![[When λ is too large.png]]

When λ is too small, the regularization term has almost no effect in regularizing the 𝜃𝑗.
![[When λ is too small.png]]

![[L1 regularization.png]]
This regularization method is called L1 regularization.  
A regression model that uses L1 regularization technique is called **Lasso Regression**.  
Lasso has the property that is able to shrink some of the weights to zero. Therefore, that feature can be removed from the model.  
Lasso can be used to select important features of a dataset.
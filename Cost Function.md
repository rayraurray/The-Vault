A cost function is a mathematical formula used to calculate the total cost of production for a given quantity of output. It represents the relationship between the cost of production and the level of output, incorporating various factors such as fixed costs, variable costs, and total costs.

![[Cost Function extended.png]]

Using [[Linear Regression]] cost function logistic regression may result in a **non-convex** function.  
This is due to the sigmoid function of ℎ𝜃(𝑥 𝑛) is a non-linear function.
![[Non-convex function.png]]

In [[Logistic Regression]], the cost function measures the discrepancy between the predicted probabilities and the actual labels in the training data. Specifically, it quantifies how well the model's predictions align with the true outcomes.  
The Binary Cross-entropy Loss Function is commonly used as the cost function. It penalizes the model more severely for misclassifications  that have higher confidence.  
By minimizing the cost function, the model adjusts its parameters to improve its predictive accuracy on the training data.

The formula for the binary cross-entropy cost function:
![[Binary cross-entropy cost function.png]]
![[Binary Cross-Entropy Cost Function Where.png]]

# In relation to [[Gradient Descent]]
![[Cost Function in relation to Gradient Descent.png]]

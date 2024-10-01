A cost function is a mathematical formula used to calculate the total cost of production for a given quantity of output. It represents the relationship between the cost of production and the level of output, incorporating various factors such as fixed costs, variable costs, and total costs.
# Linear Regression Cost Function
$$\Large
J(\theta) = \frac{1}{2N}\sum^N_{n=1}(h_\theta(x^{(n)})-y^{(n)})^2
$$
Using [[Linear Regression]] cost function logistic regression may result in a **non-convex** function.  
This is due to the sigmoid function of ℎ𝜃(𝑥 𝑛) is a non-linear function.
![[Non-convex function.png]]
# Logistic Regression Cost Function
In [[Logistic Regression]], the cost function measures the discrepancy between the predicted probabilities and the actual labels in the training data. Specifically, it quantifies how well the model's predictions align with the true outcomes.  

The Binary Cross-entropy Loss Function is commonly used as the cost function. It penalizes the model more severely for misclassifications  that have higher confidence.  

By minimizing the cost function, the model adjusts its parameters to improve its predictive accuracy on the training data.

The formula for the Binary Cross-Entropy Cost Function:
$$\large
J(\theta) = -\frac{1}{N}\sum^N_{i=1}[y^{(i)}\log(h_\theta(x^{(i)}))+(1-y^{(i)})\log(1-h_\theta(x^{(i)}))] 
$$
where:
$\large J(\theta)$ represents the cost function.
$\large N$ is the number of training examples.
$\large y^{(i)}$ is the actual training label (0 or 1) of the $\large i$-th training example. 
$\large h_\theta(x^{(i)})$ is the predicted probability that the $\large i$-th training example belongs to class 1, given by the sigmoid function applied to the input $\large x^{(i)}$ and the model parameters $\large \theta$.
# In relation to [[Gradient Descent]]
- Hypothesis $\large h_\theta(x)$ is represented as:
$$\Large
h_\theta(x) = \frac{1}{1+e^{-(\theta^Tx)}}
$$
- Parameters:
$\large \theta_0, \theta_1, ..., \theta_M$ 
- Cost Function:
$$
J(\theta) = -\frac{1}{N}\sum^N_{i=1}[y^{(i)}\log(h_\theta(x^{(i)}))+(1-y^{(i)})\log(1-h_\theta(x^{(i)}))] 
$$
- Goal:
minimize $\large J(\theta)$


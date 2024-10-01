[[AML]]
# Linear Regression using Hard Threshold

For example, from a series of $N$ training set, we want to model the relationship between the obesity level and weight.  
The obese patient is labeled as 1 and the non-obese patient is labeled as 0.
![[obese vs non-obese.png]]
This red line shows the linear regression model that maps the independent variables (weight) to the dependent variable (obesity level).  
It learns the best fit line to minimize the distance between the predicted value $\large h_\theta (x)$ and actual value $\large y$.
![[linear regression for obese non-obese.png]]
Using a linear regression model, the predicted value $\large h_\theta (x)$ can be classified into a real value, $\large y$ (0 or 1) based on hard threshold. For example: threshold $\large h_\theta (x)$ at 0.5
![[Threshold for Linear Regression.png]]
**However, linear regression model used for classification is sensitive to imbalanced data**
In addition, the prediction is continuous but not probabilistic.  
	It is possible that $\large h_\theta (x) < 0$ and $\large h_\theta (x) > 1$.
For classification, we want to model the probability of 𝑦 being 0 or 1 based on a probabilistic model, $\large h_\theta (x) = P(y = 1|x; \theta)$.   
	Hence, the prediction should fall within $1 ≤ \large h_\theta (x) ≤ 0$

=> Thus we have [[Logistic Regression]]
# Decision Boundary
See all in [[Decision Boundary]]
# Linear Regression vs Logistic Regression
| Linear Regression                                                                                                  | Logistic Regression                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Data is modelled by a linear  <br>function.                                                                        | Data is modelled by S-shaped  <br>logistic function                                                                    |
| It is necessary that a linear  <br>relationship be established among  <br>dependent and independent  <br>variable. | It is not necessary that a linear  <br>relationship be established among  <br>dependent and independent  <br>variable. |
| The dependent target output, 𝑦 is  <br>continuous.                                                                | The dependent target output, 𝑦 is  <br>discrete.                                                                      |
| ![[Linear Regression Example Another.png]]                                                                         | ![[Logistic Regression Example.png]]                                                                                   |
|                                                                                                                    |                                                                                                                        |
# Cost Function
See all in [[Cost Function]]
# Multiclass Classification
See all in [[Multiclass Classification]]
# Variants of Gradient Descent
See Variants in [[Gradient Descent]]
# Logistic Regression in Python
[[Python]] libraries:
- [[Numpy]]: library for efficient numerical operations.  
- [[Pandas]]: library for data manipulation.  
- [[Scikit-learn]]: library of machine learning tools.  
	linear_model: Implements logistic regression and other linear models.  
	vm: Module for support vector machine algorithms.  
	tree: Module for decision tree-based algorithms.
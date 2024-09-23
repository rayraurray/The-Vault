[[AML]]

# Linear Regression using Hard Threshold

For example, from a series of 𝑁 training set, we want to model the relationship between the obesity level and weight.  
The obese patient is labeled as 1 and the non-obese patient is labeled as 0.
![[obese vs non-obese.png]]
This red line shows the linear regression model that maps the independent variables (weight) to the dependent variable (obesity level).  
It learns the best fit line to minimize the distance between the predicted value ℎ𝜃(𝑥) and actual value 𝑦.
![[linear regression for obese non-obese.png]]
Using a linear regression model, the predicted value ℎ𝜃(𝑥) can be classified into a real value, 𝑦 (0 or 1) based on hard threshold. For example: threshold ℎ𝜃(𝑥) at 0.5
![[Threshold for Linear Regression.png]]

**However, linear regression model used for classification is sensitive to imbalanced data**
In addition, the prediction is continuous but not probabilistic.  
	It is possible that ℎ𝜃 (𝑥) < 0 and ℎ𝜃 (𝑥) > 1.
For classification, we want to model the probability of 𝑦 being 0 or 1 based on a probabilistic model, ℎ𝜃 (𝑥)= P (𝑦 = 1| 𝑥; 𝜃).  
	Hence, the prediction should fall within 1 ≤ ℎ𝜃 (𝑥) ≤ 0

=> Thus we have [[Logistic Regression]]
# Decision Boundary
[[Decision Boundary]]

# Linear Regression vs Logistic Regression
| Linear Regression                                                                                                  | Logistic Regression                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Data is modelled by a linear  <br>function.                                                                        | Data is modelled by S-shaped  <br>logistic function                                                                    |
| It is necessary that a linear  <br>relationship be established among  <br>dependent and independent  <br>variable. | It is not necessary that a linear  <br>relationship be established among  <br>dependent and independent  <br>variable. |
| The dependent target output, 𝑦 is  <br>continuous.                                                                | The dependent target output, 𝑦 is  <br>discrete.                                                                      |
| ![[Linear Regression Example Another.png]]                                                                         | ![[Logistic Regression Example.png]]                                                                                   |
|                                                                                                                    |                                                                                                                        |
# Cost Function
[[Cost Function]]

# Multiclass Classification
[[Multiclass Classification]]
# Variants of Gradient Descent
See Variants in [[Gradient Descent]]

# Logistic Regression in Python
[[Python]] libraries  
- [[Numpy]]: library for efficient numerical operations.  
- [[Pandas]]: library for data manipulation.  
- [[Scikit-learn]]: library of machine learning tools.  
	linear_model: Implements logistic regression and other linear models.  
	vm: Module for support vector machine algorithms.  
	tree: Module for decision tree-based algorithms.
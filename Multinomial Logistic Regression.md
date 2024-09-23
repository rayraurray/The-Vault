Multiple logistic regression, also known as multinomial logistic regression, is an extension of Binary [[Logistic Regression]] that allows for more than two categories in the dependent variable. It's commonly used when the dependent variable has three or more categories that are unordered.  

In multiple logistic regression, the model estimates the probabilities of each category of the dependent variable and assigns observations to the category with the highest predicted probability.

# Example
To classify the three different species based on the length and width of the sepal:
![[three species based on the length and width of the sepal.png]]

![[Softmax Function.png]]
The softmax function is used to convert raw scores into probabilities while ensuring that the probabilities sum up to 1 across all categories. It's defined as:
![[Defined Softmax Function.png]]
![[Softmax Eval.png]]
# [[Cost Function]]
Multinomial logistic regression has a slightly different loss function than binary logistic  
regression because it uses the Softmax rather than the sigmoid classifier.  

The cost function used in multiple logistic regression is typically the cross-entropy loss  
function. It measures the difference between the predicted probabilities and the actual  
labels. The cross-entropy loss function for multiple logistic regression is given by:

![[Softmax Cost Function.png]]
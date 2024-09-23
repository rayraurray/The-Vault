Logistic Regression is one of the machine learning algorithms used for classification problems.  
It predicts the probability of a categorical dependent variable 𝑦, which could be represented by binary values, 0 or 1, true or false, yes or no.  
In other words, the logistic regression model predicts P( 𝑦 = 1 𝑥; 𝜃 ) as a function of 𝑥, given parameters of 𝜃.

This type of statistical model (also known as _logit model_) is often used for classification and predictive analytics. Since the outcome is a probability, the dependent variable is bounded between 0 and 1. In logistic regression, a logit transformation is applied on the odds—that is, the probability of success divided by the probability of failure. This is also commonly known as the log odds, or the natural logarithm of odds, and this logistic function is represented by the following formulas:

To ensure hypothesis ℎ𝜃 lies between 0 and 1:
**0 ≤ ℎ𝜃 (𝑥) ≤ 1**

**𝑧 = 𝜃0 + 𝜃1𝑥**  
ℎ𝜃 𝑥 is represented as:  
ℎ (𝑥) = 𝑔 (𝑧)
where 𝑔 is a sigmoid function  
![[Sigmoid Function.png]]![[Sigmoid Predict.png]]

# Interpretation of 𝒉𝜽 (𝒙)
ℎ𝜃 (𝑥) = 𝑔 (𝑧) = 𝑔(𝜃0 + 𝜃1𝑥) = 𝑔(𝜃0 + 𝜃1. 𝑤𝑒𝑖𝑔ℎ𝑡)

![[Sigmoid Intepretation.png]]
[[AML]]
# Definition
[[Deep Learning]] is a subset of [[Machine Learning]]
[[Machine Learning]] is a subset of [[Artificial Intelligence]]

-ML is the process of training a piece of software (model) to make a useful prediction of a dataset.
-This predictive model can then serve up predictions about previously unseen data -> taking action.
![[Basic Description of ML.png]]
# Rational Understanding
-Target function 𝑓 is unknown, learning algorithms cannot obtain a perfect function 𝑓.
-Hypotheses function 𝑔 approximates function 𝑓, but maybe different from  
function 𝑓.
![[Target equation in ML.png]]
# Process
-Collect the data
-Prepare the data
	Data processing
	Feature extraction
	Feature scaling and selection
-Modeling (a cycle of):
	Validation
	Hyperparameter tuning
	Training
-Deployment
![[ML development cycle.png]]

# ML and rule-based systems
See all in [[Rule-based System]]
See all in [[Machine Learning]]

![[Rule-based vs ML.png]]

## When to use
| Rule-based                                                                                            | ML                                                                                                                                                                                                            |
| ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Lower volumes of data<br>Relative simplicity<br>Speedy output<br>Clear and constant data distribution | Simple rules, guidelines don't apply<br>Complex rules and intensive issues<br>Long term problem -> Manageability and improvement and enhancement<br>Data distinction changes over time -> Constant adaptation 
# Types of ML algorithms
See all in [[Supervised Learning]]
![[Supervised Learning Example.png]]

See all in [[Unsupervised Learning]]
![[Unsupervised Learning Example.png]]

# Deep Learning
## Definition
See all in [[Deep Learning]]
![[Deep Learning Base.png]]
## ML vs DL

| ML                                 | DL                                          |
| ---------------------------------- | ------------------------------------------- |
| Low hardware requirements          | High hardware requirements                  |
| Applicable for small training data | Applicable for massive training data        |
| Performance cannot be improved     | Performance is high and improving           |
| Level-by-level problem breakdown   | End-to-end learning                         |
| Manual feature selection           | Algorithm-based automatic feature selection |
| Easy-to-explain                    | Hard-to-explain                             |
## Types of DL Networks
See all in [[Convolutional Neural Network]]
See all in [[Recurrent Neural Network]]
## Deep Learning Frameworks
See all in [[Deep Learning Framework]]
See all in [[Noice Deep Learning Frameworks]]
## How does a Neural Network actually learn
See all in [[Neural Network Learning]]
See all in [[Backpropagation]]
# ML Life Cycle
See all in [[Machine Learning Life Cycle]]
# Project Example
## 1. Data Preparation  
- MINIST datasets  
- Training set: 60,000 handwriting images and corresponding labels  
- Testing set: 10,000 handwriting images and corresponding labels
## 2. Network structure definition
![[Project Example Model Design.png]]

## 3. Network Compilation
Model compilation involves the following three parts:  
- Loss function: measures how accurate the output is  
- Optimizer: measures how the model is updated  
- Metrics: monitors the training to determine when to stop
## 4. Model Training
All training data is trained through batch iteration.  
In TensorFlow, model.fit is used for training .  
An "epoch" refers to one complete pass through the entire training dataset.

![[Model Training Example in PyTorch.png]]

## 5. Model Evaluation
In TensorFlow, model.evaluate is used for testing.  
It compares the predicted results with the groundtruth label to calculate the accuracy of the test set.
![[Model Evaluation Example.png]]

# Other things to know
![[Other factors in ML.png]]
# Applications
See all in [[Applications of Machine Learning]]

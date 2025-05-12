A support vector machine (SVM) is a [[Supervised Learning]] algorithm that classifies data by finding an optimal line or hyperplane that maximizes the distance between each class in an N-dimensional space.
It is also called a **large-margin classifier**.
# Why Large-Margin Classifier?

Given N number of data points (training set)  
To classify obese/non-obese ($y$) based on the height $x_1$ and weight $x_2$ of the person, which will be the decision boundary chosen by the SVM?

![[Classify Obese vs Non-Obese.png]]

In SVMs, the distance between the observation vectors of the two domains (positive and negative) is equal to the threshold, which together constitute the margin.  

![[How SVMs work.png]]

Answer is the red line.  
The objective of the SVM algorithm is to find a decision boundary with the **maximum margin**, which is the greatest distance from the nearest data point to the decision boundary.

![[SVM Margin.png]]
- Objective: To find the hyperplane that best separates the classes with the maximum margin.  
- Margin: Distance between the hyperplane and the nearest data points from each class (support vectors).
- For linearly separable data, SVM finds a direct hyperplane that separates the classes.  
- For non-linearly separable data, SVM uses kernel tricks to transform the data into a higher dimension where a hyperplane can be used for separation.
# Kernel Trick
The kernel trick involves transforming data into a higher dimension where it is easier to separate using a linear classifier.  
Common Kernels: Linear, Polynomial, Radial Basis Function (RBF), Sigmoid.  
The choice of kernel affects the decision boundary and the performance of the SVM model.

# Math Intuition

For the positive domain, when data points are just right on the margin, $𝜃^𝑇 𝑥 = 1$, when data points are between decision boundary and margin, $0 < 𝜃^𝑇 𝑥 < 1$  
For the negative domain, when data points are just right on the margin, $𝜃^𝑇 𝑥 = -1$, when data points are between decision boundary and margin, $-1 < 𝜃^𝑇 𝑥 < 0$.
# Non-Linear SVM

The simplest way to separate two groups of data is with a straight line (1 dimension), flat plane (2 dimensions) or an N-dimensional hyperplane.  
However, there are situations where a nonlinear region can separate the groups more efficiently.  Non linear decision boundary is necessary to separate the data points.

![[Non-Linear SVM.png]]
# Loss Function
The loss function is designed to find a decision boundary (a hyperplane in the feature space) that maximizes the margin between different classes while penalizing points that fall on the wrong side of the margin.
The two primary components of the SVM loss function are:
	Hinge Loss
	Regularization Term
## 1. Hinge Loss
Hinge Loss: The hinge loss is used for "maximum-margin". For an individual sample, the hinge loss is defined as:

$$\large L_i = max(0,1 - y_i(w \cdot x_i -b))$$

where $w$ represents the weights of the model, 
$x_i$ is the feature vector of the i-th sample, 
$b$ is the bias term, 
$y_i$ is the actual class label for the i-th sample, which should be -1 or 1. 

The term $w⋅x_i−b$ is the raw output of the classifier. If this output is correct and beyond the margin, the loss is 0. Otherwise, the loss increases linearly with the distance from the margin.
## 2. Regularization Term

To prevent the model from overfitting, a regularization term is added to the loss function. The most common form in SVMs is the L2 regularization, which is the squared magnitude of  
the weight vector $w$.
## 3. Complete Loss Function
Complete SVM loss function with the regularization term is given by:
$$\Large J(w) = \frac{\lambda}{2}||w||^2 + \frac{1}{N}\sum^{N}_{i=1}max(0,1 - y_i(w \cdot x_i-b))$$
where $\large \lambda$ is a regularization parameter that controls the trade-off between increasing the margin size and ensuring that the xi lies on the correct side of the margin. 
$\large N$ is the number of training samples. 
A smaller value for $\large \lambda$ implies less regularization (allowing more complexity in the model), whereas a larger $\large \lambda$ promotes simplicity in the model at the risk of not capturing all the nuances in the data.

## 4. Loss Function with C
In many descriptions of SVMs, particularly in the context of scikit-learn or other practical machine learning libraries, you might encounter the regularization parameter denoted as C rather than λ. The formulation with C looks like this:

$$\Large J(w) = C\sum^{N}_{i=1}max(0,1 - y_i(w \cdot x_i-b)) + \frac{1}{2}||w||^2$$

A large value of C corresponds to assigning a higher penalty to misclassified points, essentially prioritizing the correctness of classification over the width of the margin. Conversely, a smaller C value emphasizes a larger margin and allows more misclassifications.

## 5. Large C Effect
However, model with large C value is sensitive to outliers, similar to no regularization.  
Such a model is subject to overfitting (lower bias, higher variance).

![[Large C Effect.png]]

## 6. Small C Effect
Smaller C allows a bigger margin. It is useful for non-linearly separable dataset with tolerance of data points who are misclassified or have margin violation.

![[Small C Effect.png]]

However, a model with a too small C value is subject to underfitting (Higher bias, lower variance).
# Function $f$
𝑓 is a similarity function which is called a kernel function. It is used to map the data into  
a different space when a hyperplane (linear) cannot be used to do the separation.  
A non-linear function is learned by a linear learning machine in a high-dimensional feature space while the capacity of the system is controlled by a parameter that does not depend on the dimensionality of the space.  
This is called kernel trick which means the kernel function transform the data into a higher dimensional feature space to make it possible to perform the linear separation.

![[Function f.png]]


Multiple logistic regression, also known as multinomial logistic regression, is an extension of Binary [[Logistic Regression]] that allows for more than two categories in the dependent variable. It's commonly used when the dependent variable has three or more categories that are unordered.  

In multiple logistic regression, the model estimates the probabilities of each category of the dependent variable and assigns observations to the category with the highest predicted probability.

To classify the three different species based on the length and width of the sepal:
$$ \Large
C = [\text{setosa}, \text{versicolor}, \text{verginica}]
$$
$$ \Large
y^{(n)} \in \{1, 2, 3\}
$$

| Sepal Length, $\large x_1$ | Sepal Length, $\large x_2$ | Species    | y   |
| -------------------------- | -------------------------- | ---------- | --- |
| 5.1                        | 3.5                        | setosa     | 1   |
| 4.9                        | 3                          | setosa     | 1   |
| 6.7                        | 3.1                        | versicolor | 2   |
| 6.7                        | 3.3                        | virginica  | 3   |
| ...                        | ...                        | ...        | ... |
$$ \Large
z = [z_{\text{set.}},z_{\text{vers.}}, z_{\text{verg.}}] = [z_1, z_2, z_3]
$$
where:
$$\Large
z_c = \theta^{(c)}_0 + \theta^{(c)}_1 x_1 + \theta^{(c)}_2 x_2 = \theta^{(c)T}x 
$$
and
$$\Large
h_\theta(x) = \text{softmax}(z)
$$
# Softmax Function
The Softmax Function is used to convert raw scores into probabilities while ensuring that the probabilities sum up to 1 across all categories. It's defined as:
$$\Large
\text{softmax}(z_c)=\frac{e^{z_c}}{\sum^K_{k=1} e^{z_k}}
$$
where:
$\large z$ is a vector of raw scores. 
$\large K$ is the total number of classes.
$\large \text{softmax}(z_c)$ is the probability of category $\large c$ given the raw scores.

In our previous example:
$$ \large
z = [z_{\text{set.}},z_{\text{vers.}}, z_{\text{verg.}}] = [z_1, z_2, z_3]
$$
where:
$$\large
z_c = \theta^{(c)}_0 + \theta^{(c)}_1 x_1 + \theta^{(c)}_2 x_2 = \theta^{(c)T}x 
$$
Then:
$$\large
h_\theta(x) = \text{softmax}(z) = 
\begin{bmatrix}
\frac{e^{z_1}}{\sum^3_{i=1}e^{z_i}} \\
\frac{e^{z_2}}{\sum^3_{i=1}e^{z_i}} \\
\frac{e^{z_3}}{\sum^3_{i=1}e^{z_i}}
\end{bmatrix}
=
\begin{bmatrix}
P(y = \text{setosa} | x) \\
P(y = \text{versicolor} | x) \\
P(y = \text{verginica} | x)
\end{bmatrix}
$$
Cont.:
$$ \large
C = [\text{setosa}, \text{versicolor}, \text{verginica}]
$$
$$ \Large
h_\theta(x) = \text{softmax}(z) = 
\begin{bmatrix}
0.8 \\
0.15 \\
0.05
\end{bmatrix}
$$
Then $\large y$ = 1
# [[Cost Function]]
Multinomial logistic regression has a slightly different loss function than binary logistic regression because it uses the Softmax rather than the Sigmoid classifier.  

The cost function used in multiple logistic regression is typically the cross-entropy loss function. It measures the difference between the predicted probabilities and the actual labels. The cross-entropy loss function for multiple logistic regression is given by:
$$\Large
J(\theta) = - \frac{1}{N} \sum_{i=1}^{N} \sum_{k=1}^{K} y_{ik} \log(\hat{p}_{ik})
$$
where:
$\large \theta$ represents all the parameter vectors.
$\large N$ is the number of observations.
$\large y_{ik}$ is an indicator variable equals that equals 1 if observation $\large i$ belongs to category $\large k$, and 0 otherwise.
$\large \hat{p}_{ik}$ is the predicted probability that observation $\large i$ belongs to category $\large k$.

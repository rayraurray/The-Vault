A neural network is a [[Machine Learning]] program, or model, that makes decisions in a manner similar to the human brain, by using processes that mimic the way biological neurons work together to identify phenomena, weigh options and arrive at conclusions.
# Understanding ANN
The human brain has hundreds of billions of cells called neurons. Each neuron is made up of a cell body that is responsible for processing information by transporting information to (inputs) and from (outputs) from the brain.

Artificial neural networks are built like the human brain. It has hundreds or thousands of artificial neurons which are interconnected. The input neurons receive various forms of data and, based on an internal weighting system, the neural network learns the patterns of the data and matches them to the target output.
![[Anne.webp]]

# Neuron Model
Neural network consists of stack of neurons that takes in input $x$ and output predicted value $ℎ_𝜃(𝑥)$  
Given enough number of neurons, neural network are incredibly good at mapping input $x$ to the actual output $y$.

![[Neuron Model for ANN.png]]
## Single Hidden Layer
![[Single Hidden Layer ANN.png]]

## Notation used in computation:  
$\large a^{(j)}_i$ : activation of neuron $i$ in layer $j$

$\large 𝜃^𝑗$: matrix of weights make up the mapping function from layer $j$ to $j + 1$  

$\large s^j$: number of neurons in layer 𝑗 not including bias
## Matrix Format:
$\large z^{[l]} = W ^{[l]} a^{[l-1]} + b^{[l]}$
$\large a^{[l]} = g ^{[l]} (z^{[l]})$

Note that, if the network has $s_j$ neurons in layer $j$ and $s_{j+1}$ neurons in layer $j+1$, then, the  
matrix dimension for $𝜃_j$ is  
$\large s_{j+1} × (s_j+1)$
# Calculations
![[Calcs in ANN.png]]

# Cost Function (Classification)
Terminology used:  
$K$ : number of output neurons  
$L$ : total number of layers in network  
$s_1$: Number of neurons in layer 𝑙 (not including bias)  

- For multiclass classification ($K$ classes where $K ≥ 3$)  
$\large y \in \mathbb{R}K$  
$\large h_𝜃 (x) \in \mathbb{R} K$  
- For binary classification:  
$\large y \in 0,1$  
$h_𝜃(x) \in \mathbb{R}$

# Forward Propagration
![[Forward Propagation.png]]

# Backward Propagation
1. **Input:** given N number of data points (training set) = ($x_2$ , $y_2$ ), ..., ($x_N$ , $y_N$)  
2. **Feedforward:** For each $\large l = 1,2, ..., L$, compute $\large z^{(l+1)} = 𝜃^{(l)} 𝑎^{(l)}$ and $\large a^{(l+1)} = g(z^{(l+1)})$
3. **Output Error:** Compute $\large \delta ^ {(L)}$  
4. **Backpropagate the error:** For each $\large l = 2, ..., L$ compute $\large \delta^{(l)}$
5. **Gradient computation:** Compute weights $\Large \frac{\delta J(\theta)}{\delta \theta ^{(l)} _{j}}$ and biases $\Large \frac{\delta J(\theta)}{\delta \theta ^{(l)} _{k}}$
7. **Optimization algorithm:** You can use any gradient descent optimization algorithm to minimize the error function $J(𝜃)$.

![[Backprop.png]]
## Intuition
Backward propagation computes the error term $\large \delta^{(l)}$ from the right to the left.  
E.g. $$\Large \delta^{(L-2)}_1 = \theta^{(L-2)}_{11}\delta^{(L-1)}_1 + \theta^{(L-2)}_{21}\delta^{(L-1)}_2 + \theta^{(L-2)}_{31}\delta^{(L-1)}_3$$Measure of how much will we like to modify the weights 𝜃 𝑙 in order to affect this intermediate value of the calculation so as to influence the final result $h_\theta (x)$ and the cost function $J(\theta)$.

# Random Initialization for $\large \theta$
By initializing the same weights for all layers, all hidden units calculate the same function.  
This is equivalent to learning the same features for each neuron in a hidden layer.  
To break the symmetry, initialize with random number (small value close to zero).


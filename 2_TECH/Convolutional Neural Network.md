# Definition
Convolutional [[Neural Network]] (ConvNets or CNNs) is a deep learning model which was initially designed to work with two-dimensional image data. It can be used also with both one and three-dimensional data.

CNN are particularly well-suited for data that has a spatial (or temporal) locality relationship. This characteristic is most evident in tasks involving images, videos, and even audio or time series data, where the relationship between nearby elements is crucial for understanding the overall structure and content of the data.

CNNs are used mainly for [[Image Classification]], Processing, Segmentation, Object Detections and also for other auto correlated data.

![[cnn.png]]

In a typical CNN, each input image will pass through a series of convolution layers with filters (or kernals), pooling, fully connected layers (FC) and apply the softmax function to classify an object with probabilistic values between 0 and 1.

![[cat cnn.png]]

# Convolutional Layer
A convolutional layer is **the main building block of a CNN**. It contains a set of filters (or kernels), parameters of which are to be learned throughout the training.

Main functionalities:
- Feature detectors  
- Generate feature maps by convolving input with filters  

To compute the pixel value $\large i$ of an $\large r$-th feature map for layer $\large l$, we use:
$$\Large
x^{(l)}_i = g(\sum^k_{j=1}x^{(l-1)}_j \space*\space w^{(l-1)}_j \space+\space b^{(l-1)}_i)
$$
where:
$\large g(\cdot)$ is an activation function
$\large x^{(l-1)}$ is one of the input regions
$\large w^{(l-1)}$ is the filter with size of $\large N \times N$
$\large b_i$ is the bias
$\large k$ is the total pixel of filter
$\large *$ is elements wise multiplication
![[c layer cat.png]]

## Mathematic Operations
### Scenario 1
Consider a 2 dimensional input feature map, $\large x^{(l−1)}$ with size $= (d, d) = (5,5)$ 

**Parameters:**
$\large w^{(l-1)}$ filter size = $\large (N, N) = (3,3)$
Stride (number of pixel shifts over the input matrix): $\large s = 1$
Padding: None

$\large x^{(l)}$ feature map's output size $\large = \frac{d-N}{s} + 1 = \frac{5-3}{1} + 1 = 3$

![[feature map output size.png]]

![[cnn calc.png]]
### Scenario 2
Similarly, If:
- Padding = (1,1)
- Input Image size: (7,7)
- Feature map's output size $\large = \frac{7-3}{1} + 1 = 5$

![[7x7 paddin.png]]
### Scenario 3
Similarly, if:
- Input image's size: (5, 5)
- Feature map's output size $\large = \frac{5-3}{1} + 1 = 2$
![[5x5 cnn.png]]

$\large \rightarrow$ **Thus, N number of filters produces N number of feature maps.**
![[feature maps.png]]

If we use a convolutional layer with 1 filter of size $m* m * r = 6*6*3$. then the output is a matrix of dimension $(n+1-m)*(n+1-m)=27*27$

Input is a multi-array of a tensor, because it has 3 color channels:
$$\Large x \in \mathbb{R}^{n\times n \times r}$$
Typical convolutional layer has multiple filters to capture multiple patterns.
Each one is called a channel
Each channel has a filter of the same size $m* m * r$ but with different weights
Each channel outputs a matrix of dimension $(n+1-m)*(n+1-m)$
Put together the output is a tensor of dimension $(n+1-m)*(n+1-m)*D$
## Weights Sharing
Weight sharing happens across the **receptive field** of the neurons(filters) in a particular layer. Weights are the numbers within each filter.  

So essentially we are trying to **learn a filter**. These filters act on a certain receptive field/ small section of the image.  

When the filter moves through the image, the filter does not change. The idea being, if an edge is important to learn in a particular part of  
an image, it is important in other parts of the image too.  

Weight sharing is to provide **translation invariance** (allows the  
network to recognize the same object in an image no matter where it  
appears) , which is fundamental to image-based recognition.
## Translation Invariance
![[Translation Invariance.png]]
## Sparsity of Connection
The sparsity of connection means that each element of the output  
**depends only on the small section** of the input.  

For example, an element in the output of convolutional layer with 3 x 3 filter will depend only on 9 numbers from the input.  

As we get deeper into the network, the outputs will depend on less and  
less numbers.  

This allows us to train with less samples and prevent overfitting.
![[connection sparsity.png]]

## Activation Function
The $\large g(\cdot)$ is an activation function that maps the input signals into output signals that are needed for the neural network to function.

Increasingly, neural networks use **non-linear activation functions**, which can help the network learn complex data, calculate and learn almost any function representing a question, and provide accurate predictions.
![[activation function.png]]
### Sigmoid and Tanh
Traditionally, two widely used nonlinear activation functions are the **sigmoid** and **hyperbolic tangent** activation functions.

- **Sigmoid:**
$$\Large
g(z) = \frac{1}{1+e^{-z}}
$$
![[sigmoid af.png]]
- **Hyperbolic Tangent:**
$$\Large
g(z)=\tanh(z)
$$
![[tanh af.png]]

- **Restrictions:**
Limited sensitivity and saturation of the function: Large values snap to 1.0 and small values snap to -1 or 0 for tanh and sigmoid respectively. The functions are only really sensitive to changes around their mid-point of their input, such as 0.5 for sigmoid and 0.0 for tanh.  

Vanishing gradient (details will be explained later): In a feedforward network, the back propagated error typically decreases exponentially as a function of the distance from the final layer, resulting in the model impossible learn.

Computationally expensive.
### ReLU
ReLU stands for Rectified Linear Unit for a non-linear operation. The  
output is: $$
\Large f(x) = \max(x)
$$ Why ReLU is important :  
‘Because rectified linear units are nearly linear, they preserve many of the properties that make linear models easy to optimize with gradient-based methods. They also preserve many of the properties that make linear models generalize well.’ − Page 175, Deep Learning 2016
![[relu af.png]]

### Other AFs
![[other afs.png]]

# Pooling Layer
Pooling layers are **responsible for reducing the spatial dimensions of the input, controlling overfitting, and extracting dominant features**.

Main functionalities:
- Feature selection  
- Improve generalization  
- Pooling method  
	Max pooling  
	Min pooling  
	Average pooling  
	etc.

Similarly:
$$\Large
x_i^{(l)} = \max(x^{(l-1)})
$$
where:
$\large x_i^{(l)}$ is the output pixel.
$\large x^{(l-1)}$ is one of the input window region of the $\large r$-th feature map.
![[Pooling Layer.png]]
## Mathematic Operations
### Scenario 1
Consider a 2 dimensional input feature map, $\large x^{(l−1)}$ with size $= (d, d) = (5,5)$ 

**Parameters:**
$\large w^{(l-1)}$ filter size = $\large (N, N) = (3,3)$
Stride (number of pixel shifts over the input matrix): $\large s = 1$
Padding: None

$\large x^{(l)}$ **pooled** map's output size $\large = \frac{d-N}{s} + 1 = \frac{5-3}{1} + 1 = 3$
![[pooled map wat.png]]
![[pooled map calc.png]]
### Scenario 2
Similarly, If:
- Padding = (1,1)
- Input Image size: (7,7)
- Feature map's output size $\large = \frac{7-3}{1} + 1 = 5$
![[pool 7x7.png]]
### Scenario 3
Similarly, if:
- Input image's size: (5, 5)
- Feature map's output size $\large = \frac{5-3}{1} + 1 = 2$
	![[pool 5x5.png]]
# Fully Connected Layer
![[fully connected layer.png]]

In a fully connected (FC) layer, each neuron is connected to every neuron in the previous layer, and each connection has it's own weight, as seen in regular ANN.  

In contrast, in a convolutional layer, each neuron is only connected to a few nearby (local) neurons in the previous layer, and the same set of weights (and local connection layout) is used for every neuron.
![[FC layer.png]]

# Replacing FC with Convolutional Layer
The benefit of replacing a fully connected layer with a convolutional layer is that the number of parameters to adjust are reduced due to the fact that the weights are shared in a convolutional layer.  

It provides faster and more robust learning.
![[Replacing FC with Convolutional Layer.png]]
## FC Layer
- FC Layer (18914, 4096):
$$ \large
\text{Parameters} = (18914+1) \times4096=18915\times4096=77,480,640 \space \text{parameters}
$$
- FC Layer (4096, 1000):
$$ \large
\text{Parameters} = (4096+1) \times 1000=4097\times 1000=4,097,000 \space \text{parameters}
$$
## Convolutional Layer
- Conv Layer with Filter Size (7,7):
The input shape is (7, 7, 386), and the output shape is (1, 1, 386)
$$ \large
\text{Parameters} = 7 \times 7 \times 386 \times 386 = 7,304,884 \space \text{parameters}
$$
- Conv Layer with Filter Size (1, 1) from (1, 1, 386) to (1, 1, 4096):
$$ \large
\text{Parameters} = 1 \times 1 \times 386 \times 4096 = 1,581,056 \space \text{parameters}
$$
- Conv Layer with Filter Size (1, 1) from (1, 1, 4096) to (1, 1, 1000):
$$ \large
\text{Parameters} = 1 \times 1 \times 4096 \times 1000 = 4,096,000 \space \text{parameters}
$$
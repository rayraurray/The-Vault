[[Convolutional Neural Network]]

An Inception layer is a CNN module combining parallel convolutions of various filter sizes and pooling, concatenated to capture features at multiple scales.

Inception Layer is a combination of all those layers (namely, $1\times1$ convolutional layer, $3\times3$  convolutional layer, $5\times5$ convolutional layer) with their output filter banks concatenated into a single output vector forming the input of the next stage.  

$1\times1$ Convolutional layer before applying another layer is mainly used for dimensionality reduction.

A parallel Max Pooling layer provides another option to the inception layer.

![[inception layer.png]]

The intuition behind of inception layer is to allow the internal layers to pick and choose which filter size will be relevant to learn the required information.  
	E.g., it would probably take a lower filter size for the left image and a higher filter size for the right image.
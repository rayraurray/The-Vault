[[Convolutional Neural Network]]

Individual nodes are either dropped out of the net with a $\large 1-p$ probability or retained with a $\large p$ probability.  

The inbound and outbound edges to a dropped-out node are also removed.  

For example, Dropout(0.5), a new set of nodes is randomly chosen to be dropped based on the specified dropout rate.

![[dropout.png]]
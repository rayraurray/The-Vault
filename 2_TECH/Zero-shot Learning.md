Zero-shot learning (ZSL) enables identification of classes that are not seen before by means of transferring knowledge from seen classes to unseen classes.

This knowledge transfer is usually done via utilizing prior information from various auxiliary sources, such as descriptions/semantic attributes/word embedding's (vector representations of a particular word).

For example, consider a scenario where an AI model is trained to classify various animals using a collection of images and their descriptive texts. If this model, which knows how to identify horses, is provided with descriptions stating that zebras are essentially striped horses, it can recognize a zebra image accurately, even though it has never explicitly been trained on images of zebras.

Auxiliary Info Example:
![[Auxiliary Info Example.png]]

# Main Idea
The aim is learn a projection function from visual space (i.e. image features) to semantic space (i.e. word vectors/semantic embedding) using data from seen classes.

Then, the unseen class image features are passed as input to the trained network and we get the corresponding semantic embedding as the output.

Nearest neighbor search is perform in the semantic embedding space to find the closest match to the output of the network. Finally, the label corresponding to the closest semantic embedding is predicted as the output label of the input image feature.

![[Zero-shot Learning.png]]
One-shot learning is a variant of transfer learning where we try to infer the required output based on just one or a few training examples

It emphasize on knowledge transfer, which makes use of prior knowledge of learnt categories and allows for learning on minimal training examples.

![[One-shot Learning.png]]

# Problem of Naïve Convolutional Network
A small training set is not enough to train a robust neural network. The trained feature vectors do not contain important information that can be used for future image recognition.

Retraining the convolutional network every time the number of classes or dataset is increased is way too time-consuming and resource-intensive.

# Main Idea
Train a model to differentiate between the same and different pairs, then generalize these ideas to evaluate new categories.

Learning a similarity function The deep learning model takes two images and returns a value that shows the similarity between the two images.
![[One-shot Learning 2.png]]

If the images contain the same object (or the same face), the neural network returns a value below a specific threshold, $\large \lambda$ (say zero) and if they are not the same object, it will be above the threshold.

![[One-shot Learning 3.png]]

If $\large d(img_1, img_2) \le \lambda \rightarrow \text{same}$
else  $\large d(img_1, img_2) > \lambda \rightarrow \text{not same}$ 
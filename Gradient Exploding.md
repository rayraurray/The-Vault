Gradient exploding is a problem in training deep neural networks where gradients can grow exponentially during backpropagation, causing very large weight updates and leading to numerical instability.  

This often results in model training failure, with weights becoming NaN (not a number) or diverging to infinity. It's especially prevalent in architectures with many layers.
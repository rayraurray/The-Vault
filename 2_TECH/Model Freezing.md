[[Machine Learning]]
[[Deep Learning]]
[[Transfer Learning]]

Model Freezing is the process of “locking” several chosen weights of the neural network. In other words, the **frozen weights of the model do not change** (zero gradient flows into them), so the encoder is locked in place so it doesn't degenerate to conserve computational resources by reducing the number of trainable parameters.
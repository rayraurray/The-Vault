# 1. Determine your goals
What is the problem you intend to solve? Classification problem? Regression problem? The problem will define the loss function as well as the target label.  
Case studies: As part of the automatic parking system, a new car payment system based on the authentication of license plate numbers will be proposed. An automated system for the registration of cars entering the car park must therefore be put in place.  

Problem to solve:  
- Car license plate recognition for automatic parking system  
- Both regression and classification problem involved as you have to detect where the license plate is located (regression) and what the license plate numbers/characters are (classification).
# 2. Establishing a working end-to-end pipeline
Establish an appropriate performance metrics such as precision, recall, cosine similarity matrices and etc. And, deployment of baseline models for initial experiment

Data collection: collect raw data and provide label.  

Performance metrics for multi-class classification (A-Z characters, 1-9 numbers):  
- Top-1 or Top-5 accuracy  
- Mean average precision (mAP): calculate the average precision (AP) for each class and then average among all classes  

Performance metrics for object detection (car license plate):  
- Intersection over Union (IOU)
- Precision and Recall
- mAP
- 
Default Baseline models:  
- Determine the complexity of your problem to decide between deep and non-deep approaches. (Since our problem falls into an ‘AI-complete’ category, hence deep learning model is recommended)  
- Choose a model based on the structure of your input data: fixed size vectors (FC), image (CNN), sequential data (RNN). (Our problem will be dealing with images, hence CNN is recommended)  
- CNN architecture for object detection: R-CNN, Fast- RCNN, Faster- RCNN, YOLO (we will discuss this in the future lecture)  
- CNN architecture for character classification: AlexNet or VGG. (Choose the network according to the complexity of your data)
# 3. Determine the bottlenecks in performance
Overfitting? Underfitting? Defect in the data or software?

Problems that may be encountered in modeling deep neural network:  
- [[Overfitting]]  
- [[Underfitting]] 
- [[Gradient Exploding]]  
- [[Gradient Vanishing ]] 
- Data and software defect
## Solution to Overfitting
- Gather more training data  
- Dataset augmentation: Translation, flip, mirror, noise, colour augmentation and etc.  
- Reduce the complexity of the network: increase number of neurons, layers and weights parameters.  
 - Apply regularization techniques: L1/L2 weight decay, dropout, early stopping
## Solution to Underfitting
- Increase the model complexity: add new layers, increase number of neurons  
- Increase training time  
- Reduce dropout
## Solution to Gradient Exploding
- Gradient clipping: forcing the gradient values (element-wise) to a specific minimum or maximum value if the gradient exceeded an expected range.  
- Use smaller learning rate  
- Weight regularization  
- Data preparation: [[Data Normalization]]  
- Re-design the network to have fewer layers.
## Solution to Gradient Vanishing
- Use ReLU activation instead of Sigmoid: Sigmoid function squishes a large input space into a small input space between 0 and 1. Therefore, a large change in the input of the sigmoid function will cause a small change in the output. Hence, the derivative becomes small.  
- Use residual based network: It provides residual connections straight to earlier layers.  
- Batch normalization: It forces the activations of a layer to follow a single distribution, independent of the changes in the parameters of upstream layers  
- Combine careful initialization of weights
# 4. Repeatedly make changes to improve the system
Increase dataset size, adjust hyperparameters, changing algorithm. 

Qualitative analysis: Observe the windows detected by the trained model to find out whether car license plates are captured.  

Quantitative analysis: Examine the misclassification made by the network using the returned softmax probability. For example, the model may incorrectly identify the character Q as 0, which may be due to incorrect labels of the data.

Fit a tiny data: Bugs in algorithms are often difficult to catch. Try to fit the model using a tiny data (says 5 or 10 samples) and check the results.

Monitor the learning curves
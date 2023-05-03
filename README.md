# Neural-Networks-Project


**Instructions:**

- Open NeuralNetworksProject.ipybn file in Google Colab and run each cell in file
- Open “Neural Networks Project Presentation.pptx” to view extra credit presentation


**Database Description:**

The test database is similar to the previous database used. It takes a random 20% sample of the initial database to get 60 data objects. Each data object contains two images; one image is a genuine signature and the other is either a genuine signature or forged signature. The network is designed to predict whether the second image is genuine or is a forged signature of the first image in the data object. This testing data has not been seen by the model before so it should be a good representation of the generalization capabilities of the developed model. 


**Classification Accuracy:**

- Training Accuracy: 89.44%
- Validation Accuracy: 60.00%
- Testing Accuracy: 46.67%


**Commentary:**

The training accuracy obtained is significantly higher than the training accuracy I had obtained in the previous project update. One cause of this change was experimentation with different optimizers before settling on using a Stochastic Gradient Descent optimizer. A more significant change was the calculation of my distance function that is used to create predictions. The contrastive loss function calculates the Euclidean distance between the two images. Then, the distance is subtracted from a margin (which I identified to be 0.4 for best results). If the difference is negative, then the signature in question is real, while if the difference is positive, then the signature is fraudulent. Finding the right value for the margin allowed the model to make better predictions and hence, an increase in accuracy.
  
As expected the testing set performed worse than the training set and validation set. There are multiple reasons why this potentially occurred. This is likely due to overfitting of the model. In other words, the model is learning the noise that is associated with the training set too well and is unable to recognize what the data is supposed to look like when it reaches the testing set. To address this issue, I could reduce the number of epochs. This would likely decrease the training accuracy but would potentially increase the testing accuracy because the model would not have been trained to recognize noise in the data. Another potential solution would be to use cross validation. This would limit overfitting because it would use different parts of the dataset as validation, which would reduce the noise when the process is repeated multiple times. When using this proposed cross validation, we would want to see similar performance within all the different subgroups. While the testing accuracy is lower than desired, the model performed well with the training set and validation set.


# Neural-Networks-Project

**Instructions:**

- Open NeuralNetworksProject.ipynb file in Google Colab and run each cell in file

**Network Architecture:**

This project utilizes a Siamese Neural Network. A Siamese Neural Network is a combination of 2 separate networks to form one final output. In this case, I use two Convolutional Neural Networks, one for each image being compared at a given point in time. The two Convolutional Neural Networks share identical structures, but each image is passed through the network separately. First there are 5 convolutional layers, starting with one input channel and the last one outputting 256 channels. The networks also utilize standard ReLu activation functions along with max pooling layers. There are also two batch normalization layers to normalize the different elements of a batch; one layer has 96 channels and the other has 256 channels. These values were selected to match the prior layers of the network. Finally, there are linear layers to apply linear transformations to the data. The second of these fully connected layers outputs 10 features. This description of the Convolutional Neural Networks helps define the outputs that will be used to create the prediction of a real or forged signature. 

The loss function used for this Siamese Network is Contrastive Loss. Contrastive Loss measures the distance between the outputs of two images. Two images that are similar will have a small distance between them, indicating that they are both real signatures. Meanwhile, a forged signature will have a large distance between itself and the real signature. For this implementation of Contrastive Loss, I used Euclidean distance which simply finds the pairwise distance between the two images. For the optimization function, I used Adam which uses gradient descent to update the weights of the network at each epoch. After some experimenting with various optimization algorithms, this one proved to be the best by providing an increase in accuracy scores.

**Accuracy:**

- Training Accuracy: 50.56%
- Validation Accuracy: 53.33%

**Commentary/Potential Improvements:**

The first thing I notice is that the accuracy is as good as a random guess. Since there are only two potential classifications, a 50% accuracy would be the expected accuracy of a random guess. However, it is interesting that the Validation Accuracy was higher than the Training Accuracy. While this difference was fairly small, it is possible that I am overfitting my model. To combat this I would likely want to restructure my Siamese Network to potentially eliminate a few layers. Increasing the number of epochs could also help improve performance by giving the model more time to learn. On the other hand, the small difference between the training accuracy and validation accuracy could just be the result of a different portion of the dataset and therefore not a significant issue with the network. Regardless, I think it is also worthwhile for me to explore using different distance calculations to make predictions. For example, instead of using Euclidean distance, I could try using Cosine Similarity Distance. This could potentially provide a higher accuracy for my model.

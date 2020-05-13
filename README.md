# Fully-Connected-Neural-Net.-vs-CNN
What's Happening: Running accuracy tests for 3 different ways of setting up a learning model to see which works best for image processing using the cifar10 dataset.

-The first model is your standard fully connected layer. However, since images are a bit larger than what is preferered I needed to scale them in order to reduce their size without compromising their integrity. I then shuffled the dataset in an attempt to combat any sort of fitting issues, flattened the images into a single vector for ease of use, and created a confusion matrix for the actual classification. Lastly, the learning model is created.

-The second model is set up the same, but the model has a few tweaks implemented: I added a dropout layer (Drops 20% of the data) in an attempt to prevent the model from learning how to classify the data its used to rather than actually learning, changed the optimizer from Adam to SGD, and added a momentum of .9. 

-The last model is designed to be a Convolutional Neural Network. The only changes in the setup before creating the model is the images no longer need to be scaled since CNNs use filters to process image data and also no longer need to be flattened; However, the layers in the model are flattened. The model now uses filters of a specified size(which I set to be 3x3) and max pooling is used to maintain the the integrity of the image.

*All tests are run for 50 epochs and a save path is used in order for the models to save the best version of theirselves.

Results:

Fully Connected:
-The training and validation accuracy for the first model are terrible, with both finishing at about 50%. Although the rate at which the data converges seems to be fine, where it converges shows that this model couldn't be used for reliable classification. The loss is also inconsistent, as it jumps up and down and ends with a value greater than 1.

-In the second model, there was a noticable increase in the preformance of the system. The average accuracy jumped from around 50% to above 90% in both the training and validation sets. However, when looking at the graph of the system's progress, it's clear that the the data is not converging at an appropriate rate (much too fast), and the validation data begins to show signs of stagnating towards the end of the test run even though the testing data continues to improve in accuracy. Based on these first 50 epochs, it has become apparent that if the tests were to be run for twice the amount of epochs there would be a noticable decrease in preformance. 

CNN:
-The first major difference I noticed when comparing this model to the previous 2 was the total number of parameters in each network. Both FC models contain over 26 million parameters which is outrageous compared to the CNNs 1.2 million. In terms of accuracy, the CNN outpreforms the first FC network by about 30%. Compared to the second FC network model, at first glance, it seems that the FC network beats the CCN by 7%. I found that in this case it was critical that the graphs of the models' progress be examined. In the FC network, the graph show that the model converging too quickly and begins to decrease in terms of preformance towards the end of the 50 epochs. In the CNN the graph converges at an acceptable rate and even shows signs of improving towards the end of the 50 epochs.

Conclusion:
-The Convolutional Neural Network has proven to be the more cost effective and reliable way to handle image classification. While the loss in this trial could stand to be changed for improvements, the overall results of the tests still point to this method being more appropriate.

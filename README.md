
# Asignment

# Modified MNIST Network for Classification and Addition

The objective is not only predict the number from the MNIST dataset , but also predict the sum of the random number (0-9) added to it.

## Input Data Pre-processing

Build a combined dataset using

*  torchvision MNIST
*  Add random numbers between 0-9 as the second input
*  2 outputs : predicted number and sum of predicted number

### Data Representation
> The input data is created using a list. The first element of the list is the batch of images and the second element is the batch of random numbers to be added.

### Data Generation Strategy
> The data is created using the class Combined_Dataset. This class creates train or test data based on the input paramter train (True or False). It has the function __getitem__ which appends one batch of image to one batch of random numbers and returns this list. Upon calling next(iter()) on the object of this class, one batch ([images, random_numbers]) is yielded.

# Network Design and Combination of Input

* First, convolution blocks use the images as input
* **After the convolution part, we concatenate the 2nd input (random number) with the argmax of convolution output**
* Stack the tensors to get pairs of numbers and pass them through the linear layers
* There is no activation function required during addition of two numbers as it is a linear function

![image](https://user-images.githubusercontent.com/73247157/211079017-18307d9c-3861-45ba-8113-8a135ebf3b6b.png)

## Training and Loss

* Number of epochs : 10
* Loss - as there are 2 components - image detection and sum - 2 loss functions are used 

### Loss function

> The loss functions picked are -
> 1. Crossentropy loss for the image classification part of the network.
> 2. Mean squared error loss for the addition part of the network. As adding two numbers is a regression problem, we use MSE loss to find the relationship between input and output. Here, CE loss is not effective as changing the range of inputs (from 0-9 to say 0-99) will lead the network to not work. However, MSE loss will still work although it might yield poor results. For this case, the network can be easily retrained.

![image](https://user-images.githubusercontent.com/73247157/211079148-82a416fe-c5f1-4921-8c98-6fc38cad7b1d.png)


## Evaluation
> The network is evaluated by calculting the accuracy for the classification problem and the addition problem. For the addition problem, we have rounded off the final prediction to the nearest integer and then compared it with the target variables. It can be noticed that both the accuracies are same which means the addition part of the network is working 100% and gives the result as good as the classification.

![image](https://user-images.githubusercontent.com/73247157/211079270-97de0434-cd94-4b39-b4d2-573d755677c6.png)


## Observations/ Learning

* The model is able to predict the number and the sum very well
* Equal weightages were given to both the CE loss and MSE loss
* No activation function was used during addition of two numbers as it was a linear function

# PART 1

# Train a Simple Neural Network using Microsoft Excel

### Neural Network Diagram
<img width="539" alt="image" src="https://user-images.githubusercontent.com/73247157/120009954-33663e80-bffa-11eb-98b3-d7e235a1724a.png">


> 1. Draw the neural network diagram as shown in the figure.
> 2. Connect all the neurons using arrows and mark them with appropriate names and values.

---

### FeedForward Equations
![image](https://user-images.githubusercontent.com/73247157/120010011-46790e80-bffa-11eb-8809-5283b09cb3c9.png)

> 1. Write all the feedforward equations using the above diagram as reference.
> 2. Use sigmoid as the activation function for the hidden and output layers.

---

### Backpropagation Equations
![image](https://user-images.githubusercontent.com/73247157/120010087-5c86cf00-bffa-11eb-913b-bdfaba575aee.png)


### Training the Neural Network
![image](https://user-images.githubusercontent.com/73247157/120010232-863ff600-bffa-11eb-9e09-27d118ed0aee.png)


> 1. Initialize all the values of the neurons and weights as shown in the neural network diagram.
> 2. Write the equations of the weights and their gradients using the above equations and choosing the right cell numbers.
> 3. Use a constant learning rate to update the weights. This will be changed to observe the effect of learning rate on loss during training.
---

### Loss Graphs
<img width="736" alt="image" src="https://user-images.githubusercontent.com/73247157/120010299-9a83f300-bffa-11eb-9549-ea526a8c2e27.png">


> ### Observation: 
> We can observe that higher the value of learning rate, higher the rate of convergence of loss for this particular problem. This is not true in most deep neural network problems as the learning rate is generally kept low to update the weights slowly. 

---
# Part-2
On MNIST data, create a model to get 
99.4% validation accuracy
Less than 20k Parameters
You can use anything from above you want. 
Less than 20 Epochs
Have used BN, Dropout, a Fully connected layer, have used GAP. 

### Final Results
1. Achieved 99.4 test accuracy in 17th epoch
2. Total Parameters 9848
3. Droput = 0.04
4. Augmentation = Yes
5. Optimizer = SGD 
6. BatchNorm  = Yes
7. 1x1 Con Layer = Yes, 2 times
8. Max Channels = 20

### Model Architecture
![image](https://user-images.githubusercontent.com/73247157/120020888-f6a14400-c007-11eb-8956-0e000a6386b2.png)


2 3x3 conv layers followed by 1 1x1 con layer
![image](https://user-images.githubusercontent.com/73247157/120021044-2fd9b400-c008-11eb-85a8-f5e657359850.png)


### Model Results
epoches: 1
  0%|          | 0/1875 [00:00<?, ?it/s]<ipython-input-8-92be57754e27>:84: UserWarning: Implicit dimension choice for log_softmax has been deprecated. Change the call to include dim=X as an argument.
  return F.log_softmax(x)
Loss=0.01791616901755333 Batch_id=1874 Accuracy=92.02: 100%|██████████| 1875/1875 [00:32<00:00, 57.98it/s]

Test set: Average loss: 0.0578, Accuracy: 9817/10000 (98.17%)

epoches: 2
Loss=0.01668095961213112 Batch_id=1874 Accuracy=97.20: 100%|██████████| 1875/1875 [00:33<00:00, 56.75it/s]

Test set: Average loss: 0.0354, Accuracy: 9890/10000 (98.90%)

epoches: 3
Loss=0.019943520426750183 Batch_id=1874 Accuracy=97.75: 100%|██████████| 1875/1875 [00:32<00:00, 57.37it/s]

Test set: Average loss: 0.0300, Accuracy: 9897/10000 (98.97%)

epoches: 4
Loss=0.2935098707675934 Batch_id=1874 Accuracy=98.03: 100%|██████████| 1875/1875 [00:33<00:00, 56.06it/s]

Test set: Average loss: 0.0280, Accuracy: 9915/10000 (99.15%)

epoches: 5
Loss=0.01274165604263544 Batch_id=1874 Accuracy=98.19: 100%|██████████| 1875/1875 [00:33<00:00, 55.29it/s]

Test set: Average loss: 0.0240, Accuracy: 9923/10000 (99.23%)

epoches: 6
Loss=0.10993336886167526 Batch_id=1874 Accuracy=98.34: 100%|██████████| 1875/1875 [00:33<00:00, 56.28it/s]

Test set: Average loss: 0.0255, Accuracy: 9922/10000 (99.22%)

epoches: 7
Loss=0.015055202879011631 Batch_id=1874 Accuracy=98.34: 100%|██████████| 1875/1875 [00:33<00:00, 56.37it/s]

Test set: Average loss: 0.0214, Accuracy: 9929/10000 (99.29%)

epoches: 8
Loss=0.011099874041974545 Batch_id=1874 Accuracy=98.36: 100%|██████████| 1875/1875 [00:32<00:00, 57.77it/s]

Test set: Average loss: 0.0222, Accuracy: 9918/10000 (99.18%)

epoches: 9
Loss=0.061118967831134796 Batch_id=1874 Accuracy=98.48: 100%|██████████| 1875/1875 [00:33<00:00, 56.24it/s]

Test set: Average loss: 0.0239, Accuracy: 9922/10000 (99.22%)

epoches: 10
Loss=0.004031766671687365 Batch_id=1874 Accuracy=98.58: 100%|██████████| 1875/1875 [00:33<00:00, 56.12it/s]

Test set: Average loss: 0.0234, Accuracy: 9930/10000 (99.30%)

epoches: 11
Loss=0.0018003821605816483 Batch_id=1874 Accuracy=98.63: 100%|██████████| 1875/1875 [00:33<00:00, 56.62it/s]

Test set: Average loss: 0.0212, Accuracy: 9927/10000 (99.27%)

epoches: 12
Loss=0.04350588470697403 Batch_id=1874 Accuracy=98.69: 100%|██████████| 1875/1875 [00:34<00:00, 54.27it/s]

Test set: Average loss: 0.0238, Accuracy: 9919/10000 (99.19%)

epoches: 13
Loss=0.000587923510465771 Batch_id=1874 Accuracy=98.69: 100%|██████████| 1875/1875 [00:34<00:00, 55.08it/s]

Test set: Average loss: 0.0227, Accuracy: 9936/10000 (99.36%)

epoches: 14
Loss=0.007423980161547661 Batch_id=1874 Accuracy=98.70: 100%|██████████| 1875/1875 [00:33<00:00, 56.28it/s]

Test set: Average loss: 0.0221, Accuracy: 9929/10000 (99.29%)

epoches: 15
Loss=0.005151162389665842 Batch_id=1874 Accuracy=98.74: 100%|██████████| 1875/1875 [00:34<00:00, 54.03it/s]

Test set: Average loss: 0.0206, Accuracy: 9937/10000 (99.37%)

epoches: 16
Loss=0.014020382426679134 Batch_id=1874 Accuracy=98.79: 100%|██████████| 1875/1875 [00:33<00:00, 55.41it/s]

Test set: Average loss: 0.0243, Accuracy: 9927/10000 (99.27%)

epoches: 17
Loss=0.007903391495347023 Batch_id=1874 Accuracy=98.82: 100%|██████████| 1875/1875 [00:33<00:00, 55.22it/s]

Test set: Average loss: 0.0219, Accuracy: 9942/10000 (99.42%)

epoches: 18
Loss=0.09574344009160995 Batch_id=1874 Accuracy=98.82: 100%|██████████| 1875/1875 [00:33<00:00, 55.79it/s]

Test set: Average loss: 0.0222, Accuracy: 9933/10000 (99.33%)

epoches: 19
Loss=0.003300874959677458 Batch_id=1874 Accuracy=98.82: 100%|██████████| 1875/1875 [00:35<00:00, 53.37it/s]

Test set: Average loss: 0.0212, Accuracy: 9930/10000 (99.30%)
 

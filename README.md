# EV8 Assignment-4

## Task
* Acheive 99.4% accuracy on MNIST dataset(this must be consistently shown in your last few epochs, and not a one-time achievement)
* Less than or equal to 15 Epochs
* Less than 10000 Parameters (additional points for doing this in less than 8000 pts)
* Explain your 3 steps using these target, results, and analysis with links to your GitHub files

# **Step 1**
______________

[Code 1](https://github.com/dine1717/EV8/blob/Session4/Step_1.ipynb)


# Target

 1. Settle on Architeture
 2. Visualize Data
 3. Define Data Loaders, Data Transformations and Image Normalization
 4. Design vanila model architeture.
 
# Result:
 
 1. Total Parameters: 147,344
 2. Best Training Accuarcy: 99.74
 3. Best Test Accuarcy: 99.06
 
# Analysis:
 1. Model is working but we see for some of the epochs its overfitting.
 2. Model will never reach 99.4 on test data as the train data already acheived a max of 99.74
 3. To avoid overfitting we need three things; 1.Drop0ut, 2. Fewer Parameters, 3. Batch normalization

___________

# **Step 2**

[Code 2](https://github.com/dine1717/EV8/blob/Session4/Step_2.ipynb)

 
 # Target

 1. Reduce Model Parameters
 2. Use Batch Normalization to improve accuracy
 3. Use Gap to improve accuracy
 
# Result:
 
 1. Total Parameters: 10616
 2. Best Training Accuarcy: 99.50
 3. Best Test Accuarcy: 99.34
 
# Analysis:
 1. Model is performing good and in some epochs it is close to the target.
 2. MNIST doesn't need 145k parameters even 10k is good enough
 3. Model is not overfitting, so we can reach 99.4 accuracy on test
 4. Data augmentation might help

___________

# **Step 3**

[Code 3](https://github.com/dine1717/EV8/blob/Session4/Step_3.ipynb)

 
# Target
1. Increase aacuracy  by using dropout and Augmentation
 
# Result:
 
 1. Total Parameters: 10616
 2. Best Training Accuarcy: 99.35
 3. Best Test Accuarcy: 99.45
 
# Analysis:
 1. The model attained 99.4 in 12th epoch but it is not consistent 
 2. Try going deeper by adding padding in the initial layers
 3. Add 1x1 conv block after GAP
 

___________

# **Step 4**

[Code 4](https://github.com/dine1717/EV8/blob/Session4/Step_4.ipynb)
 
# Target
1. Apply 1x1 after GAP
2. Add more layers 

 
# Result:
 
 1. Total Parameters: 8172
 2. Best Training Accuarcy: 98.75
 3. Best Test Accuarcy: 99.41
 
# Analysis:
 1. Model is performing attained 99.35 for the first time in the 10th epoch and max acciracy is 99.4
 2. 8k parameters are good enough
 3. Going deeper with 7 conv layers helped
 4. Added 1x1 conv layer after GAP
 5. Consistently above 99.3 in the last 6 epochs
 
# Epochs

EPOCH: 9
Loss=0.04256036505103111 Batch_id=468 Accuracy=98.57: 100%|██████████| 469/469 [00:18<00:00, 25.99it/s]
Test set: Average loss: 0.0207, Accuracy: 9941/10000 (99.41%)

EPOCH: 10
Loss=0.060553789138793945 Batch_id=468 Accuracy=98.54: 100%|██████████| 469/469 [00:18<00:00, 25.76it/s]
Test set: Average loss: 0.0218, Accuracy: 9935/10000 (99.35%)

EPOCH: 11
Loss=0.07819259166717529 Batch_id=468 Accuracy=98.66: 100%|██████████| 469/469 [00:17<00:00, 26.47it/s]
Test set: Average loss: 0.0203, Accuracy: 9940/10000 (99.40%)

EPOCH: 12
Loss=0.02098129503428936 Batch_id=468 Accuracy=98.66: 100%|██████████| 469/469 [00:17<00:00, 26.29it/s]
Test set: Average loss: 0.0185, Accuracy: 9940/10000 (99.40%)

EPOCH: 13
Loss=0.06187823414802551 Batch_id=468 Accuracy=98.67: 100%|██████████| 469/469 [00:17<00:00, 26.07it/s]
Test set: Average loss: 0.0197, Accuracy: 9939/10000 (99.39%)

EPOCH: 14
Loss=0.05547378957271576 Batch_id=468 Accuracy=98.75: 100%|██████████| 469/469 [00:17<00:00, 26.19it/s]
Test set: Average loss: 0.0193, Accuracy: 9931/10000 (99.31%)
 
___________


# **Step 5**

[Code 5](https://github.com/dine1717/EV8/blob/Session4/Step_5.ipynb)
 
# Target

1. Less than 9000 parameters
2. Less than 15 epochs
3. Test with Cyclic LR
4. Add small dropout of 5%

# Results

1. Number of Parameters = 8172
2. Best Train Accuracy = 99.04
3.Best Test Accuracy = 99.56

# Analysis

1.We pushed the model to achieve target with approx 8k Parameters
2. Model consistently has 99.4 accuracy in the last 5 epocs
3. Onecycle LR is pure magic

## EPOCHS

EPOCH: 10
Loss=0.02085421048104763 Batch_id=468 Accuracy=98.82: 100%|██████████| 469/469 [00:18<00:00, 25.14it/s]
Epoch: 10 LR: [0.031703533067975895]
Test set: Average loss: 0.0190, Accuracy: 9942/10000 (99.42%)

EPOCH: 11
Loss=0.021372774615883827 Batch_id=468 Accuracy=98.92: 100%|██████████| 469/469 [00:18<00:00, 25.10it/s]
Epoch: 11 LR: [0.018800902517922092]
Test set: Average loss: 0.0179, Accuracy: 9943/10000 (99.43%)

EPOCH: 12
Loss=0.017850538715720177 Batch_id=468 Accuracy=98.99: 100%|██████████| 469/469 [00:20<00:00, 23.43it/s]
Epoch: 12 LR: [0.008670466465012771]

Test set: Average loss: 0.0152, Accuracy: 9956/10000 (99.56%)

EPOCH: 13
Loss=0.008586513809859753 Batch_id=468 Accuracy=99.04: 100%|██████████| 469/469 [00:18<00:00, 25.02it/s]
Epoch: 13 LR: [0.0022123586092353013]
Test set: Average loss: 0.0147, Accuracy: 9949/10000 (99.49%)

EPOCH: 14
Loss=0.04390697181224823 Batch_id=468 Accuracy=99.04: 100%|██████████| 469/469 [00:18<00:00, 25.36it/s]
Epoch: 14 LR: [4.101745150496986e-07]
Test set: Average loss: 0.0146, Accuracy: 9949/10000 (99.49%)

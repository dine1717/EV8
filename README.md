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

 
 
# Target
1. Apply 1x1 after GAP
2. Add more layers 

 
# Result:
 
 1. Total Parameters: 8172
 2. Best Training Accuarcy: 99.32
 3. Best Test Accuarcy: 99.5
 
# Analysis:
 1. Model is performing attained 99.39 for the first time in the 10th epoch and max acciracy is 99.50
 2. 8k parameters are good enough
 3. Going deeper with 7 conv layers helped
 4. Added 1x1 conv layer after GAP
 5. Consistently above 99.35 in the last 5 epochs
 

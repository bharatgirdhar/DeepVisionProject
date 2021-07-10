# EVA6_Session9
### By Bharat Girdhar, Shrey Joshi and Akshaj Verma

## Model

### PrepLayer - 
Conv 3x3 s1, p1) >> BN >> RELU [64k]
### Layer1 -
X = Conv 3x3 (s1, p1) >> MaxPool2D >> BN >> RELU [128k]
R1 = ResBlock( (Conv-BN-ReLU-Conv-BN-ReLU))(X) [128k] 
Add(X, R1)

### Layer 2 -
Conv 3x3 [256k]
MaxPooling2D
BN
ReLU

### Layer 3 -
X = Conv 3x3 (s1, p1) >> MaxPool2D >> BN >> RELU [512k]
R2 = ResBlock( (Conv-BN-ReLU-Conv-BN-ReLU))(X) [512k]
Add(X, R2)
MaxPooling with Kernel Size 4

FC Layer 

SoftMax


## Model Summary

![Model Summary](/extra/Custom_Resnet_Summary.png)



### One Cycle Policy such that:
1. Total Epochs = 24
2. Max at Epoch = 5
3. LRMIN = 0.0001
4. LRMAX = 0.2
5. NO Annihilation

## Transformations in sequence- 
1. RandomCrop 32, 32 (after padding of 4) 
2. FlipLR
3. CutOut(8, 8)

### Batch size = 512

### Accuracy - 
## 89.1 
### in 23rd EPOC 

## LR Graphs
### Exponential LR
![Increasing LR Exponentially](/extra/Exponential_LR.png)
  
### Linear LR
![Increasing LR Exponentially](/extra/Sequential_LR.png)

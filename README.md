# EVA6_Session9

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

----------------------------------------------------------------
        Layer (type)               Output Shape         Param #
================================================================
            Conv2d-1           [-1, 64, 32, 32]           1,728
       BatchNorm2d-2           [-1, 64, 32, 32]             128
            Conv2d-3          [-1, 128, 32, 32]          73,728
         MaxPool2d-4          [-1, 128, 16, 16]               0
       BatchNorm2d-5          [-1, 128, 16, 16]             256
            Conv2d-6          [-1, 128, 16, 16]         147,456
       BatchNorm2d-7          [-1, 128, 16, 16]             256
            Conv2d-8          [-1, 128, 16, 16]         147,456
       BatchNorm2d-9          [-1, 128, 16, 16]             256
           Conv2d-10          [-1, 256, 16, 16]         294,912
        MaxPool2d-11            [-1, 256, 8, 8]               0
      BatchNorm2d-12            [-1, 256, 8, 8]             512
           Conv2d-13            [-1, 512, 8, 8]       1,179,648
        MaxPool2d-14            [-1, 512, 4, 4]               0
      BatchNorm2d-15            [-1, 512, 4, 4]           1,024
           Conv2d-16            [-1, 512, 4, 4]       2,359,296
      BatchNorm2d-17            [-1, 512, 4, 4]           1,024
           Conv2d-18            [-1, 512, 4, 4]       2,359,296
      BatchNorm2d-19            [-1, 512, 4, 4]           1,024
        MaxPool2d-20            [-1, 512, 1, 1]               0
           Linear-21                   [-1, 10]           5,130
================================================================
Total params: 6,573,130
Trainable params: 6,573,130
Non-trainable params: 0
----------------------------------------------------------------
Input size (MB): 0.01
Forward/backward pass size (MB): 4.88
Params size (MB): 25.07
Estimated Total Size (MB): 29.97



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

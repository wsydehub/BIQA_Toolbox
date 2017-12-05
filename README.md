# Introduction

This Toolbox contains the source code for the following article:

    @article{DBLP:journals/corr/abs-1708-08190,
      author    = {Hui Zeng and
                   Lei Zhang and
                   Alan C. Bovik},
      title     = {A Probabilistic Quality Representation Approach to Deep Blind Image
                   Quality Prediction},
      url       = {http://arxiv.org/abs/1708.08190},
    }
    
Note that on some datasets such as TID2013, the performance varies greatly when using different training and testing splits. However, it is too cumbersome for deep BIQA methods to repeat experiments as many times (usually more than 100) as the classical methods. This can make it hard to conduct a fair comparison of results reported in different articles. Thus, this Toolbox also aims to provide relatively fair benchmark performances (by using the same 10 randomly generated training and testing splits, see `/tools/setupDataset/generateTrainingset.m`) of several popular CNN architectures and some classical blind image quality assessment (BIQA) methods using hand-crafted features on four representative image quality assessment (IQA) datasets.



#### Main functions

1. `training_testing_CNNs.m` trains a CNN model using a proportion (e.g. 0.8) of images and tests performance on the remaining images.

2. `crossDatasetTrainTest.m` trains a CNN model on one dataset and tests performance on other datasets.

3. `evaluating_existing_methods.m` evaluates several representative classical BIQA methods including DIIVINE,CORNIA,BRISQUE, NIQE, IL-NIQE, HOSA and FRIQUEE. Except for NIQE, the source codes of other methods need to be downloaded and extracted into the ``supported_methods`` before evaluating these methods. 

**How to run the Code**

1. Download the [MatConvNet](http://www.vlfeat.org/matconvnet/) into ``tools`` and Compile it according to the guidence therein. 

2. Create a new fold ``pretrained_models`` and download the pre-trained [AlexNet](http://www.vlfeat.org/matconvnet/models/imagenet-caffe-alex.mat) or [ResNet](http://www.vlfeat.org/matconvnet/models/imagenet-resnet-50-dag.mat) into ``pretrained_models`` if necessary.

3. Create a new fold ``databases``. Download an IQA dataset into ``databases`` and extract the files. Currently, four datasets are supported including the LIVE Challenge, LIVE IQA, CSIQ and TID2013. 

4. Run any of the three main functions.

# Results
The median SRCC (std SRCC) of 10 repititions of different methods on different datasets.

|  Methods | LIVE Challenge  | LIVE IQA | CSIQ |  TID2013 |
|:-------:|:-------:|:-------:|:-------:|:-------:|
| AlexNet_SQR | 0.7658 (0.0166)        | 0.9319 (0.0269)  |   0.7965 (0.0394)   |  0.5362 (0.1100) |
| AlexNet_PQR | 0.8075 (0.0123)        | 0.9554 (0.0185) |   0.8713 (0.0229)  |  0.5742 (0.1156) |
| ResNet50_SQR | 0.8236 (0.0159)       | 0.9468 (0.0199)  | 0.8217 (0.0481) |  0.6406 (0.0577) |
| ResNet50_PQR |  **0.8568 (0.0095)**  | **0.9653 (0.0105)**  | 0.8728 (0.0319) |  **0.7399 (0.1037)** |
| S_CNN_SQR |  0.6582 (0.0323)         | 0.9450 (0.0320)  | 0.8787 (0.0213) |    0.6526 (0.1136)   |
| S_CNN_PQR |  0.6766 (0.0326)         | 0.9637 (0.0223) | **0.9080 (0.0212)** |    0.6921 (0.1246) |

The median PLCC (std PLCC) of 10 repititions of different methods on different datasets.

|  Methods | LIVE Challenge  | LIVE IQA | CSIQ |  TID2013 |
|:-------:|:-------:|:-------:|:-------:|:-------:|
| AlexNet_SQR | 0.8074 (0.0176)      | 0.9426 (0.0227) |   0.8405 (0.0384)   |  0.6136 (0.1045) |
| AlexNet_PQR | 0.8357 (0.0124)      | 0.9638 (0.0181)  |   0.8958 (0.219)   |  0.6687 (0.0840) |
| ResNet50_SQR | 0.8680 (0.0117)     | 0.9527 (0.0145)     | 0.8713 (0.0355) |  0.7068 (0.0695)     |
| ResNet50_PQR | **0.8822 (0.0098)** | **0.9714 (0.093)**  | 0.9010 (0.0266) |  **0.7980 (0.0848)** |
| S_CNN_SQR |  0.6729 (0.0309)   | 0.9455 (0.0249)  | 0.8987 (0.0234) |    0.6921 (0.1314)  |
| S_CNN_PQR |  0.7032 (0.0298)   | 0.9656 (0.0219)  | **0.9267 (0.0219)** |    0.7497 (0.1089)  |

#### License

This toolbox is made available for research purpose only. 

We utilize the MatConvNet and libSVM toolboxes and re-implement some existing methods. Please check corresponding licence files for details.

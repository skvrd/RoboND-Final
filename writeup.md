# Deep Learning Project

## Introduction
This file describes the Follow Me project

In this project I build and train fully convolutional neural network, that makes segmentation.
This network can perform tracking of a target person (hero) in the simulation.

## Fully Convolutional Network (FCN)
FCN consists of 3 parts:
1. Encoder
2. Decoder

### Encoder
Encoder extracts useful features from the images. This is just a set of convolutional layers.
Each layer of the encoder “squeezes” information form the input image.
In classical Convolutional network flatten the output by connecting it to the fully connected layer. Which leads to the spatial information loss.

### 1x1 Convolution
In order to keep spatial information we can use 1x1 convolution. It helped in reducing the dimensionality of the layer and avoid flattening of the output information. 

### Decoder
instead of using fully connected layers, we will use decoder.
It upsamples information from the encoder all the way to the original image size.

## Network Structure

## Parameters
1. Learning rate. This should be relatively small, so I decide to start with 0.001
2. Batch Size = 16
    1. I started with batch size of 64 on my CPU first, and in took couple hours to process 1 epoch. 
    2. Then I installed CUDA for my 780 GTX  on ubuntu (which was somewhat challenging I have to say). 
    3. It allowed me do use GPU with tensorflow
    4. But with GPU calculations batch size of 64 leads to memory error, I assume it can not fit to memory for my network structure.
    5. Then I lower my batch size to 16.
3. Epoch = 50. I decide to go with relatively big number for the start.
4. Step_per_epoch = number of training examples / batch size
5. Validation steps = number of validation steps / batch size
6. Worker = 2 / Here I decide to stick with default value from the provided file. But since I have only 1 GPU this parameter is not should not be relevant anyway.


## Overview
Style transfer with NN approach. Cycle GAN with unsupervised learning. The model is implemented according to [the work by Jun-Yan.Z et al](https://arxiv.org/pdf/1703.10593.pdf) The original generator has 6 Resblocks, the tuned version has fewer and number of feature maps in embedding blocks are reduced. A random pooling of images is added. Hyperparameter tunings revolves around LR, decay rate and effecting of a pooling of process images. 

<p align="center">
<img src=/Images/cycle_gan.png width="512">
</p>

## Set up
The checkpoints are too large to be uploaded. In order to train the model, store the data into /datasets/face2anime/[trainA, trainB, testA, testB]/1/ respectively or change the file pathing in notebook. 100 epoch training takes about 2 days worth of time in collab. 

## Data
Unparied data of selfies and anime avatar from [kaggle](https://www.kaggle.com/sharmayush/person2anime/activity). The images are resized to 128x128 to lower computational load. 

<p align="center">
  <img src=/Images/female_348.jpg width="120">
  <img src=/Images/female_1409.jpg width="120">
  <br/>
  <img src=/Images/0008.jpg width="120">
  <img src=/Images/0009.jpg width="120">
 </p>

## Model
Cycle GAN learns input feature through two different GANs that tries to convert an image into different domains respectively. In each cycle, an image from domain A under goes transformation to domain B then back to A. The reconstructed image is compared to the original input. The generator is a ResNet style additive skip connection downsampled with conv. The discriminator outputs 16x16 map that represents the markovian field of the input image. 

<p align="center">
<img src="/Images/Model Architecture.png" width="640">
</p>

## Performance

### Training and validation
The results are evaluated qulitatively. Performance for the training set and validation set are identical. 

#### Cycle A
<p align="center">

<br/>
Some good ones
<br/>
<img src=/Images/AtoB_good.png width="640">
<br/>
Some bad ones
<br/>
<img src=/Images/AtoB_bad.png width="640">
</p>

#### Cycle B
<p align="center">
<img src=/Images/BtoA_good.png width="640">
</p>

### Testing 
For female selfies, the performance mainly depends on if the image contains foreign objects (e.g., glasses, hat, mask, phone etc.). For male selfie and objects, unrecognizable features such as beard will be ignored. 

<p align="center">
<img src=/Images/asmon.PNG width="640">
<br/>
<img src=/Images/morgen.png width="640">
<br/>
<img src=/Images/orange.png width="640">
</p>

## Conclusion 
In the downscaled models, one with random pooling method show significantly improvement in quality. The model can be expected to generalize the style transfer for both male and female. Currently, the results appear more like style transfer than filtering. In order to retain more features of the input image, the L1 loss function may be adjusted to have higher weights. 


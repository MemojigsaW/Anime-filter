## Overview
Style transfer with NN approach. Cycle GAN with unsupervised learning. The model is implemented according to [the work by Jun-Yan.Z et al](https://arxiv.org/pdf/1703.10593.pdf) The original generator has 6 Resblocks, the tuned version has fewer and number of feature maps in embedding blocks are reduced. A random pooling of images is added. Hyperparameter tunings revolves around LR and the decay rate. 

<p align="center">
<img src=/Images/cycle_gan.png>
</p>

## Set up
The checkpoints are too large to be uploaded. In order to train the model, store the data into /datasets/face2anime/[trainA, trainB, testA, testB]/1/ respectively or change the file pathing in notebook. 100 epoch training takes about 2 days worth in collab. 

## Data
Unparied data of selfies and anime avatar from [kaggle](https://www.kaggle.com/sharmayush/person2anime/activity). The images are resized to 128x128 to lower computational load. 

<p align="center">
  <img src=/Images/female_348.jpg>
  <img src=/Images/female_1409.jpg>
  <img src=/Images/0008.jpg>
  <img src=/Images/0009.jpg>
 </p>

## Model
Cycle GAN learns input feature through two different GANs that tries to convert an image into different domains respectively. The generator is a ResNet style additive skip connection downsampled with conv. The discriminator outputs 16x16 map that represents the markovian field of the input image. 

<img src=/Images/ModelArchitecture.png align="center">

## Performance

### Training and validation
The results are evaluated qulitatively. Performance for the training set and validation set are identical. 

2 good 
2 bad

### Testing 
For female selfies, the performance mainly depends on if the image contains foreign objects (e.g., glasses, hat, mask etc.). For male selfie and objects, unrecognizable features such as beard will be ignored. 

1 asmon
1 morgan 
1 organce

## Conclusion 

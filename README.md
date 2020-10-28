## Overview
Style transfer with NN approach. Cycle GAN with unsupervised learning. The model is implemented according to [the work by Jun-Yan.Z et al](https://arxiv.org/pdf/1703.10593.pdf)

## Set up
The checkpoints are too large to be uploaded. In order to train the model, store the data into /datasets/face2anime/[trainA, trainB, testA, testB]/1/ respectively or change the file pathing in notebook. 100 epoch training takes about 2 days worth in collab. 

## Data
Unparied data of selfies and anime avatar from [kaggle](https://www.kaggle.com/sharmayush/person2anime/activity). The images are resized to 128x128 to lower computational load. 

4 images for comparison 

## Model
Cycle GAN learns input feature through two different GANs that tries to convert an image into different domains respectively. The generator is a ResNet style additive skip connection downsampled with conv. The discriminator outputs 16x16 map that represents the markovian field of the input image. 

2 images for model 

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
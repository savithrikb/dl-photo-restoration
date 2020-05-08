# PHOTO RESTORATION APP

The main goal of this project is to restore an old tarnsihed photo using Deep Learning (DL) algorithms based on Generative Adversarial Networks (GANs) . For this project, the training dataset will be several old damaged photos as well as several high-quality images that can be found in the "photos/old/" and "photos/new/" directories, respectively.

## Data loading and visualization
As a first step of this project we have to load the data and visualize it. We use the PyTorch ImageFolder and DataLoader classes for this task. Also, we have done some pre-processing to rescale our training images to a range of -1 to 1. 

## Define the discriminator architecture
A CycleGAN is made of two discriminator and two generator networks. The discriminators are a neural network for determining whether the image is real or fake. We used similiar architecture of the paper Unsupervised Image Super-Resolution using Cycle-in-Cycle Generative Adversarial Networks for both discriminator and generator. This network sees a 512x512x3 image, and passes it through 5 convolutional layers that downsample the image by a factor of 2. The first four convolutional layers have a BatchNorm and ReLu activation function with negative slope 0.2 applied to their output, and the last acts as a classification layer that outputs one value.

## Define the generator architecture
The generator network has three parts, an encoder, a transformer, and a decoder. The input image is fed directly into the encoder, which shrinks the representation size while increasing the number of channels. The encoder is composed of three convolutional layers. The transformer is a series of six residul blocks, also called ResNet blocks. Finally, the decoder is composed of three transpose convolutional layers (sometimes called de-conv layers) which upsample the output of the ResNet blocks and create a new image. We use the architecture according to the same paper mentioned above.



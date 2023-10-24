---
author: Shravan Bhat
title: Deepfake Creation through Transformer-based Sequence2Sequence Modeling
description: Deepfake Creation through Transformer-based Sequence2Sequence Modeling
tags: ["python", "PyTorch", "Deep Learning"]
icon: fas map
layout: minimal
---

Sequence to Sequence (Seq2Seq) modelling is a case where we try to obtain a new sequence of data from an input sequence of data. Here the data points at every position may or may not be related to data points at other positions. For example, consider sentence translation from one language to another language. Some words will have high significance compared to other words. Therefore it is important for a model to understand the exact context of every word in the sentence. 

Traditional models which were employed to solve Seq2Seq problem lacked this crucial step of exactly figuring out the meaning of every word. Multilayer perceptrons assumed its inputs to be independent so they could only find linear relations between words and not its exact meaning. CNNs ability to correlate the words were limited by its filter sizes. RNNs faced the problem of sequential prediction which made it impossible to correlate words with future words. Also, they were very slow during training process as computations cannot be parallelised. 

All these problems lead to the invention of Transformers in 2017. A group of researchers from Google presented Transformers in a NIPS conference titled Attention is All You Need. 

**Methodlogy**

The method we are using to generate deepfakes is using the autoencoder model. Two autoencoders are trained to regenerate pictures of person A and person B. The autoencoders use a shared encoder but the decoders are different. Once the autoencoders are trained, we are swapping the decoders in order to generate  fake faces.

<div class="col-6 mx-auto">{{< image src="img/method.png" caption="Model Overview">}}</div>

The encoder has 4 sets of 2D convolutional layers with 64, 128, 256 and 512 filters followed by Batch Normalization layer. Each convolutional layer has 5*5 kernel size with stride 2. So, the feature’s size gets halved after every convolution layer. LeakyReLU is used as the activation function in every layer. The Batch Normalization helps in faster convergence. The output of the 4th convolution block is flattened and passed through a Dense layer with 512 neurons. So the encoder dimensions is 512. 

<div class="col-6 mx-auto">{{< image src="img/encoder.png" caption="Encoder">}}</div>

The decoder consists of 2 Dense layers followed by 4 sets of 2D Transpose convolutional layer and 2D convolution layer. The dense layers have 512 and 1024 neurons with Linear and ReLU activation. The convolutional layers have 512, 256, 128 and 3 filters. The kernel size is 3*3  with stride 1. It is LeakyReLU activated. Only the last convolutional layer is linearly activated. Batch Normalization layers are interspersed among these convolutional layers.

<div class="col-6 mx-auto">{{< image src="img/encoder.png" caption="Decoder">}}</div>

**Experiments and Results**

The dataset we used to train the autoencoders consisted of about 660 images of Donald Trump and Nicolas Cage randomly taken from the internet. From these raw images, only the faces were extracted using Haar Cascades Frontal Face detection model. These extracted faces are fed as inputs to the autoencoders after resizing them to 64*64 pixels. 

<div class="col-6 mx-auto">{{< image src="img/output.png" caption="Model Output">}}</div>

The autoencoders are trained using Adam optimizer with learning rate equal to 0.00005, beta1 equal to 0.5 and beta2 equal to 0.999. Mean Absolute Error is used as the loss function. The autoencoders are trained for 1000000 epochs. To ensure that the encoder is not biased, we train the autoencoders simultaneously. 32 is used as the batch size.


**Conclusion**

Deepfakes have begun to erode trust of people in media contents as seeing them is no longer commensurate with believing in them. They could cause distress and negative effects to those targeted, heighten disinformation and hate speech, and even could stimulate political tension, inflame the public, violence or war. This is especially critical nowadays as the technologies for creating deepfakes are increasingly approachable and social media platforms can spread those fake contents quickly. Sometimes deepfakes do not need to be spread to massive audience to cause detrimental effects. People who create deepfakes with malicious purpose only need to deliver them to target audiences as part of their sabotage strategy without using social media.

For example, this approach can be utilized by intelligence services trying to influence decisions made by important people such as politicians, leading to national and international security threats. Catching the deepfake alarming problem, research community has focused on developing deepfake detection algorithms and numerous results have been reported. It is noticeable that a battle between those who use advanced machine learning to create deepfakes with those who make effort to detect deepfakes is growing. Deepfakes’ quality has been increasing and the performance of detection methods needs to be improved accordingly.

Our approach to create deepfakes is not free from errors. Training the autoencoders on larger numbers of images with different expressions and also for more number of epochs definitely improves the construction of deepfaked images avoiding blurry and pixelated outputs. Also, the autoencoders can be coupled with discriminator model and trained in a GAN way. The perceptual loss from the Discriminator can help in making the deepfaked output more natural. 
# Biometric_Recognition

## Table of contents
* [General info](#general-info)
* [Requirements](#requirements)
* [Project 1: Fingerprint recognition](#project-1---fingerprint-recognition-siamese-network)
* [Project 1b: Fingerprint recognition (triplet loss)](#project-1b---fingerprint-recognition-siamese-network-using-triplet-loss)
* [Project 2: Fingerprint autoencoder](#Project-2---Fingerprint-autoencoder)

## General info
These are some little projects to learn how to identify people based on their biometrics using CNN, pre-trained models, triplet-loss etc...

## Requirements

The basic libraries for machine learning and computer vision 😃

Libraries:
* OpenCV (python)
* Numpy
* Tensorflow
* Keras

## Project 1 - Fingerprint recognition (Siamese network)

The dataset used is Sokoto Coventry Fingerprint Dataset (SOCOFing) from Kaggle: https://www.kaggle.com/ruizgara/socofing/home

The network is designed to have 2 inputs and substract embeddings from both inputs to classify if the inputs are from the same person or not.

The network is made from scratch and thus very slow to train, I achieved 87% accuracy (~13% error), if I want to improve it I will use Resnet50 or VGG19.

## Project 1b - Fingerprint recognition (Siamese network using triplet loss)

This time we will use triplets and triplet-loss instead of a sigmoid to classify if a person belong to a database.

Triplet-loss consist of retrieving batch of triplets such as one image serves as the anchor, one as the positive (same class or person) and one negative (different person), we then compute the distance between the anchor and the positive then the distance between the anchor and the negative image.
The goal is to make the positive image closer to the anchor than the negative image.

<p align="center">
  <img src="https://user-images.githubusercontent.com/65224852/136039328-766c7e20-1730-4f0f-a465-c65cf4a08c70.png"/>
  <br><a href="https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Schroff_FaceNet_A_Unified_2015_CVPR_paper.pdf">(From 2015 Facenet paper)</a>
</p>

The formula to compute the loss is:

<p align="center">
<img src="https://user-images.githubusercontent.com/65224852/136038688-0cac2328-6401-4097-82a2-6b232ac6c44c.png">
</p>

Where:
* x is the training set, xa the anchor image, xp the positive, xn the negative
* α is a constant ranging from 0.2 to 1.0
* f(xi) is the embeding of the i-th image from the training set.

## Project 2 - Fingerprint autoencoder

This second project aims to **repair** damaged fingerprint by using an autoencoder also made from scratch.

We can use this idea to improve handwriting for instance.

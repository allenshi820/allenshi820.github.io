---
layout:     post
title:      "Cheetah Image Masking"
date:       2017-06-20 09:37:00
author:     "Allen Shi"
header-img: "img/posts/cheetah.jpg"
comments: true
---

## Goal
The goal is to segment the “cheetah” image (shown below in the left) into its two components, cheetah (foreground) and grass (background) by implementing a Gaussian Naive Bayes classifier. The parameters of the model are estimated using maximum likelihood and maximum a posteriori methods.

The image on the left is the image that we are trying to segment and the image on the right is the ground truth.

Cheetah Image           |  Ground Truth
:-------------------------:|:-------------------------:
<img src="/img/posts/cheetah.png" align="left" width="350" height="350" >  |  <img src="/img/posts/cheetah_mask.png" align="right" width="350" height="350" >

## Gaussian Naive Bayes Classifier

The Naive Bayes classifier adopts the Bayesian decision theory, which is just maximum a posteriori estimation.

<center><img src="/img/posts/BDR1.png" width="315" height="80" ></center>

In our problem, i indicates the binary classes - foreground and background. The equation above can be rewritten into the equation below based on Bayes rule.

<center><img src="/img/posts/BDR2.png" width="365" height="80" ></center>

We assumed that the likelihood function has a Gaussian distribution.





## Image Processing
We first performed a discrete fourier transform using blocks of 8x8 pixels and transformed the 2D array into a 64D feature vector after DFT. The figure below summarizes the process.

<center><img src="/img/posts/DFT.png" width="600" height="450" ></center>

## Feature Selection
In the training set, we are provided with these 64 features with "foreground" and "background" labeled. By making the assumption that each of these features has a Gaussian distribution, we estimated their mean and variance through maximum likelihood. In the Gaussian case, the estimated mean and variance are just the sample mean and sample variance. However, a 64 dimensional feature space is huge. To reduce the dimension, we selected the best 8 feature by plotting the "foreground" and "background" feature distributions, where the blue curve is background and orange curve is foreground.

<center><img src="/img/posts/64_feats.png" width="600" height="450" ></center>

The rule of thumb in feature selection is to select features whose background distribution and foreground distribution are far apart. We plotted the best and worst 8 features below.

Best 8 Features         |  Worst 8 Features
:-------------------------:|:-------------------------:
<img src="/img/posts/best_feats.png" align="left" width="350" height="350" >  |  <img src="/img/posts/worst_feats.png" align="right" width="350" height="350" >

## Classification

To segment the image, we first performed DCT using a sliding window on the input cheetah image and calculated the probabily of foreground and background for each block. In the next step, the model classified each block into either foreground or background using the Bayesian Decision Theorem as described above.

The following image shows the result after segementation.
<center><img src="/img/posts/mask.png" width="420" height="300" ></center>

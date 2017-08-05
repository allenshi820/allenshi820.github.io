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

$i^*(x) = \underset{<constraints>}{\operatorname{<argmax>}}$

$\underset{c\in C}{\operatorname{argmax}}$

\alpha

## Image Processing

## Feature Selection
We first performed a discrete fourier transform using blocks of 8x8 pixels and converted transform the 2D array into a 64D feature vector after DFT. The figure below summarizes the process.
<img src="/img/posts/DFT.png" align="middle" width="600" height="450" >

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
<img src="/img/posts/cheetag.jpg" align="left">
<img src="/img/posts/cheetag_mask.jpg" align="right">

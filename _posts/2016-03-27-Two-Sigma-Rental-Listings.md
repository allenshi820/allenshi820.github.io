---
layout:     post
title:      "Rental Listings in NYC"
subtitle:   "Predict the rental listings interese level in NYC"
date:       2017-08-1 17:00:00
author:     "Allen Shi"
header-img: "img/posts/rental-listings.jpg"
comments: true
---

## Goal
Finding a perfect apartment is really diffcult and the whole process should be more than just browsing through endless listings. To better solve this problem and unleash potential business opportunity, I built a model to predict New York rental listings interst level by using the dataset released by RentHop.

## Exploratory data Analysis
The interest level is categorized into three classes - high, medium and low. Let's first take a look at the geographic distribution of all the listings' interest level.

<center><img src="/img/posts/NY_listings.png" width="650" height="650"></center>



<div>
    <a href="https://plot.ly/~a98051827/24/?share_key=oCcFzT3JrveEqO0NPRIUIc" target="_blank" title="Rental Listings" style="display: block; text-align: center;"><img src="https://plot.ly/~a98051827/24.png?share_key=oCcFzT3JrveEqO0NPRIUIc" alt="Rental Listings" style="max-width: 100%;width: 800px;"  width="800" onerror="this.onerror=null;this.src='https://plot.ly/404.png';" /></a>
    <script data-plotly="a98051827:24" sharekey-plotly="oCcFzT3JrveEqO0NPRIUIc" src="https://plot.ly/embed.js" async></script>
</div>




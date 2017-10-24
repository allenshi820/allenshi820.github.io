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

## Features
Let's first take a look at what features are available to us. For this dataset, we have:

- Number of Bedrooms
- Number of Bathrooms
- Building ID
- Created Date and Time
- Description
- Display Address
- Features
- Latitude and Longitude
- Photos URLs
- Price
- Street Address

## Exploratory Data Analysis
Now let's explore the dataset further and see if there's anything interesting that we could capture. 

### 1. Responsible Variable - Interest Level
The interest level is categorized into three classes - high, medium and low. The geographic distribution of all the listings' interest level is shown below.
<iframe width="700" height="600" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/24.embed"></iframe>
As the map shows above, most of the listings with low interest level are centered in Manhattan area whereas the apartments with high and medium interest levels are distributed across the Queens, Brooklyn and Bronx. As we can see, the dataset contains outliers - listings in Massachusetts, Pennsylvania and etc. Since our interest is to predict the interest level in New York City, we can remove these outliers by specifying -74.05 < Longitude < -73.80 and 40.6 < Latitude < 40.9.

The pie chart below shows the distrbution of all the listings according to their interest level.
<iframe width="500" height="400" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/26.embed"></iframe>
### 2. Feature - Price
Here we plot the price distribution with outliers removed beyond the 99% percentile.
<center><img src="/img/posts/price_dist.png" width="485" height="325" ></center>

### 1. Feature - Building ID
To transfer the building ID feature into a feature that can be implemented into our model, we first focused on 600 buildings with 15 units or more. Within each building, we calculated and assigned the prior probability of the 3 interest levels.

### 2. Feature - Manager ID
We took the same approach above to assign prior probablity to managers who manage 15 apartments or more.

### 3. Feature - Created Time and Date
We converted the feature "created time and date" of each listing into 3 numerical features - "created month", "created hour" and "created day of week". The following 3 figures show the interestl level distribution based on the 3 features.
<center><img src="/img/posts/DoW.png" width="485" height="325" ></center>
<center><img src="/img/posts/Hour.png" width="485" height="325" ></center>
<center><img src="/img/posts/month.png" width="485" height="325" ></center>

### 4. Feature - Feature Descriptions
Our first attemp was to try to identify keywords in listings with different interest levels. To do that, we counted the word frequency and plotted 3 wordclouds with 3 different interest levels. However, most of the high-frequency words were the same in 3 interest levels as the 3 wordclouds show below.
<center><img src="/img/posts/high.png" width="525" height="325" ></center>
<center><img src="/img/posts/medium.png" width="525" height="325" ></center>
<center><img src="/img/posts/low.png" width="525" height="325" ></center>
In order to perform a more detailed sentiment analysis, we used bag-of-words to simply the text feature representation by converting a collection of text documents to a matrix of token counts. To retrieve only the valuable information from the token counts, we also calculated the term frequency–inverse document frequency(tf-idf) scores for each token count. Therefore, we were able to use the finalized tf-idf score matrix as our features when we performed classification.

### 5. Feature - Latitude & Longitude
In EDA, we observed that in some area, such as Midtown East, the chance of interest level being high is a lot higher than other areas. In order to take this observation into account, we used the latitude and longitude to calcuate the distance between each listing to the center of New York and then clustered all the rental listings into 5 clusters. The following figure shows the result of clustering.
<iframe width="700" height="600" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/44.embed"></iframe>

## Feature Engineering

## Model Selection
To deal with imbalanced data, we eliminated some of the listings with low interest level. Our goal was to optomize the F1 score, which is the weighted average of Precision and Recall, since we had balanced data. We tested the performance of Support Vector Machine, Random Forest, XGBoost and an ensemble model of the three and XGBoost gave us the best performance in terms of F1 score and Log Loss. The table below summarizes the performance of XGBoost.


|          |  precision    |  recall |   f1-score  | support |
|----------|:-------------:|---------:|-----------:|--------:|
|   high   |  0.66 | 0.58 |  0.61  |  408  |
|   low    |  0.75 | 0.68 |  0.71  |  499  |
|  meidum  |  0.57 | 0.67 |  0.62  |  603  |
|avg/total |  0.65 | 0.65 |  0.65  |  1510 |



The final model achieved an accuracy of 0.66 and a Log Loss of 0.73.

We also examined the performance by plotting the receiver operating characteristic curve that illustrates the diagnostic ability. In general, the larger the AUC(Area Under Curve), the better the model performs.

<center><img src="/img/posts/ROC.png" width="500" height="400" ></center>




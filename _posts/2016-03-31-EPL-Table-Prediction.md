---
layout:     post
title:      "EPL Table Prediction"
subtitle:   "Soccer or football?"
date:       2017-07-20 4:17:00
author:     "Allen Shi"
header-img: "img/posts/EPL.jpg"
comments: true
---

## English Premier League
The Premier League is an English professional league for men's association football clubs. At the top of the English football league system, it is the country's primary football competition. Contested by 20 clubs, it operates on a system of promotion and relegation with the English Football League (EFL; known as "The Football League" before 2016–17).

Rules: If a team receives 3 points for a win, 1 point for a draw and 0 point for a loss.

## Goal
The goal of this project is to predict the total points every team will receive at the end of a season by using the game statistics data scrapped from The Premier League website.


## Feature Selection
In order to determine which features to use, We first plotted the feature correlation heatmap and tried to eliminate features which have a strong correlation with others.
<iframe width="750" height="750" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/30.embed"></iframe>
We also find the correlation between each feature and the target variable "Points" and eliminated features which have a correlation value less than 0.4.
<iframe width="850" height="600" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/32.embed"></iframe>
After the feature selection, only 5 features were left - "Goals Per Match", "Goals Conceded Per Match", "Pass Accuracy %", "Shooting Accuracy %" and "Penalties Scored".

The following pairplot shows the relation of each feature pair and no strong correlation is shown.
<center><img src="/img/posts/feature_corr.png"  width="570" height="530" ></center>

## Feature Engineering
A club is considered as a successful club if it made appearance in EPL more than 6 seasons in the last 11 years. We counted the appearances of every club in the last 11 years and selected the top 7 clubs to be successful clubs. We created another feature "Successful Club" to indicate whether or not a club is successful.
<center><img src="/img/posts/appearances.png"  width="520" height="530" ></center>

## Model Selection
In this project, we dediced to use linear regression as our model to predict the total points that a team will receive by the end of a season. We first performed grid search on the degree of a polynomial and plotted the corresponding mean square error(MSE) and R-squared value.
<iframe width="1000" height="450" align="left" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/36.embed"></iframe>

In linear regression, the higer the magnitude of the coefficient is, the more complex the model becomes. To penalize model complexity, we performed L2 regularization on our model by grid searching the best alpha parameter which is the regularization strength. The L2 regularization adds an extra term to the objective function.
<center><img src="/img/posts/obj.png"  width="250" height="70" ></center>
The larger the alpha is, the more we penalize the model with large coefficients.


<iframe width="1000" height="450" align="left" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/38.embed"></iframe>

As the above two figures show, the best alpha of our model is 1.55.

## Prediction
We predicted the total points each team will received of season 2016-2017 using a ridge regression model. The figure below shows the actual points and the predicted points.
<iframe width="900" height="500" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/40.embed"></iframe>
The MSE of this model is 113.772.

## Evaluation
One of the key assumptions of linear regreesion is that the residual should be normally distributed. To verify ths assumption, we plotted the the residuals and the Q-Q plot below.
<center><img src="/img/posts/eval.png"  width="750" height="350" ></center>
As the Q-Q plot indicates, most of the residuals lie along a line the distribution has the same shape as the theoretical distribution we have supposed.


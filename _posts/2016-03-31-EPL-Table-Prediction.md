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
In this project, we dediced to use Linear Regression as our model to predict the total points that a team will receive by the end of a season. We first performed grid search on the degree of a polynomial and plotted the corresponding mean square error(MSE) and R-squared value.
<iframe width="700" height="600" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/36.embed"></iframe>


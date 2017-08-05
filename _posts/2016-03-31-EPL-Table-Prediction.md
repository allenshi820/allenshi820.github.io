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
<iframe width="800" height="800" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/30.embed"></iframe>
We also find the correlation between each feature and the target variable "Points" and plotted the heatmap below.
<iframe width="1000" height="600" frameborder="0" scrolling="no" src="//plot.ly/~a98051827/32.embed"></iframe>

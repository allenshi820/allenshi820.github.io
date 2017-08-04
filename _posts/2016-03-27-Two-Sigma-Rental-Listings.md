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


<meta charset="utf-8">


<script src="//cdnjs.cloudflare.com/ajax/libs/d3/4.7.2/d3.min.js"></script>
<script src="/_posts/d3pie.min.js"></script>
<script>
var pie = new d3pie("pieChart", {
	"header": {
		"title": {
			"text": "Lots of Programming Languages",
			"fontSize": 24,
			"font": "open sans"
		},
		"subtitle": {
			"text": "A full pie chart to show off label collision detection and resolution.",
			"color": "#999999",
			"fontSize": 12,
			"font": "open sans"
		},
		"titleSubtitlePadding": 9
	},
	"footer": {
		"color": "#999999",
		"fontSize": 10,
		"font": "open sans",
		"location": "bottom-left"
	},
	"size": {
		"canvasWidth": 590,
		"pieOuterRadius": "77%"
	},
	"data": {
		"sortOrder": "value-desc",
		"content": [
			{
				"label": "Low",
				"value": 34284,
				"color": "#4daa4b"
			},
			{
				"label": "High",
				"value": 3839,
				"color": "#d41d22"
			},
			{
				"label": "Medium",
				"value": 11229,
				"color": "#e6ca0c"
			}
		]
	},
	"labels": {
		"outer": {
			"pieDistance": 33
		},
		"inner": {
			"hideWhenLessThanPercentage": 3
		},
		"mainLabel": {
			"fontSize": 20
		},
		"percentage": {
			"color": "#ffffff",
			"fontSize": 17,
			"decimalPlaces": 0
		},
		"value": {
			"color": "#adadad",
			"fontSize": 20
		},
		"lines": {
			"enabled": true
		},
		"truncation": {
			"enabled": true
		}
	},
	"effects": {
		"pullOutSegmentOnClick": {
			"effect": "linear",
			"speed": 400,
			"size": 8
		}
	},
	"misc": {
		"gradient": {
			"enabled": true,
			"percentage": 100
		}
	}
});
</script>


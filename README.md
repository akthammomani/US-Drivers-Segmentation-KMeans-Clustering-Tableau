# Project:
# Reducing Traffic Mortality in the USA using K-means Clustering Powered by Tableau

How can we find a good stratgey for reducing traffic-related deaths?

## 1. Introduction

![car](https://user-images.githubusercontent.com/67468718/108003465-c2010380-6fa7-11eb-8824-ce140d363179.JPG)

While the rate of fatal road accidents has been decreasing steadily since the 80s, the past ten years have seen a stagnation in this reduction. Coupled with the increase in number of miles driven in the nation, the total number of traffic related-fatalities has now reached a ten year high and is rapidly increasing.

Per request of the US Department of Transportation, we are currently investigating how to derive a strategy to reduce the incidence of road accidents across the nation. By looking at the demographics of traﬃc accident victims for each US state, we find that there is a lot of variation between states. Now we want to understand if there are patterns in this variation in order to derive suggestions for a policy action plan. **In particular, instead of implementing a costly nation-wide plan we want to focus on groups of states with similar profiles. How can we find such groups in a statistically sound way and communicate the result effectively?**

To accomplish these tasks, we will make use of data wrangling, plotting, PCA (dimensionality reduction, unsupervised clustering (K-means) and Tableau.

## 2. Dataset:

The data given to us was originally collected by the National Highway Traffic Safety Administration and the National Association of Insurance Commissioners in <code>**2011**</code>. This particular dataset can be found in this [Location](https://github.com/fivethirtyeight/data/tree/master/bad-drivers) which was based in this [story](https://fivethirtyeight.com/features/which-state-has-the-worst-drivers/)

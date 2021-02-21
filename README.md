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

## 3. Create a textual and a graphical summary of the data

We now have an idea of what the dataset looks like. To further familiarize ourselves with this data, we will calculate summary statistics and produce a graphical overview of the data. The graphical overview is good to get a sense for the distribution of variables within the data and could consist of one histogram per column. It is often a good idea to also explore the pairwise relationship between all columns in the data set by using a using pairwise scatter plots (sometimes referred to as a "scatterplot matrix").

![Pairplot](https://user-images.githubusercontent.com/67468718/108630648-af108800-741a-11eb-90e3-2cbabca082cd.png)

## 4. Quantify the association of features and accidents

<p>We can already see some potentially interesting relationships between the target variable (the number of fatal accidents) and the feature variables (the remaining three columns).</p>
<p>To quantify the pairwise relationships that we observed in the scatter plots, we can compute the Pearson correlation coefficient matrix. The Pearson correlation coefficient is one of the most common methods to quantify correlation between variables, and by convention, the following thresholds are usually used:</p>
<ul>
<li>0.2 = weak</li>
<li>0.5 = medium</li>
<li>0.8 = strong</li>
<li>0.9 = very strong</li>
</ul>

![heatmap](https://user-images.githubusercontent.com/67468718/108630647-af108800-741a-11eb-9b2a-735a97cbd071.png)





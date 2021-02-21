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

## 5. Fit a multivariate linear regression

From the correlation table, we see that the amount of fatal accidents is most strongly correlated with alcohol consumption (first row). But in addition, we also see that some of the features are correlated with each other, for instance, speeding and alcohol consumption are positively correlated. We, therefore, want to compute the association of the target with each feature while adjusting for the effect of the remaining features. This can be done using multivariate linear regression.

Both the multivariate regression and the correlation measure how strongly the features are associated with the outcome (fatal accidents). When comparing the regression coefficients with the correlation coefficients, we will see that they are slightly different. The reason for this is that the multiple regression computes the association of a feature with an outcome, given the association with all other features, which is not accounted for when calculating the correlation coefficients.

A particularly interesting case is when the correlation coefficient and the regression coefficient of the same feature have opposite signs. How can this be? For example, when a feature A is positively correlated with the outcome Y but also positively correlated with a different feature B that has a negative effect on Y, then the indirect correlation (A->B->Y) can overwhelm the direct correlation (A->Y). In such a case, the regression coefficient of feature A could be positive, while the correlation coefficient is negative. This is sometimes called a masking relationship. Let’s see if the multivariate regression can reveal such a phenomenon.

## 6. Visualize the first two principal components

The first two principal components enable visualization of the data in two dimensions while capturing a high proportion of the variation (79%) from all three features: speeding, alcohol influence, and first-time accidents. This enables us to use our eyes to try to discern patterns in the data with the goal to find groups of similar states. Although clustering algorithms are becoming increasingly efficient, human pattern recognition is an easily accessible and very efficient method of assessing patterns in data.

We will create a scatter plot of the first principle components and explore how the states cluster together in this visualization.

![PCA clusters](https://user-images.githubusercontent.com/67468718/108630649-afa91e80-741a-11eb-98f7-0281ba9f9e27.png)

## 7. Modeliing: K-Means Clustering (Choosing K):

The Elbow Method is one of the most popular methods to determine this optimal value of k.

From the above visualization, we can see that the optimal number of clusters should be between 3-5. But visualizing the data alone cannot always give the right answer. Hence we demonstrate the following steps.

Now, let's define the following:-

 * **Distortion:** It is calculated as the average of the squared distances from the cluster centers of the respective clusters. Typically, **the Euclidean distance metric is used.**
 * **Inertia:** it will be calaculated in two methods:
   * It is the sum of squared distances of samples to their closest cluster center. Typically, **inertia_ attribute from kmeans is used.**
   * Lastly, we look at the sum-of-squares error in each cluster against $K$. We compute the distance from each data point to the center of the cluster (centroid) to which the data point was assigned. 

$$SS = \sum_k \sum_{x_i \in C_k} \sum_{x_j \in C_k} \left( x_i - x_j \right)^2 = \sum_k \sum_{x_i \in C_k} \left( x_i - \mu_k \right)^2$$

where $x_i$ is a point, $C_k$ represents cluster $k$ and $\mu_k$ is the centroid for cluster $k$. We can plot SS vs. $K$ and choose the *elbow point* in the plot as the best value for $K$. The elbow point is the point at which the plot starts descending much more slowly. 















# datascientist_project1_bostonairbnb
Analysis of the factors predicting price in boston airbnb data, and their spatial variation

# Air BNB Housing Styles and Prices in Boston

In this post I examine the dataset of AirBNB listing in the Boston area. Data is from [this kaggle dataset](https://www.kaggle.com/airbnb/boston) Plotting by region is inspired by the ResidentMario's excellent geoplot library and its documentation, which plots the price by location on this same dataset (however it is reprocessed here in different way) in its [gallery](https://residentmario.github.io/geoplot/gallery.html).

### Business Questions to Answer

The specific questions I seek to answer are these:

    1. Which areas (grouped by zipcode) have the highest price for AirBNB listing? Which have the lowest?
    2. What factors contribute most strongly to the price of a particular listing?
    3. What factors in the data are correlated, how can I reduce dimensionality and retain the most information?
    4. Are their clusters of listing types in the reduced dimensionality dataset?

### Dependencies

Packages required for this analysis are as follows:

shapely 1.6.4 <br>
scikit-learn 0.19.1 <br>
geopandas 0.4.0 <br>
geoplot 0.2.3 <br>
quilt 2.9.15 <br>

### Using quilt

One note on the quilt library. Quilt is a library for maintaing version controlled datasets, for easy access and reproduction later. In order to map the map plots from the geopandas examples, you will need to use quilt to install the data library from ResidentMario cited above. To install this quilt dataset run the following command:

<code> import quilt </code> <br>
<code> quilt.install("ResidentMario/geoplot_data") </code>

Then you will be able to call data from this data libray like this:

<code> from quilt.data.ResidentMario import geoplot_data </code>

# Summary of Conclusions

Location is an important predictor of price of an AirBNB listing. In particular, proximity to downtown increases cost.

The most important predictors of cost are, in order, AirBNB size (bedrooms, beds, bathrooms), requires guest phone verification, and location.

PCA proves to be quite useful for dimensionality reduction, the top three factors explain almost 90% of the variance. These are cost and cost correlated factors listed above, and factors related to renter risk management (offsetting cost with security deposits and more selective acceptance rates).

Clustering of the datasets with KMeans reveals that renters in more ideal locations closer to downtown have the ability not only to charge more, but also to reject more potential rentees, supply and demand in action. Additionally, by looking at the clustering results, it seems that the region near Quincy and Adam's Shore also contain several "nice" types of AirBNB rentals, due to its role as popular vacation spot for residents of the city itself.

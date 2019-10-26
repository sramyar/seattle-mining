# Installation
Python 3 is used for coding. Packages used are numpy, pandas, and scikit-learn.

# Motivation
Using Seattle Airbnb listings data to answer the following questions:

1. Can we categorize neighborhood vibes using the available data? What is each neighborhood's vibe?
2. What are the busiest times in Seattle? How do prices change in the high season?
3. Can we diagnose some long-term trends in terms of demand and supply for airbnb listings in Seattle?

# Descriptions

There is a jupyter notebook that contains the code for data analysis. The approach taken in this project follows the CRISP-DM framework. Particularly, the following steps have been taken:

1. Business Understanding: The business understanding is motivated by and focused on the three questions discussed above. Mainly, we seek to figure out, using the available data, what are the busiest months in Seattle and how that would impact prices. This question is investigated using exploratory statistics. The other focus is on categorizing neighborhood vibes. We use (unusupervised) machine learning to classify the vibes of each neighborhood based on guests' reviews.

2. Data Understanding: We use the Airbnb Seattle listings (data)[https://www.kaggle.com/airbnb/seattle/data] that contains information on listings, hosts, and reviews from guests. This data is part of the (Inside Airbnb project)[http://insideairbnb.com/about.html]. Particularly, three data sets are available: calendar, that includes the listings availability and prices; reviews, that contains reviews from guests; and listings that include data on listings, the corresponding host and descriptions. The calendar and reviews data sets have been extensively used in this project.

3. Data Preparation: For clustering neighborhoods based on vibes, we concatenate all the reviews to make one larger text. The text is then used for training the KNN model. For finding high seasons, the time series features of the panda library is used. This involves reading in the data and formatting the strings corresponding to each day as dates. The same process is used for preparing the data for long-term trends analysis.

4. Data Modeling: For clustering neighborhood vibes, I tried to focus on guests’ reviews and trained a kNN (k Nearest Neighbors) model using SciKitLearn package. Choosing the number of clusters is a bit ad-hoc but after a couple of trial and errors, it converged to 5 as the best option. Using this method, and particularly the embedded TF-IDF approach for finding key words in each cluster, led to a surprisingly interesting categorization of neighborhood vibes. We can then roughly predict each neighborhood’s vibe using the trained model.

For analyzing high season, I use the reviews data set. This is because if guests have left a review for a room, they must have stayed there very recently. It’s unlikely to leave a review for the place you stayed after a month; especially since the host’s review can also be visible only once the guests leave their review. So, using the time series features of the panda library, I plotted the monthly average frequencies of reviews for 2015.

For long-term trend analysis, I plot the monthly average of room occupancy over a period of years based on reviews data.

5. Evaluating results: For neighborhood vibes, for instance, in one cluster we have words like 'nightlife', 'bars', 'restaurants' and in another we can see terms such as 'market', 'museum', and 'pike' and in another we see words like 'walking', 'park', 'quiet', 'university'. This gives us some confidence in that the clustering approach has captured some of the characteristics of each neighborhood.

For high season, the long-term trend can be seen as a validation of the results. We can see the exact same trends in previous years that verifies our conclusion as the summer times being the most popular time for vising Seattle.

# Results
The findings are posted on this [article](https://medium.com/@sepehr.ramyar/seattle-rediscovered-88352cb7a157) in medium.

# Acknowledgments
Credits must be given to StacOverflow for the data. Also thanks to Udacity for the introducing the concepts. Clustering method was introduced in this [article](https://medium.com/@MSalnikov/text-clustering-with-k-means-and-tf-idf-f099bcf95183)

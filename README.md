# Hacking the Oscars


[Click here](https://adrianfo-16.github.io/ADA-adlucere2022-web-page/) to see the data story 
## Team AdLluCeRe

* Adrián Augusto Ferrer Orgaz
* Lluka Stojollari
* Cecilia Stella Mannik
* Raphael Rakotomahanina

## Abstract

In the current age of easy access to humanity's greatest cinematic achievements when we like and how we like, we often wish to seek out the best of the best when looking for a way to spend an afternoon. But what really makes a movie a critical success? Is it an artistic X factor, the result of a director, the cast and the crew pouring their heart and soul into a project, or are there measurable factors that influence if we see a film as "high quality"? Is there a recipe for a critical darling?

In this project we attempt to gain a deeper understanding of what makes a movie a critical success using a data-driven approach. Our analysis takes into account several factors and takes advantage of the large amounts of lexical data provided in the data set using feature extraction.
## Structure 

```bash
|
├── data
|    ├── CMU                                       : contains all the dataset required for this project.
|    ├── clustering                                : contains the .json files from the kmeans and dbscan clustering.
|    ├── plot                                      : contains the temporary saved dataset after preproccesing.
|
├── figs                                           : contains all the images that are used in the data story .
|
├── src
│   ├── Latent_Dirichlet_Allocation.ipynb          : notebook performing LDA analysis finding latent topics.
│   ├── TF-iDF_Clustering.ipynb                    : notebook using TF-IDF matrix on summaries for clustering purposes.
│   ├── data_preprocessing_exploration.ipynb       : notebook containing our preprocessing phase on the merged data.
│   ├── final_statistical_analysis.ipynb           : notebook performing statistical analysis on different features for different quantiles.
|   ├── plot_summary_NLP_processing.ipynb          : notebook that contains NLP processing on plot summaries for each movie.
|   ├── jaccard_clustering.ipynb                   : notebook performing the jaccard approach for clustering purposes over the plot summaries.
|
├── README.md
```
## Research Questions

* Can we profile successful movies?
* What would be the most significant features to seperate movies? 
* How much are plot summaries helpful in identifying "5-star" movies?

### Datasets
Our [main dataset](http://www.cs.cmu.edu/~ark/personas/) contains the data from Wikipedia + aligned metadata extracted from Freebase.
[IMDB dataset](https://www.imdb.com/interfaces/): included as to enrich the selected dataset's features. After analysis only the IMDB score was kept. Despite leading to a decreasing number of complete datapoints (around 20 to 25% of losses), we decided to perform the merge to obtain this interesting score. In order to deal with the data size of 100GB, we perform the analysis and the data extraction on a local machine (code provided on the notebook) before exporting the resulting dataframe ('movie_data_imdbscores.csv') on this GitHub repository.Finally we merged the 5 initial dataframes into one dataframe with the objective of completing missing values through common features.

### Data Preprocessing and Feature Extraction

Convertion of string features that combine all languages, countries and genres of a given movies into more computational-friendly features such as several columns in the main dataframe. Correcting repetitive values that are seen as different e.g. different english languages. Selecting only the most present languages, countries and genres to reduce the number of different categories.Creation of new features that appear relevant such as gender ratio, number of positive words in the plot, indicators for translations given the most present languages. Testing some agglomerative clustering on text data using Jaccard distance on word sets.  Basic NLP processing of plot summaries and titles such as stopwords removal, performing lemmatization , punctuantion removal also we removed digits and one letter strings for ease of analysis and performing LDA topic modeling.

### Plot Summary Encoding
Using plot summaries in the analysis, we perform “feature engineering” on them and encode them into a numerical representation for further analysis.
We generate two different representations of plot summaries with two different techniques.

#### LDA
So our first approach is performing LDA topic modeling and find the latent topic ditribution over the movies.We used the coherence score to compare the models in order to fine-tune the topic parameter for the LDA technique, and in the end we chose the model with the lowest score. We also extract a list of "prototype" movies for each topic, namely the top five weighted probability movies on each topic based on the movie-topic matrix distribution.

#### Factor Analysis
As our second approach we manage to make three significant separations of the movies based on plot summaries depending on whether they “belong” to one of 3 computed categories named factors. We assigned each movie to one of them and since we have three groups of movies we perform statistical analysis running T-tests on mean proportions for our categorical variables and means for the numeric variables.

### Statistical IMDb Score Analysis
For the statistical analysis part we first discretize the imdb average rating into 5 quantiles analogously to ratings in terms of number of stars. We then split the dataset into two categories: movies with 5-star ratings and movies with ratings below 5 stars.First, we conduct t-tests to determine if the difference in the mean values of the features between 5-star and non-5-star movies is statistically significant.This requires a large number of comparisons, thus the standard p-value of 0.05 needs to be corrected.We therefore sort the features by increasing order of p-value and in the end we filter out the features most likely to have a strong effect on success by analyzing the mean differences between the features after standardization.

#### For more advices how to hack Oscars , you should go through the data story. Happy hacking!
# Hacking the Oscar

## Abstract

In the current age of easy access to humanity's greatest cinematic achievements when we like and how we like, we often wish to seek out the best of the best when looking for a way to spend an afternoon. But what really makes a movie a critical success? Is it an artistic X factor, the result of a director, the cast and the crew pouring their heart and soul into a project, or are there measurable factors that influence if we see a film as "high quality"? Is there a recipe for a critical darling?

In this project we attempt to gain a deeper understanding of what makes a movie a critical success using a data-driven approach. Our analysis takes into account several factors and takes advantage of the large amounts of lexical data provided in the data set using feature extraction.

## Research Questions

* Is it possible to relevantly assemble movies between each others?
* In that case, what would be the most significant features to seperate movies? 
* Are those significant features always the same over time? 
* Do these clusters allow us to predict the imdb score nowadays?


## Additional Datasets

[IMDB dataset](https://www.imdb.com/interfaces/): included as to enrich the selected dataset's features. After analysis only the IMDB score was kept. Despite leading to a decreasing number of complete datapoints (around 20 to 25% of losses), we decided to perform the merge to obtain this interesting score. In order to deal with the data size of 100GB, we perform the analysis and the data extraction on a local machine (code provided on the notebook) before exporting the resulting dataframe ('movie_data_imdbscores.csv') on this GitHub repository. 

## Methods

### Dataset Description

Merge of the 5 initial dataframes into one dataframe with the objective of completing missing values through common features. Conversion of some feature in the datetime format. Plot of the feature missing values ratio.

### Preprocessing

Convertion of string features that combine all languages, countries and genres of a given movies into more computational-friendly features such as several columns in the main dataframe. Correcting repetitive values that are seen as different e.g. different english languages. Selecting only the most present languages, countries and genres to reduce the number of different categories.  Basic NLP processing of plot summaries and titles for ease of analysis.

### Feature Extraction

Creation of new features that appear relevant such as gender ratio, number of positive words in the plot, indicators for translations given the most present languages. Testing some agglomerative clustering on text data using Jaccard distance on word sets.

### IMDB Processing

Merge based on the movie title of the IMDB dataset in order to obtain the score given by the public.


## Proposed Timeline

* 11 Dec 2022: Cluster code + clusters changes over time + statistical tests to compare clusters
  * Anova / t-tests / other? to be tested
  * 2 or 3 clusters algorithms
  * comparison of clustering performance 
               
* 18 Dec 2022: Machine Learning methods to predict imdb score from the clusters infos
  * NN / Random forest / other? to be tested
  * comparison of ML methods performance
          
* 21 Dec 2022: Correction + Harmonization + Commenting + Plotting

* 23 Dec 2022: Website implementation

## Team Organization

* **Ad**rián: cluster method 1 + time changes + ML method 2 + Web page
* **Llu**ka: cluster method 1 + stats method 1 + ML method 1 + corrections
* **Ce**cilia: cluster method 2 + time changes + ML method 1 + corrections
* **R**aphael: cluster method 2 + stats method 2 + ML method 2 + corrections

## Questions for TAs

None for now

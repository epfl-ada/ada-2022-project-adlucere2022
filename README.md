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

* Dataset Description

* Preprocessing

* Feature Extraction

* IMDB Processing

* Natural Language Processing:

* Jaccard Distance Computation:


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

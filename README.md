# Time-Series-Classification-for-Exoplanet-Discovery
Time series classification machine learning techniques for the discovery of exoplanet signatures in light curves.

![](img/exoplanet1.jpg)
Image from https://www.nasa.gov/feature/jpl/cosmic-milestone-nasa-confirms-5000-exoplanets.

## Introduction

Exoplanets are planets that orbit stars other than our Sun. Exoplanets can be discovered by researchers on Earth in several ways.
One of the most successful methods for discovering exoplanets has proven to be the Transit Method, also called Transit Photometry. 
Thousands of exoplanets have been identified orbiting other stars in our galaxy using transit photometry. 

On March 21, 2022 NASA confirmed that the 5K threshold for exoplanet discoveries had been reached, a truly remarkable accomplishment but
no doubt destined to be far surpassed by an exploding number of new discoveries in the near future.

Here is the beginning of the article on the NASA site (https://www.nasa.gov/feature/jpl/cosmic-milestone-nasa-confirms-5000-exoplanets):

"The count of confirmed exoplanets just ticked past the 5,000 mark, representing a 30-year journey of discovery led by NASA space telescopes.
Not so long ago, we lived in a universe with only a small number of known planets, all of them orbiting our Sun. But a new raft of discoveries marks a scientific high point: More than 5,000 planets are now confirmed to exist beyond our solar system."


## Data

The "Exoplanet Hunting in Deep Space" dataset from Kaggle is used in this study. This data consistes of labeled time series data
from the Kepler space telescope. More info about the dataset and the actual data files can be found here: https://www.kaggle.com/datasets/keplersmachines/kepler-labelled-time-series-data.

An important observation about this dataset is that it only contains 40 instances of the positive class (i.e., exoplanet discovery) and 5615 instances of the negative class (no exoplanet). The classes are imbalanced.
Many strategies exist to address imbalanced datasets in machine learning problems. These include:

	1) Undersample the majority class. Can combine with an ensembling strategy to avoid removing data samples.
	2) Oversample the minority class. SMOTE, ADASYN, and Generative Models and are variations on this strategy with varying levels of sophistication.
	3) Set hyperparameters to give more weight to the minority class (example is setting scale_pos_weight in XGBoost).

We will implement several of these in this notebook and study the impact they have on our models.

## Feature Extraction

We transform the time series classification problem into a tabular matrix of features by extracting features from the time series. 
The Time Series FeatuRe Extraction on the basis of Scalable Hypothesis tests (tsfresh) library of feature extractors was used to 
accomplish the extraction. See Christ, Maximilian, et al. "Time series feature extraction on basis of scalable hypothesis tests (tsfresh–a python package)." Neurocomputing 307 (2018): 72-77, for details on the library.

## Model

Several models and model variations are implemented in the study. These include:

1) Balanced XGBoost baseline: An XGBoost classification model with default parameters and settings.
The dataset is approximately balanced by selecting the first 100 negative measurements (negative=no exoplanet discovered) combined
with all 40 positive explanet discoveries. A randomly selected 20% of the under-sampled dataset is used for the test set.


## Model Evaluation

Balanced XGBoost Baseline:
	accuracy: 0.931
	precision: 0.909
	recall: 1.0
	f1: 0.952
	roc_auc: 0.889

## Discussion

(TBD)

## Next Steps

(TBD)

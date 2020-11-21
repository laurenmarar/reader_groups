# Reader Groups
Exploring potential for creating reader interest groups based on Goodreads data

## Overview
This script analysizes user shelf data from Goodreads to assess its usefullness in defining reader interest groups. It uses the Goodreads API to gather data from over 120,000 randomly selected users and their shelves. It identifies the users with sufficient and recent content and creates a dataframe for analysis. It then implements Principal Component Analysis (PCA) and several cluster analyses to attempt to group users based on the genres they read. While the results did not yield meaningful clusters, the data do reveal that sparsity and lack of standardization in shelf labels are limiting the usefulness of the shelf data set. 

## Getting Started

### Request Goodreads API token
https://www.goodreads.com/api
https://pypi.org/project/goodreads-api-client/

### Python version: 
3.6.12

### Python libraries
```
import goodreads_api_client as gr
import pandas as pd
import numpy as np
from datetime import date
import random
import io 
import ast
import seaborn as sns
import matplotlib.pyplot as plt

from sklearn.decomposition import PCA
from sklearn.cluster import AgglomerativeClustering
from sklearn.cluster import DBSCAN
from sklearn.cluster import KMeans
from sklearn import mixture
from sklearn.metrics import silhouette_score
```
## Files

### Jupyter Notebook
ReaderClusters.py contains the following code:

#### Data Understanding
- Collecting data on a random selection of users and user shelves via the Goodreads API
- Storing data in dataframes and saving as csv files for easy access

#### Data Preparation
- Examining distribution of data 
- Cleaning hyper-unique shelf names by mapping them to more common names 
- Addressing skewed and sparse data
- Combining user and user shelves data sets

#### Modeling 
- Different thresholds for minimum number of users per shelf/shelves per user were tested in conjunction with principal component analysis and several cluster analyses: K-means, Ward and Average Linkages Clustering. 
- Visual of PCA highlights what genres are associated with each component.

#### Evaluation
- All cluser analyses showed low silhouette scores. The highest was K-means with PCA, with a silhouette score of .2.

#### Appendix
- Notebook contains additional views of user/shelf data, with descriptive statistics on age and geographical location.

### Shelf Dictionary
shelf_dictionary.txt - used in Jupyter Notebook to map uncommon shelf spellings to common spellings

## Conclusion
The Goodreads user shelf data is sparse and higlighy variable. There is potential generating more accurate reader profiles with more complete and standardized data. A blog post explores possibilities for future analysis in greater depth: 

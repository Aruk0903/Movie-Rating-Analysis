# Movie-Rating-Analysis

Analyzing the rating given by viewers of a movie helps many people decide whether or not to watch that movie. So, for the Movie Rating Analysis task, you first need to have a dataset that contains data about the ratings given by each viewer. For this task, I have collected a dataset from Kaggle that contains two files:

1. one file contains the data about the movie Id, title and the genre of the movie 
2. and the other file contains the user id, movie id, ratings given by the user and the timestamp of the ratings

Now let’s get started with the task of movie rating analysis by importing the necessary Python libraries and the datasets:
```python
import numpy as np
import pandas as pd
movies = pd.read_csv("movies.dat", delimiter='::')
print(movies.head())
```

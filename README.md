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
In the above code, I have only imported the movies dataset that does not have any column names, so let’s define the column names:

```python
movies.columns = ["ID", "Title", "Genre"]
print(movies.head())
```

Now let’s import the ratings dataset:
```python
ratings = pd.read_csv("ratings.dat", delimiter='::')
print(ratings.head())
```
The rating dataset also doesn’t have any column names, so let’s define the column names of this data also:
```python
ratings.columns = ["User", "ID", "Ratings", "Timestamp"]
print(ratings.head())
```
Now I am going to merge these two datasets into one, these two datasets have a common column as ID, which contains movie ID, so we can use this column as the common column to merge the two datasets:
```python
data = pd.merge(movies, ratings, on=["ID", "ID"])
print(data.head())
```

I will first have a look at the distribution of the ratings of all the movies given by the viewers
```python
ratings = data["Ratings"].value_counts()
numbers = ratings.index
quantity = ratings.values
import plotly.express as px
fig = px.pie(data, values=quantity, names=numbers)
fig.show()
```

So, according to the pie chart above, most movies are rated 8 by users. From the above figure, it can be said that most of the movies are rated positively.

As 10 is the highest rating a viewer can give, let’s take a look at the top 10 movies that got 10 ratings by viewers:

```python
data2 = data.query("Ratings == 10")
print(data2["Title"].value_counts().head(10))
```

So, according to this dataset, Joker (2019) got the highest number of 10 ratings from viewers. 





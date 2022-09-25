# Movie-Rating-Analysis

Many individuals decide if they want to watch a movie based on the ratings offered by viewers. So, for the Movie Rating Analysis, we must first need to have a dataset including data about the ratings given by each viewer. I have used two files from Kaggle.

1. Movies file that contains the data about the movie Id, the title of the movie and the genre of the movie.
2. Ratings file that contains the user id, movie id, ratings given by each user along with the timestamp.

Importing the required Python libraries and datasets:
```python
import numpy as np
import pandas as pd
movies = pd.read_csv("movies.dat", delimiter='::')
print(movies.head())
```
![image](https://user-images.githubusercontent.com/89111546/192160490-047dbe1b-6067-4c5a-829b-1b48f9425769.png)

The movies dataset does not have column names, so let’s define the column names:

```python
movies.columns = ["ID", "Title", "Genre"]
print(movies.head())
```
![image](https://user-images.githubusercontent.com/89111546/192160543-5210168d-ebd0-47e6-8bba-3d0758dc77f8.png)

Now let’s import the ratings dataset:
```python
ratings = pd.read_csv("ratings.dat", delimiter='::')
print(ratings.head())
```
![image](https://user-images.githubusercontent.com/89111546/192160568-11749962-9a4f-428a-9edc-0fc3032174b9.png)

The rating dataset also does not have any column names, so let’s define the column names here too:
```python
ratings.columns = ["User", "ID", "Ratings", "Timestamp"]
print(ratings.head())
```
![image](https://user-images.githubusercontent.com/89111546/192160589-e8df208f-9edd-4e65-b8b7-ce99de50903c.png)

Now lets merge these two datasets into one, these two datasets have a common column as ID, which contains movie ID, so we can use this column to merge the two datasets:
```python
data = pd.merge(movies, ratings, on=["ID", "ID"])
print(data.head())
```
![image](https://user-images.githubusercontent.com/89111546/192160618-6802d217-ac0f-4873-84ff-d1d8790c43b3.png)

Lets have a look at the distribution of the ratings of all the movies given by the viewers
```python
ratings = data["Ratings"].value_counts()
numbers = ratings.index
quantity = ratings.values
import plotly.express as px
fig = px.pie(data, values=quantity, names=numbers)
fig.show()
```
![image](https://user-images.githubusercontent.com/89111546/192160635-245e4c8f-22d3-4abd-890b-3d06afd881eb.png)

So, according to the pie chart above, most movies are rated 8 by users. From the above figure, it can be said that most of the movies are rated positively.

As 10 is the highest rating a viewer can give, let’s take a look at the top 10 movies that got 10 ratings by viewers:

```python
data2 = data.query("Ratings == 10")
print(data2["Title"].value_counts().head(10))
```
![image](https://user-images.githubusercontent.com/89111546/192160650-48bf592a-e567-44f5-8334-a20e7d87f00a.png)

So, according to this dataset, Joker (2019) got the highest number of 10 ratings from viewers. 





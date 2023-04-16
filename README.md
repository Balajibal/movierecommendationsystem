# Content Based Movie Recommendation

This is a content based movie recommendation system

## Dataset

The dataset is taken from kaggle This database consist of 5000 movies from imdb. It is available on https://www.kaggle.com/datasets/carolzhangdc/imdb-5000-movie-dataset

![image](https://user-images.githubusercontent.com/75234946/232274367-446a0cb8-8869-4182-96ae-452e4acd10f1.png)

## Steps

## step 1:

Collect the dataset

## step 2:

Import the required packages

## step 3:

Select the features required for content based recommendation(genres,title,director,tagline,cast are taken here)

## step 4:

Convert the features into numerical values using vectorization

## step 5:

Using difflib library the closest match is found

## step 6:

The list of movies is sorted based on similarity

## step 7:

The Favorite movie of user is taken and the similar movies in the list are recommended 

## Program
```python

import numpy as np
import pandas as pd
import difflib
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
df = pd.read_csv('/content/movies.csv',sep='delimiter', header=None)
features=['genres','keywords','tagline','cast','director']
features
rel_feature=df['genres']+' '+df['keywords']+' '+df['tagline']+' '+df['cast']+' '+df['director']
print(rel_feature)
vectorizer=TfidfVectorizer()
vvec=vectorizer.fit_transform(rel_feature)
print(vvec)
similarity=cosine_similarity(vvec)
print(similarity)
movie_name=input('Enter your Favourite movie name: ')
mov_list=df['title'].tolist()
print(mov_list)
find_close_match=difflib.get_close_matches(movie_name,mov_list)
print(find_close_match)
close_match=find_close_match[0]
print(close_match)
print(similarity_score)
print(sorted_similar_movies)
print('Movies suggested for you : \n')

i = 1

for movie in sorted_similar_movies:
  index = movie[0]
  title_from_index = df[df.index==index]['title'].values[0]
  if (i<30):
    print(i, '.',title_from_index)
    i+=1
    
movie_name = input(' Enter your favourite movie name : ')

list_of_all_titles = df['title'].tolist()

find_close_match = difflib.get_close_matches(movie_name, list_of_all_titles)

close_match = find_close_match[0]

index_of_the_movie = df[df.title == close_match]['index'].values[0]

similarity_score = list(enumerate(similarity[index_of_the_movie]))

sorted_similar_movies = sorted(similarity_score, key = lambda x:x[1], reverse = True)

print('Movies suggested for you : \n')

i = 1

for movie in sorted_similar_movies:
  index = movie[0]
  title_from_index = df[df.index==index]['title'].values[0]
  if (i<30):
    print(i, '.',title_from_index)
    i+=1
```

## Output

![image](https://user-images.githubusercontent.com/75234946/232275053-82b5ea77-cb38-4859-990f-12d54c932c4e.png)

![image](https://user-images.githubusercontent.com/75234946/232275096-7a3a9571-61b4-445c-896b-fdfae6840f35.png)







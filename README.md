# Movie-Recommendations-system

There are basically **three** types of recommender systems:-

**Demographic Filtering** - They offer generalized recommendations to every user, based on movie popularity and/or genre. The System recommends the same movies to users with similar demographic features. Since each user is different , this approach is considered to be too simple. The basic idea behind this system is that movies that are more popular and critically acclaimed will have a higher probability of being liked by the average audience.

**Content Based Filtering** - They suggest similar items based on a particular item. This system uses item metadata, such as genre, director, description, actors, etc. for movies, to make these recommendations. The general idea behind these recommender systems is that if a person liked a particular item, he or she will also like an item that is similar to it.

**Collaborative Filtering** - This system matches persons with similar interests and provides recommendations based on this matching. Collaborative filters do not require item metadata like its content-based counterparts.

In this repository I have made three python kernels explaining and implementing the different types of movie recommender systems.

A webapp built using streamlit to display movie recommendation based on contect based filtering using cosine similarity. 

- It gives recommendations based on movie content.
- One can give the movie title or director's name to get appropriate movie recommendations.


After preprocessing the datasets I decided to keep these columns in order to proceed further

| Column | Description |
| --- | --- |
| Movie ID | Unique ID for identification of movie and fetch appropriate poster for the same |
| Title| Title was used to get recommendations |
| Tags | Tags column was made using 'Overview','Cast','Genres','Keywords','Crew'|
| crew | Kept it to fetch recommendations based on Directors |

## Built With

* Python 3.6
* nltk.stem.porter
* CountVectorizer
* cosine_similarity


https://user-images.githubusercontent.com/60546202/161950725-29351f71-2dd9-4c10-a112-4ebe3c92d29c.mp4


## How to run the project

1. Clone this repository to your local machine.
2. Install all the libraries mentioned in the [requirements.txt](https://github.com/santanukumar666/Movie-Recommendations-System/blob/main/requirements.txt) file with the command `pip install -r requirements.txt`
3. Open your terminal/command prompt from your project directory and run the file `app.py` by executing the command `streamlit run app.py`.

## What I plan to do next

- Make some changes in the UI and also shift it to flask webapp.
- Improve my predictions and also implement collabrative,demographic and hybrid filtering based recommendations.

Datasets - [The Movie Dataset](https://www.kaggle.com/rounakbanik/the-movies-dataset) , [TMDB Movie Dataset](https://www.kaggle.com/tmdb/tmdb-movie-metadata)

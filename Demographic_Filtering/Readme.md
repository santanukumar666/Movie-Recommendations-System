## Movie Recommendations using Demographic Filtering
In this kernel we'll be building a baseline Movie Recommendation System using TMDB 5000 Movie Dataset. For novices like me this kernel will pretty much serve as a foundation in recommendation systems and will provide you with something to start with.

In this kernel we would be using demographic filtering to recommend movies.

The first dataset contains the following features:- movie_id - A unique identifier for each movie.
```
cast - The name of lead and supporting actors.

crew - The name of Director, Editor, Composer, Writer etc.
```
The second dataset has the following features:- 
```
budget - The budget in which the movie was made.

genre - The genre of the movie, Action, Comedy ,Thriller etc.

homepage - A link to the homepage of the movie.

id - This is infact the movie_id as in the first dataset.

keywords - The keywords or tags related to the movie.

original_language - The language in which the movie was made.

original_title - The title of the movie before translation or adaptation.

overview - A brief description of the movie.

popularity - A numeric quantity specifying the movie popularity.

production_companies - The production house of the movie.

production_countries - The country in which it was produced.

release_date - The date on which it was released.

revenue - The worldwide revenue generated by the movie.

runtime - The running time of the movie in minutes.

status - "Released" or "Rumored".

tagline - Movie's tagline.

title - Title of the movie.

vote_average - average ratings the movie recieved.

vote_count - the count of votes recieved.
```
Before getting started with demographic filtering -

- We need a metric to score or rate movie

- Calculate the score for every movie

- Sort the scores and recommend the best rated movie to the users.

We can use the average ratings of the movie as the score but using this won't be fair enough since a movie with 8.9 average rating and only 3 votes cannot be considered better than the movie with 7.8 as as average rating but 40 votes. So, I'll be using IMDB's weighted rating (wr) which is given as :-

![weighted_rating](https://user-images.githubusercontent.com/60546202/157710388-1b11481d-9ed1-49c9-825b-509abb7ddcf0.png)

- v is the number of votes for the movie;

- m is the minimum votes required to be listed in the chart;

- R is the average rating of the movie; And

- C is the mean vote across the whole report

We see that there are 481 movies which qualify to be in this list.
Now, we need to calculate our metric for each qualified movie. To do this, we will define a function, weighted_rating() and define a new feature score, of which we'll calculate the value by applying this function to our DataFrame of qualified movies.


These demographic recommendendations provide a general chart of recommended movies to all the users. They are not sensitive to the interests and tastes of a particular user. This is when we move on to a more refined system- Content Basesd Filtering.

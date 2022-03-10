## Movie Recommendations using Collaborative Filtering
In this kernel we'll be building a baseline Movie Recommendation System using The Movie Dataset on kaggle. For novices like me this kernel will pretty much serve as a foundation in recommendation systems and will provide you with something to start with.

In this kernel we would be using collaborative filtering to recommend movies.

Our content based engine suffers from some severe limitations. It is only capable of suggesting movies which are close to a certain movie. It is not capable of capturing tastes and providing recommendations across genres.

Also, the engine that we built is not really personal. That is it doesn't capture the personal tastes and biases of a user. Anyone querying our engine for recommendations based on a movie will receive the same recommendations for that movie, regardless of who she/he is.

Therefore, in this section, we will use a technique called Collaborative Filtering to make recommendations to Movie Watchers. It is basically of two types :-

- User based filtering- These systems recommend products to a user that similar users have liked. For measuring the similarity between two users we can either use pearson correlation or cosine similarity. This filtering technique can be illustrated with an example. In the following matrixes, each row represents a user, while the columns correspond to different movies except the last one which records the similarity between that user and the target user. Each cell represents the rating that the user gives to that movie. Assume user E is the target.

![user_similarity_1](https://user-images.githubusercontent.com/60546202/157715682-59c03d82-7ff0-4f5b-ba62-62639b147716.png)

Since user A and F do not share any movie ratings in common with user E, their similarities with user E are not defined in Pearson Correlation. Therefore, we only need to consider user B, C, and D. Based on Pearson Correlation, we can compute the following similarity.

![user_similarity_2](https://user-images.githubusercontent.com/60546202/157715718-6f2dcdc2-f66f-4471-8739-4f0444e4cc7c.png)

From the above table we can see that user D is very different from user E as the Pearson Correlation between them is negative. He rated Me Before You higher than his rating average, while user E did the opposite. Now, we can start to fill in the blank for the movies that user E has not rated based on other users.

![user_similarity_3](https://user-images.githubusercontent.com/60546202/157715745-bc152204-9f6b-4f37-84e2-a1d0803a1664.png)

Although computing user-based Collaborative Filtering is very simple, it suffers from several problems. One main issue is that user preference can change over time. It indicates that precomputing the matrix based on their neighboring users may lead to bad performance. To tackle this problem, we can apply item-based Collaborative Filtering.

- Item Based Collaborative Filtering- Instead of measuring the similarity between users, the item-based Collaborative Filtering recommends items based on their similarity with the items that the target user rated. Likewise, the similarity can be computed with Pearson Correlation or Cosine Similarity. The major difference is that, with item-based collaborative filtering, we fill in the blank vertically, as oppose to the horizontal manner that user-based Collaborative Filtering does. The following table shows how to do so for the movie Me Before You.

![item_similarity](https://user-images.githubusercontent.com/60546202/157715826-0b19b096-a1c8-400b-8f49-c25d808c4728.png)

It successfully avoids the problem posed by dynamic user preference as item-based Collaborative Filtering is more static. However, several problems remain for this method. First, the main issue is scalability. The computation grows with both the customer and the product. The worst case complexity is O(mn) with m users and n items. In addition, sparsity is another concern. Take a look at the above table again. Although there is only one user that rated both Matrix and Titanic rated, the similarity between them is 1. In extreme cases, we can have millions of users and the similarity between two fairly different movies could be very high simply because they have similar rank for the only user who ranked them both.

### Single Value Decomposition

One way to handle the scalability and sparsity issue created by Collaborative Filtering is to leverage a latent factor model to capture the similarity between users and items. Essentially, we want to turn the recommendation problem into an optimization problem. We can view it as how good we are in predicting the rating for items given a user. One common metric is Root Mean Square Error (RMSE). The lower the RMSE, the better the performance.

Latent factor is a broad idea which describes a property or concept that a user or an item have. For instance, for music, latent factor can refer to the genre that the music belongs to. SVD decreases the dimension of the utility matrix by extracting its latent factors. Essentially, we map each user and each item into a latent space with dimension r. Therefore, it helps us better understand the relationship between users and items as they become directly comparable. The below figure illustrates this idea.

![single_value_decomposition](https://user-images.githubusercontent.com/60546202/157715793-e7f9bf4b-dfb5-4f46-a726-ad051bfdcbaa.png)


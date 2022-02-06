# Recommender System Based on Amazon Beauty Product Ratings

<br>
This is an example of bar charts that are obtained in the data preprocessing and inspection stage. Here, we can see that most products have less than 10 ratings.
<p align="center">
<img width="1025" alt="Screenshot 2022-02-06 at 3 45 02 PM" src="https://user-images.githubusercontent.com/46462603/152704776-673754c4-ff20-408d-8a3c-40fdaf833b02.png">
</p>
<br>

The program is able to find the top k users that are the most similar to a given user based on their ratings on Amazon beauty products. In this example, k is set to be equal to 5.
<p align="center">
<img width="1345" alt="Screenshot 2022-02-03 at 12 26 41 AM" src="https://user-images.githubusercontent.com/46462603/152703084-e7ace2bb-7bfe-4e74-85f5-b954d8d22a67.png">
</p>

<br>

The top m products that the program thinks should be recommended to a given user. In this example, m is set to be equal to 5.
<p align="center">
<img width="1344" alt="Screenshot 2022-02-03 at 12 26 55 AM" src="https://user-images.githubusercontent.com/46462603/152703149-1ee2743d-016d-44a1-bb1d-1e3828913832.png">
</p>

## Goal
To create a recommender system that is able to decide the top m beauty products on Amazon to recommend to a given user where m is a positive integer.

## Dataset 
The dataset contains 4 columns, which are UserId, ProductId, Rating, and Timestamp. In this project, only the first 3 columns are used. I.e., the Timestamp column is ignored. UserId contains the IDs of all users whose ratings have been recorded in this dataset while ProductId contains the IDs of the Amazon beauty products that have their ratings recorded here. The Rating column contains integers from 1 to 5, with 1 being the lowest and 5 being the highest or best rating. 

There are altogether 2,023,070 ratings spanning May 1996 - July 2014. All rows are unique. The csv file that contains this dataset, ratings_Beauty.csv, can be downloaded from <a href="http://jmcauley.ucsd.edu/data/amazon/" target="_blank">Amazon product data</a> by clicking "ratings only" at the row "Beauty". The file is too large to be uploaded to GitHub. 

## Code, files, or folders needed to run the program
- <a href="https://github.com/ZhengEnThan/Amazon-Recommender-System/blob/main/Recommender_System_for_Amazon_Customers.ipynb" target="_blank">Recommender_System_for_Amazon_Customers.ipynb</a>
- ratings_Beauty.csv, which can be downloaded from <a href="http://jmcauley.ucsd.edu/data/amazon/" target="_blank">Amazon product data</a> by clicking "ratings only" at the row "Beauty"

## How to use the program
To decide the top 5 most similar users in terms of ratings and top 5 products to recommend to a random user from the dataset, simply run all the code cells in <a href="https://github.com/ZhengEnThan/Amazon-Recommender-System/blob/main/Recommender_System_for_Amazon_Customers.ipynb" target="_blank">Recommender_System_for_Amazon_Customers.ipynb</a> as they are (without editig them).

- If you want to pick a specific user from the dataset to recommend products to (instead of a random user from the dataset), simply edit the code cell immediately below the markdown "Finding the top k users who are most similar to a chosen user". Assign the ID of the specific user that you chose to the variable user_id. Make sure that the user you chose exists in the dataset ratings_Beauty.csv. 

Edit the code cell to look like this:

```python
from sklearn.metrics.pairwise import cosine_similarity
import operator

# Randomly select a user from the user_item_matrix to be our customer of concern
#random_row_num = np.random.randint(0, user_item_matrix.shape[0] + 1)
#users = user_item_matrix.index.tolist()
#user_id = users[random_row_num]

user_id = A21RYR788TRJZR
print("The chosen user is: ", user_id)
```

Replace "A21RYR788TRJZR" in the code cell above by the ID of the user that you chose.

<br>

- If you want to change the number of most similar users, edit the code cell immediately above the markdown "Recommending top m products to the chosen user".

```python
# Find the top 5 users that are most similar to the chosen user
k = 5

similar_users = top_k_similar(user_id, user_item_matrix, k)
print("The top {} users that are most similar to the chosen user are {}".format(k, similar_users))
```

Replace the value assigned to the variable k with a positive integer that you want. k will be the number of most similar users that you want to find. Edit the comment "# Find the top 5 users that are most similar to the chosen user" so that it matches your k value.

<br>

- If you want to change the number of top products to recommend to the chosen user, edit the last code cell.

```python
# Find the top 5 recommended products
m = 5

top_products = top_m_products(user_id, similar_users, user_item_matrix, m)
print("The top {} recommended products are {} ".format(m, top_products))
```
Replace the value assigned to the variable m with a positive integer that you want. m will be the number of top products that you want to recommend to the chosen user. Edit the comment "# Find the top 5 recommended products" so that it matches your m value.

## What have I learned
- Used pandas to create a dataframe from the given csv file and used various functions from pandas such as head(), duplicated(), sum(), unique(), isnull(), any(), value_counts(), counts(), groupby(), sort_values(), nlargest() and numpy functions such as mean() to inspect the dataset by checking if there are duplicate rows, computing the number of ratings received by each product, and so on.
- Used plotly.graph_objects to display interactive bar charts and histograms to visualize the different properties of the dataset such as the number of ratings and the number of users who give that amount of ratings, number of ratings and the number of products that received that amount of ratings and so on.
- Used sklearn.preprocessing to encode alphanumerical data as numerical data.
- Used the pandas function pivot_table to create a user-item matrix where each row corresponds to a user and each column represents a product. Each entry contains a rating. 
- Used the cosine_similarity function from sklearn.metrics.pairwise to compute the cosine similarity between the chosen user and other users in terms of their ratings.

## Main libraries or modules used
- pandas
- numpy
- plotly.graph_objects
- sklearn
- operator

## Approaches 
In this project, I decided to explore collaborative filtering as a way to decide which products to recommend to a specific user. There are other methods to implement a recommender system such as using a content-based approach. In collaborative filtering, it is assumed that if user A and user B have similar ratings to several products, we can interpret this as the users having similar "tastes" or liking similar things. Hence, if user B likes product 123 which user A has never bought before, we can recommend product 123 to user A in hope that user A will like this product too.

Cosine similarity is used to decide how similar 2 users are in terms of their ratings. I prefer cosine similarity over Euclidean distance because cosine similarity focus more on the features rather than the magnitudes. For example, by using Euclidean distance, person A who bought 100 eggs, 100 carrots, and 100 drumsticks might be considered as more similar to person B who bought 100 eggs, 100 broccolis, and 100 sausages instead of person C who bought 10 eggs, 10 carrots, and 10 drumsticks. On the other hand, cosine similarity will tell us that person A is more similar to person C than person B. 

The consine similarity that I used is also "centered". This means that the ratings of all the products in the dataset are normalized for each user. This makes the ratings less biased. If these ratings are not normalized, a missing rating, which is denoted by 0, might be treated as the worst rating. A user not buying a product does not necessarily imply that the user dislikes the product. It might simply be the case that the user has not seen the product before. Hence, normalizing the ratings for each user will cause 0 ratings to be "neutral" instead of "worst".

A user's rating of 5 might be the same as another user's rating of 4 in terms of how much they like a product. This is because different people define their feelings differently. Therefore, the ratings are normalized for each user to negate this difference or bias.

I have also removed several entries in the dataset as the original dataset is very large and sparse. I decided to remove products that have less than or equal to 200 ratings. It is up to you to decide whether you want to leave the dataset as it is or reduce its size or sparsity in another way. 

## Comments
It is difficult to evaluate how good the model is performing. One way to do it may be choosing a user, removing his 5.0 ratings for some of the products, and checking if those products are listed in the top m recommended products or not. However, this is still not a good way to tell whether the model is performing well. If the product that the user rated 5 for does not fall into the top m recommended products, does this necessarily mean the model is not doing well? The user could equally like the other products that are recommended. 

Just like most models employed in real-life settings, the best way to evaluate and implement this model is by consistently monitoring and improving it. If a user reports that he dislikes a product that this program has recommended to him, we can then adjust the model by changing how it works and reevaluate it. For example, we can try to use content-based filtering or even a mix of both content-based filtering and collaborative filtering instead. 

## References
- Matrix Normalization with Centered Cosine Similarity before using Cosine Similarity (movie recommendation system) <br>
https://www.reddit.com/r/statistics/comments/7o4i9v/matrix_normalization_with_centered_cosine/
- A comparison of cosine similarity vs Euclidean distance in ALS recommendation engine <br>
https://medium.com/nerd-for-tech/a-comparison-of-cosine-similarity-vs-euclidean-distance-in-als-recommendation-engine-51898f9025e7#:~:text=According%20to%20my%20research%2C%20it's,the%20factors%20have%20actual%20meaning
- Cosine Similarity Vs Euclidean Distance <br>
https://medium.com/@sasi24/cosine-similarity-vs-euclidean-distance-e5d9a9375fc8
- Why is the cosine distance used to measure the similatiry between word embedding <br>
https://datascience.stackexchange.com/questions/81169/why-is-the-cosine-distance-used-to-measure-the-similatiry-between-word-embedding
- Collaborative Filtering Vs Content-Based Filtering for Recommender Systems <br>
https://analyticsindiamag.com/collaborative-filtering-vs-content-based-filtering-for-recommender-systems/
- Collaborative filtering <br>
https://en.wikipedia.org/wiki/Collaborative_filtering
- Why you should remove the top products in a recommender system? <br>
https://www.researchgate.net/post/Why_you_should_remove_the_top_products_in_a_recommender_system

~ Project created in June 2021 ~

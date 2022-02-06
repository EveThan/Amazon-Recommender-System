# Recommender System Based on Amazon Beauty Product Ratings

<br>

The program is able to find the top k users that are the most similar to a given user based on their ratings on Amazon beauty products. In this example, k is set to be equal to 5.
<p align="center">
<img width="1345" alt="Screenshot 2022-02-03 at 12 26 41 AM" src="https://user-images.githubusercontent.com/46462603/152703084-e7ace2bb-7bfe-4e74-85f5-b954d8d22a67.png">
</p>

<br>

The top k products that the program thinks should be recommended to a given user. In this example, k is set to be equal to 5.
<p align="center">
<img width="1344" alt="Screenshot 2022-02-03 at 12 26 55 AM" src="https://user-images.githubusercontent.com/46462603/152703149-1ee2743d-016d-44a1-bb1d-1e3828913832.png">
</p>

## Goal
To create a recommender system that is able to decide the top k beauty products on Amazon to recommend to a given user where k is a positive integer.

## Dataset 
The dataset contains 4 columns, which are UserId, ProductId, Rating, and Timestamp. In this project, only the first 3 columns are used. I.e., the Timestamp column is ignored. UserId contains the IDs of all users whose ratings have been recorded in this dataset while ProductId contains the IDs of the Amazon beauty products that have their ratings recorded here. The Rating column contains integers from 1 to 5, with 1 being the lowest and 5 being the highest or best rating. 

There are altogether 2,023,070 ratings. I have checked that all rows are unique. The csv file that contains this dataset, ratings_Beauty.csv, can be downloaded from <a href="http://jmcauley.ucsd.edu/data/amazon/" target="_blank">Amazon product data</a> by clicking "ratings only" at the row "Beauty". The file is too large to be uploaded to GitHub. 

## Code, files, or folders needed to run the program
- <a href="https://github.com/ZhengEnThan/Amazon-Recommender-System/blob/main/Recommender_System_for_Amazon_Customers.ipynb" target="_blank">Recommender_System_for_Amazon_Customers.ipynb</a>
- ratings_Beauty.csv, which can be downloaded from <a href="http://jmcauley.ucsd.edu/data/amazon/" target="_blank">Amazon product data</a> by clicking "ratings only" at the row "Beauty"

## How to use the program
To decide the top 5 most similar users in terms of ratings and top 5 products to recommend to a random user from the dataset, simply run all the code cells in <a href="https://github.com/ZhengEnThan/Amazon-Recommender-System/blob/main/Recommender_System_for_Amazon_Customers.ipynb" target="_blank">Recommender_System_for_Amazon_Customers.ipynb</a> as they are (without editig them).

If you want to pick a specific user from the dataset to recommend products to (instead of a random user from the dataset), simply 

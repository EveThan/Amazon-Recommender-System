# Recommender System Based on Amazon Beauty Product Ratings

<br>

The program is able to find the top 5 users that are the most similar to a given user based on their ratings on Amazon beauty products.
<p align="center">
<img width="1345" alt="Screenshot 2022-02-03 at 12 26 41 AM" src="https://user-images.githubusercontent.com/46462603/152703084-e7ace2bb-7bfe-4e74-85f5-b954d8d22a67.png">
</p>

<br>

The top 5 products that the program thinks should be recommended to a given user.
<p align="center">
<img width="1344" alt="Screenshot 2022-02-03 at 12 26 55 AM" src="https://user-images.githubusercontent.com/46462603/152703149-1ee2743d-016d-44a1-bb1d-1e3828913832.png">
</p>

## Goal
To create a recommender system that is able to decide what beauty products on Amazon to recommend to a given user.

## Dataset 
The dataset contains 4 columns, which are UserId, ProductId, Rating, and Timestamp. In this project, only the first 3 columns are used. I.e., the Timestamp column is ignored. UserId contains the IDs of all users whose ratings have been recorded in this dataset while ProductId contains the IDs of the Amazon beauty products that have their ratings recorded here. The Rating column contains integers from 1 to 5, with 1 being the lowest and 5 being the highest or best rating. 

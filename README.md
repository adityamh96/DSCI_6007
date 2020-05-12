# DSCI_6007
##Statement of objective 
Aim of the project is to use algorithms that help recommend users with similar movie preferences, movies that users might like and maybe haven’t come across yet. The applications for these kinds of algorithms can be seen across variety of industries. These algorithms help drive some key decisions like which movie user is likely to watch next or in case of ecommerce industry it helps the company predict what products a user is likely to buy next. We will be analyzing the collaborative filtering algorithm which is used in most of the recommendation engines that helps drive these decisions.

##Collaborative filtering algorithm 
The basic approach followed by this algorithm is:
1.	In order to make movie recommendations to a user we need to find group of users who have similar preferences to our target user.
2.	We can achieve our first step by finding ratings of movies that our target user has rated and compare them with users who have given ratings for similar movies.
3.	We can use the cosine similarity metric to determine the similarity between users. Higher the cosine similarity metric better will be the similarity between two users.
4.	Our next step will be to determine the accuracy of our prediction. One way to achieve this accuracy is by calculating the root mean square error where we calculate the difference between values that we have predicted and the actual values(test set), do a square of all the error values we have, take an average of those values and square root it.
5.	The lower the RMSE score, better will be the accuracy of our predictions.

##Dataset details
1.	Our dataset is divided between three text files training, testing and movie titles.
2.	We have close to 3.2 million samples in our training data and close to 100,000 values as part of our testing data.
3.	We have movie id, user id and ratings as features of our training and testing data while our movie titles dataset has movie id, year of release and titles as its features.

##Problem 2 – Analyzing the Netflix data
1.	We start off with doing some basic analysis like finding distinct number of users and movies.
2.	In our next step we take a small sample of our training data and build pivot table where the rows are user id, columns are movie id and values are the ratings for the movies provided by the user. Since one user cannot have ratings for all movies we replace those cells with the value 0 instead of keeping it nan.
3.	 We use a similar approach for movies where we replace the rows with movie id, the column with user id and values with ratings. Similar preprocessing is applied to this approach as well.
4.	We then proceed towards computing the cosine similarity. When we compute cosine similarity between two users we are essentially doing user based collaborative filtering and the one between movies is called as item based collaborative filtering.
5.	Our function is provided certain key parameters initially like the target user/movie, the pivot table.

6.	The approach our function takes after that is it takes the pivot table and fits it using the Knn model. Our function then tries to find the K nearest values in terms of cosine similarity score.
7.	The function returns the cosine similarity score and the user/movie against which the score has been attained.
8.	Our analysis has shown that user based collaborative filtering has resulted in better cosine similarity scores.
9.	This will be the approach we will consider moving forward with to provide the users with best recommendations.

# Netflix movie recommendation
## Statement of objective 
Aim of the project is to use algorithms that help recommend users with similar movie preferences, movies that users might like and maybe haven’t come across yet. The applications for these kinds of algorithms can be seen across variety of industries. These algorithms help drive some key decisions like which movie user is likely to watch next or in case of ecommerce industry it helps the company predict what products a user is likely to buy next. We will be analyzing the collaborative filtering algorithm which is used in most of the recommendation engines that helps drive these decisions.

## Collaborative filtering algorithm 
The basic approach followed by this algorithm is:
1.	In order to make movie recommendations to a user we need to find group of users who have similar preferences to our target user.
2.	We can achieve our first step by finding ratings of movies that our target user has rated and compare them with users who have given ratings for similar movies.
3.	We can use the cosine similarity metric to determine the similarity between users. Higher the cosine similarity metric better will be the similarity between two users.
4.	Our next step will be to determine the accuracy of our prediction. One way to achieve this accuracy is by calculating the root mean square error where we calculate the difference between values that we have predicted and the actual values(test set), do a square of all the error values we have, take an average of those values and square root it.
5.	The lower the RMSE score, better will be the accuracy of our predictions.

## Dataset details
1.	Our dataset is divided between three text files training, testing and movie titles.
2.	We have close to 3.2 million samples in our training data and close to 100,000 values as part of our testing data.
3.	We have movie id, user id and ratings as features of our training and testing data while our movie titles dataset has movie id, year of release and titles as its features.

## Problem 2 – Analyzing the Netflix data
1.	We start off with doing some basic analysis like finding distinct number of users and movies.
2.	In our next step we take a small sample of our training data and build pivot table where the rows are user id, columns are movie id and values are the ratings for the movies provided by the user. Since one user cannot have ratings for all movies we replace those cells with the value 0 instead of keeping it nan.
3.	 We use a similar approach for movies where we replace the rows with movie id, the column with user id and values with ratings. Similar preprocessing is applied to this approach as well.
4.	We then proceed towards computing the cosine similarity. When we compute cosine similarity between two users we are essentially doing user based collaborative filtering and the one between movies is called as item based collaborative filtering.
5.	Our function is provided certain key parameters initially like the target user/movie, the pivot table.
6.	The approach our function takes after that is it takes the pivot table and fits it using the Knn model. Our function then tries to find the K nearest values in terms of cosine similarity score.
7.	The function returns the cosine similarity score and the user/movie against which the score has been attained.
8.	Our analysis has shown that user based collaborative filtering has resulted in better cosine similarity scores.
9.	This will be the approach we will consider moving forward with to provide the users with best recommendations.

## Problem 3 – Collaborative filtering Implementation
Our next step will be to implement the algorithm on our large training data and check the accuracy of our model on the test data. Let’s analyze the steps taken to implement the algorithm:
1.	Most of the recommendation systems we come across use the collaborative filtering approach. The major reason behind this approach is because most of times we come across data where we receive implicit feedback.
2.	For example in our case if we select a user and analyze his/her ratings we will notice that the user has not provided ratings for all the movies in our dataset, this is because its practically not feasible for a user to watch all the movies and rate them.
3.	In that case we need an algorithm which will handle these missing values with a better approach than the one we used for finding the cosine similarity, i.e. replacing every missing value with a zero. Because a zero rating can be considered as a rating.
4.	This approach will not help us understand if the user has disliked the movie or if he has not watched it yet.
5.	In that case we turn to ALS which stands for alternating least squares. It’s a matrix factorization algorithm. The advantage with ALS is that it works well sparse matrices and has high scalability.
6.	ALS tries to fill in the blank spaces in the sparse matrix by taking values from similar users and predicting the ratings for a user who has not watched a particular movie. This same approach is then implemented for all the users.
7.	The movies with highest predicted ratings are then considered as recommendation to users. 

## Algorithm Implementation
1.	First step towards implementing the model will be to load the libraries. Some of the libraries we will need as part of implementation are the regressor evaluator which will help us measure the performance of our ALS model and import the ALS model itself.
2.	Since our data has been splitted we can proceed towards model creation. 
3.	While creating our ALS model we can fine tune our hyperparameters by specifying the number of max iterations we want the model to have, set our regparam value and provide the user column (userCol), item column (itemCol) and the rating column (ratingCol).
4.	We then fit the model on our training dataset and predict the ratings value against our actual rating values in our test dataset.
5.	The outcome of our predictions can then be analyzed by computing the root mean square error (RMSE) values and the mean square error (MAE) values.
6.	We were able to achieve our best results of MSE score 0.70 and an RMSE score 0.83 by setting the max iterations at 20 and regression parameter at 0.08.
7.	Looking at the predictions given by the model we can see that we are not far off from the actual predictions. 
8.	It is safe to assume that the model can provide pretty accurate recommendations to the users based on their preferences.

## Adding Self rated data to the dataset 
1.	As part of our next approach we were supposed to create dataset containing ratings for movies that we have watched and adding it to the dataset.
2.	After adding our user ratings, we applied the model to our user id and tried to see the recommendations given by our model.
3.	The outcome was pretty good and some of the recommendations given by our model seemed to be of interest.

## Conclusion 
1.	Collaborative filtering is the go-to approach when it comes to recommendation engines as it takes into account several critical factors like implicit feedback which is a real-world scenario. 
2.	ALS algorithm helped us achieve pretty good accuracy with our predictions and can certainly be considered as a good option for movie recommendations. 
3.	Building an accurate recommendation system should certainly be of utmost importance for any organization, as better recommendations result in better user experience



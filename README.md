# Sushi Recommendation System
Implementation of a system that recommends the best sushi options for each customer based on their preferred sushi and the characteristics of those sushi.

## Recommendation Systems
We used two different approaches to create the system to recommend sushis to users. The types of recommendation systems created are as follows:

1. Content Based Recommendation 
2. User Based Recommendation



##  Content Based Recommendation System
The content based recommendation system recommends sushi to the user based on his/her preferences of characteristics of sushi. It takes user id, user preferences data, normalized sushi characteristics data, and number of sushi recommending and returns the top 5 recommended sushi for the user. The number of recommendations is set to 5 as default. It first computes the dot product of user preferences data and normalized sushi characteristics data, which results in creating what each user prefers for each sushi characteristics. We name this user profile data. Then, we compute the cosine similarity between user profile data and sushi characteristics data, which makes it possible to define how close each sushi is to the user's preference. Finally, the function returns with sushi having top 5 highest similarity scores for the designated user. Note that if the designated use id does not exist in the user preferences data, the recommender returns top 5 highest rated sushi.

## User Based Recommendation System
The user based recommendation system recommends sushi based on the preferences of the users who are close to the target users. It takes user id, user preferences data, and number of sushi recommending and returns the top 5 recommended sushi for the user. The number of recommendations is set to 5 as default. It first computes the similarity scores between all users by taking cosine similarity of user preference data. It then finds 5 of the most similar users to the target user and extract their sushi preference data. Their sushi preference data is weighted based on the similarity score to calculate "recommendation scores" for each sushi. It then returns to the sushi having the top 5 highest recommendation scores.

## Evaluation
we computed the precision of each recommendation systems, and compare the result. How we assess the precision of the recommendation systems is computing the hit rate for the each systems and compare. Hit rate is the fraction of rated sushi by the user among the recommended sushi by the system. However, since the score of 1 indicates "dislike" in this data set, I determined the hit rate as the fraction of rated sushi with the score of 2 or above by the user among the recommended sushi by the system.

Procedure of the test is the following:

1.Randomly extract the test set (20 percent of whole user preference data) \\
2.Compute the hit rate of each user and find the average hit rate \\
3.Repeat step 1 and 2 for 5 times and take the average of the hit rate  \\
4.Do the above steps for both of the recommendation systems and compare the scores\\

## Result
Average hit rate of 0.18 and 0.89 are computed for the content based recommendation system and user based recommendation system respectively.

## Source Code
Open the Jupytor Notebook (https://github.com/ssunami/RecommendationSystem/blob/main/Recommendation_System_Project.ipynb) The Notebook should be loadable in browser. This can also be downloaded locally though requires installing Python and Jupyter.


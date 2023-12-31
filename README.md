# Sushi Recommendation System
Implementation of a system that recommends the best sushi options for each customer based on their preferred sushi and the characteristics of those sushi.

## Recommendation Systems
We used two different approaches to create the system to recommend sushis to users. The types of recommendation systems created are as follows:

1. Content Based Recommendation 
2. User Based Recommendation

## Data
We used the following 2 data sets, both of them are from Toshihiro Kamishima’s SUSHI Pref-
erence Data Sets. (https://www.kamishima.net/sushi/#:~:text=The%20SUSHI%20Preference%20Data%20Set,additionally%20by%20a%20ranking%20method)

### sushi.3idata
\item This data contains the characteristics of each 100 kinds of sushi
    \item Each row corresponds to sushi and each column corresponds to characteristic
    \item The characteristics included in the dataset is as below:
\end{itemize}
1. item ID \\
2. name (in Japanese with Roman alphabets) \\
3. style 0:maki 1:otherwise (see Wikipedia) \\
4. major group 0:seafood 1:otherwise 0 corresponds to the minor group nos 0--8. \\
5. minor group 0:aomono (blue-skinned fish) 1:akami (red meat fish) 2:shiromi (white-meat fish) 3:tare (something like baste; for eel or sea eel) 4:clam or shell 5:squid or octopus 6:shrimp or crab 7:roe 8:other seafood 9:egg 10:meat other than fish 11:vegetables \\
6. the heaviness/oiliness in taste, range[0-4] 0:heavy/oily \\
7. how frequently the user eats the SUSHI, range[0-3] 3:frequently eat \\
8. normalized price \\
9. how frequently the SUSHI is sold in sushi shop, range[0-1] 1:the most frequently \\

We call this data set as sushi characteristics data.

### sushi3b.5000.10.score
\begin{itemize}
    \item This data set contains he results of a ranking method questioning 5,000 people about their sushi preferences.
    \item Each row corresponds to a user and each column corresponds to sushi (100 in total).
    \item The evaluation values are on a 5-point scale, from 0 indicating dislike to 4 like the most, and -1 indicating no evaluation.
\end{itemize}

We call this data set as user preferences data in this report.

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


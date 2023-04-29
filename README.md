# Recommendation_System
## 1.	Problem Selection

●	Recommender systems have become a game-changer in the way we search for things that match our interests. These systems utilize information filtering methods to predict the preferences of a user and are widely applied in various domains such as books, news, articles, music, videos, and movies.

●	Movie recommendation systems play an important role in providing users with reliable movie recommendations that align with their preferences. These systems help reduce the time spent searching for favorable movies. With the exponential increase in online data, recommendation systems are becoming increasingly valuable for decision making in various activities of day-to-day life.



## 2.	Data Collection & Description



We are using IMDB data set that contains different files like movie_metadata.csv, keywords.csv, credits.csv, ratings_small.csv.
movie_metada.csv – Contains 45,466 rows & 24 columns with complete information of movies.
Keywords.csv - Contains 46,418 rows & 2 columns with keyword information.
Ratings_small.csv – Contains 29,965 rows and 4 columns of Ratings of users given to the movies.
Credits.csv – Contains 45,476 rows and 3 columns of Cast of movies in movie_data.csv.

## 3.	Data Cleaning & Feature Extraction

•	Filtering movies that have vote count > 50 from movie_md dataset.
movie_md = movie_md[movie_md['vote_count']>=50]
•	Considering 'id','original_title','overview','genres' columns of movie_md dataset.
•	Considering ‘id’,’cast’ of movie_credits dataset.
•	Merging the datasets movie_md, movie_keywords, movie_credits.
•	Performing Data cleaning on ‘keywords’, ‘genres’, ’cast’ columns to extract the keywords, genres and cast from movies.

Null Value Handling:

Replacing the null values in ‘keywords’,’genres’,’cast’ with empty list.

•	Merging the above columns into a single column called ‘tags’ on ‘id’ column of the three data frames.

TF-IDF Vectorizer:
TF-IDF stands for "Term Frequency-Inverse Document Frequency". It is a statistical measure that reflects the importance of a word in a document or a corpus. TF-IDF assigns a weight to each word in a document based on how often it appears in the document and how rare it is across all documents in the corpus. The more frequently a word appears in a document, the higher its TF-IDF score, but the more common a word is across all documents, the lower its TF-IDF score.

The fit_transform function converts the data to sparse matrix of TF-IDF features.

We planned to Use dimensionality reduction techniques that can better work on Uncentered Data and Can capture Nonlinear relations within the data without the requirement of any Data Transformation techniques to be applied before.

## 4.	Dimensionality Reduction

Since the TF-IDF converted matrix consists of a lot many columns we perform Dimensionality Reduction using TruncatedSVD algorithm.

TruncatedSVD:
•	TruncatedSVD is a matrix factorization technique that splits the sparse matrix into smaller matrices. It does not assume any distribution of data like PCA.
•	TruncatedSVD handles outliers effectively when compared to PCA.
•	Since I already Performed PCA in the other Projects, I preferred to explore other Dimensionality Reduction Techniques in Data Mining that can bring better results.








## 5.	Types of Recommendation Systems
 
1.	Content Based Recommender Systems:
Content based systems provide recommendations based on their own user preference and past behavior. Content based systems use the feature items of their own to make decisions.

Advantages:  Can provide recommendations to new user with little or no previous data
Disadvantages: They cannot capture the complex behavior of the users and can sometimes overfit the data.

2.	Collaborative Based Recommender Systems:
Collaborative filtering methods make recommendations based on preferences of similar Users. It takes the idea that users who have similar preferences in the past also have similar preferences in the future.

There are two types of Collaborative systems:


User-Based Collaborative Filtering: This method identifies similar users based on their past behaviors and recommends items that similar users have liked in the past. For example, if two users have both rated a set of movies highly, the system might recommend movies that one user liked to the other user.

Item-Based Collaborative Filtering: Item based collaborative filtering finds similarity between items that user has interacted with. For example, if a user has rated a particular movie highly, the system might recommend other movies that are similar in terms of genre, director, or cast.

## 6.	 Types of Similarity Measures
There are different types of Similarity measures to calculate the distance between different users or items.

1.	Cosine Similarity: This measure calculates the cosine of angle between two vectors. It is frequently used in text-based recommendation systems to calculate similarity between documents based on frequency of words that they share.

2.	Pearson correlation coefficient: This similarity measure is used to calculate the correlation between two variables. Commonly used in collaborative filtering to calculate the similarity between users based on their ratings of items. It measures how much two variables are linearly related to each other.

3.	Euclidean distance: This similarity measure calculates the distance between two vectors in a multidimensional space. It can be used in collaborative filtering to calculate the similarity between users or items based on their ratings. It measures the magnitude of the difference between two vectors.

4.	Jaccard similarity: This similarity measure is commonly used in recommendation systems that deal with binary data, such as whether a user has purchased an item or not. It calculates the similarity between two sets of items by comparing the number of items they have in common.




## 7.	Project Results
Content Based Filtering
In Content Based Recommender Systems we recommended movies to a user based on similarity value of the movies he/she watched. The movies are grouped together based on the different features extracted like the keywords, overview, cast, title. 

The output of content-based recommender in our project, displays the top five movies that can be suggested to a user based on the movie that he has watched.

Collaborative Based Filtering

We leverage the library Surprise and SVD (Singular Value Decomposition) to perform collaborative filtering which splits the sparse matrix into three other matrices.

In Collaborative filtering we predict the rating of a movie by a user based on the ratings of similar users. We utilize Rating.csv Dataset that contains ratings of movies given by different users.

Item Based and User based methods were implemented using KNNBasic Algorithm which is a collaborative filtering algorithm that uses similarity measure between pair of users or items.


For the User_id= 3 and movid_id= 2959 the rating predictions are 
Type of Algorithm	Actual Rating	Predicted Rating
Collaborative (SVD)	5.0	4.197
Item Based (KNN Basic)	5.0	3.577
User Based (KNN Basic)	5.0	4.524

We Observe that Prediction of Rating based on the similar Users rating is almost like the actual rating of the user. For this example, User Based Filtering predicted more accurate rating than the rest. 



## 8. Impact of the Project
The following are the Impact that Recommendation Projects Can have.

1.	Increased Revenue: Through these techniques of recommendations the movie companies can increase their revenue by allowing users to watch more similar content.

2.	Customer Satisfaction: The idea of bringing together all the similar movies that a user has watched will help to increase customer satisfaction, which helps to increase repeated business.

3.	Improved Efficiency: Automated movie recommendation systems can save time of time and resources of streaming services by reducing the need for manual analysis.




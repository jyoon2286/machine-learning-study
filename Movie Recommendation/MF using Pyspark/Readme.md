### Abstract 
Among the recommendation algorithms, one of the most widely used algorithms is by far Collaborative Filtering (CF). Among them, the one with the highest performance as a single algorithm is the Matrix Factorization (MF) algorithm, which is a model-based CF. The MF recommendation model can be viewed as a process of filling in the missing data in the sparse user-item matrix through the model. In this paper, we study how we can split the rating matrix into user and item matrices and explain how it can train the objective function to minimize error in the Latent Factor matrix of users and items.

### INTRODUCTION
The recommendation system for movies, TV shows, etc. helps the show selection by predicting the audience's preference based on the audience's past behavior or their reviews. According to an interview with The New York Times, Neal Mohan, YouTube's Chief Product Officer, said, '70% of YouTube users' viewing time is the result of the recommendation algorithm, and the introduction of the algorithm increases the total video viewing time by more than 20 times than before. Netflix collects the data based on viewers’ preferences and uses the same to help you find content which you will be interested in. Netflix held a contest that award a prize of $1 million to the team that was able to improve their recommendation system back in 20061. Disney plus, Apple Tv, Hulu, etc., all of the over-the-top (OTT) media services put much effort into providing a better recommendation system to the customers. Of course, dealing with human tastes and providing the right preferences is a challenging problem. There were many different algorithms researched and developed for the recommendation system, and the OTT companies like YouTube, Netflix, etc. have continued to seek the state-of-art algorithm. <p />
This paper explores to find out how does the recommended system work and what is the logic behind the system. In the real-world problem, hundreds of million data would be used to build the model and recommendation system, but one million datasets is used for this paper because of the limit of handling big data.
The dataset is a movie dataset from MovieLens at Grouplens.org, which contains the id of users and movie, and. The dataset contains the 20 variables which are the information of the 1 million ratings from 6000 users on 4000 movies, released in 2/2003.<p />
Recommendation systems are largely divided into Collaborative Filtering (CF) and Content-Based Filtering (CBF). The CBF configures each profile database for users and items. In the case of an item, for example, if it is a movie, it can contain the actors, genre, year of production, etc. The CF identifies the relationship between existing users and items and makes recommendations between new users and items. Unlike the CBF, explicit data is used, and experience data such as the rating of movies are mainly used. In this case, the performance of the CBF model is better, but the CF model works better for most cases.<p />
This paper seeks to understand the CF movie recommendation system using the Matrix Factorization (MF) which is the latent factor model, the average of ratings of movies and correction of bias. The Latent Factor model learns the relationship between the user and the item as each of the Latent Vector. The interaction between the item and the user is calculated as the value of the inner product between these two vectors. That is, it expresses the user's interest in the item. Since the data on item-user interaction is sparse, we use the regularization method to learn to reduce the error of the model. For that method, the Stochastic Gradient Descent (SGD) or the Alternating Least Squares (ALS) are used.<p />
This paper seeks to understand the CF movie recommendation system using the Matrix Factorization (MF) which is the latent factor model, the average of ratings of movies, and correction of bias. The Latent Factor model learns the relationship between the user and the item as each of the Latent Vector. The interaction between the item and the user is calculated as the value of the inner product between these two vectors. That is, it expresses the user's interest in the item. Since the data on item-user interaction is sparse, we use the regularization method to learn to reduce the error of the model. For the different methods of gradient descent and optimization, the Stochastic Gradient Descent (SGD) or the Alternating Least Squares (ALS) are used, but the study is more focused on the SGD than the ALS methods. This paper also suggests how can the CF recommendation system run in the big data environment using the Pyspark. To deal with large datasets, the three methods of Pyspark are used. The first method is that it reads the dataset
with Pyspark DataFrame and creates Scipy's sparse matrix to feed the matrix to the MF model. Secondly, Pyspark's MLlib is used to read data and build a model using MLlib’s ALS package. Finally, Keras is used to build the MF recommendation model. Then, the performance of the recommendation system is evaluated using the Root-Mean-Square-Error (RMSE) to see which methods perform better than other.<p />
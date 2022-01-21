# A graph-based recommendation system

Recommender systems are really well spread nowadays in web services such as Youtube, Amazon, Netflix and others. They are used for suggesting relatives items to users, thus leading industries to have more incomes and in general to stand out from the competitors when the algorithms applied are efficient. Here the project is based on using graph features and a GNN to implement a recommender system.  

For a detailed description of the project look at **report** folder with respective pdf file.  
On the contrary, for a brief summary of the results obtained read bellow.  

## Dataset

The [dataset](https://www.kaggle.com/CooperUnion/anime-recommendations-database) contains information regarding the preferences of users about some anime.
The anime information are: unique id identifying the item, full name, genre (separated by comas for more than one), type, episodes, rating and members (number of community members that are in this anime's "group"). For the ratings the information are: user id (non-identifiable, randomly generated user id), the anime id (the anime that this user has rated) and a rating score in a range from 0 to 10, also if the user watched it but didn't assign a rating then the score is -1.  

<img src="https://github.com/chguizz/graph_based_recommendation_system/blob/main/figures/anime_genres_popularity.jpg" style="float:left">

Therefore a first dataset exploration is done on notebook [DataExploration.ipynb](https://github.com/chguizz/graph_based_recommendation_system/blob/main/DataExploration.ipynb), where thanks all information available a graph is build. A small example of some nodes is below  

<img src="https://github.com/chguizz/graph_based_recommendation_system/blob/main/figures/graph_example.jpg" height="400" style="float:left">

## Algorithm

To solve the cold-start problem when new users or items enter the system and have no or very few interactions, the strategies are:
* when a new user enters the system, the top K items proposed are found thanks closeness-centrality (where the graph is considered both with and without weights) or degree-centrality metric;
* when a new item enters the system is proposed to the most active users. Those are found using closeness-centrality metric (where the graph is considered both with and without weights) or degree-centrality metric.  

Refer to [GraphCentralities.ipynb](https://github.com/chguizz/graph_based_recommendation_system/blob/main/GraphCentralities.ipynb)  

<img src="https://github.com/chguizz/graph_based_recommendation_system/blob/main/figures/RBO_heatmap_anime.png">  

<img src="https://github.com/chguizz/graph_based_recommendation_system/blob/main/figures/RBO_heatmap_users.png">

When the user has reached a minimum number of user-item interactions, then the system can use these information to suggest the most likely anime to be watched (or a set of possible proposals). This is done thanks a [GNN](https://github.com/chguizz/graph_based_recommendation_system/blob/main/GNN.ipynb), whose performances are compared with a base-line method and also with [Node2Vec](https://github.com/chguizz/graph_based_recommendation_system/blob/main/Node2vec.ipynb) algorithm.

<img src="https://github.com/chguizz/graph_based_recommendation_system/blob/main/figures/ranking_distributions_final.jpg">

For the creation of this last image refer to [VisualisationLinkP.ipynb](https://github.com/chguizz/graph_based_recommendation_system/blob/main/VisualisationLinkP.ipynb)

For checking all hyper-paramters tried for the GNN, look at [hyper-parameters.xlsx](https://github.com/chguizz/graph_based_recommendation_system/blob/main/data/hyper-parameters.xlsx)

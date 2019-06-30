# Recommendation System

A recommender system or a recommendation system is a subclass of information filtering system that seeks to predict the "rating" or "preference" a user would give to an item. They are primarily used in commercial applications. A recommendation engine filters the data using different algorithms and recommends the most relevant items to users. It first captures the past behavior of a customer and based on that, recommends products which the users might be likely to buy.

Recommender systems are utilized in a variety of areas, and are most commonly recognized as playlist generators for video and music services like Netflix, YouTube and Spotify, product recommenders for services such as Amazon, or content recommenders for social media platforms such as Facebook and Twitter.

# Types of Recommendation Engine

Recommendation systems use a number of different technologies. We can classify these systems into two broad groups
1. Content Based Recommendations
2. Collaborative Filtering


![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/Types.png?raw=true "Types of Recommendation Engine")

## 1. Content Based Recommendations :

Content-based filtering methods are based on a description of the item and a profile of the user’s preferences. These methods are best suited to situations where there is known data on an item (name, location, description, etc.), but not on the user. Content-based recommenders treat recommendation as a user-specific classification problem and learn a classifier for the user's likes and dislikes based on product features.
 
 ### Properties :
 * Idea: If you like an item then you will also like a "similar" item
 * Based on similarity of the items being recommended
 * It generally works well when its easy to determine the context/properties of each item. For instance when we are recommending the same kind of item like a movie recommendation or song recommendation
 
 ### Pros :
 * No need for data on other users
 * Able to recommend to users with unique tastes
 * Able to recommend new and unpopular items
 * Explanations for recommended items - features that caused the item to be recommended
 
 ### Cons :
 * Finding the appropriate features is hard
   * Eg: images, movies, music
 * Overspecialization
   * Never recommends items outside user's content profile
   * People might have multiple interests
   * Unable to exploit quality judgement of other users
 * Cold-start problem for new users
   * How to build a user profile ?
 
## 2. Collaborative Filtering :

Collaborative filtering is based on the assumption that people who agreed in the past will agree in the future, and that they will like similar kinds of items as they liked in the past. The system generates recommendations using only information about rating profiles for different users or items.

### Properties :
* Idea: If a person A likes item 1, 2, 3 and B like 2,3,4 then they have similar interests and A should like item 4 and B should like item 1.
* This algorithm is entirely based on the past behavior and not on the context. This makes it one of the most commonly used algorithm as it is not dependent on any additional information.
* For instance: product recommendations by e-commerce player like Amazon and merchant recommendations by banks like American Express.
* Further, there are several types of collaborative filtering algorithms :
  * **User-User Collaborative filtering:** Here we find look alike customers (based on similarity) and offer products which first customer’s look alike has chosen in past. This algorithm is very effective but takes a lot of time and resources. It requires to compute every customer pair information which takes time. Therefore, for big base platforms, this algorithm is hard to implement without a very strong parallelizable system.
  * **Item-Item Collaborative filtering:** It is quite similar to previous algorithm, but instead of finding customer look alike, we try finding item look alike. Once we have item look alike matrix, we can easily recommend alike items to customer who have purchased any item from the store. This algorithm is far less resource consuming than user-user collaborative filtering. Hence, for a new customer the algorithm takes far lesser time than user-user collaborate as we don’t need all similarity scores between customers. And with fixed number of products, product-product look alike matrix is fixed over time.

 ### Pros :
 * Works for any kind of item
   * No feature selection needed
 
 ### Cons :
 * Cold start problem
   * Need enough users in the system to find a match
 * Sparsity
   * The user/ratings matrix is sparse
   * Hard to find users that have rated the same items
 * First rater problem
   * Cannot recommend an unrated item - New items, Esoteric items
 * Popularity bias
   * Tends to recommend popular items
   
 # Case Study : How to develop a recommender systems which can recommend popular item as well as new/esoteric items
 
 Assume the case where a customer X logs into our e-commerce platform to buy himself a t-shirt. He has made multiple purchases on the same website before as well. He is a guy who prefers graphic t-shirts which can also be seen in his buying behaviour on the platform. Below are few products from his previous purchase through our platform.
 
 ![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/FB-1.png?raw=true "Purchase History")

Now he is back to our e-commerce platform to buy a few more t-shirts. His preference might or might not be same as before. He either buy a popular product which is currently in trend or he might stick to his original preference. Either ways, lets assume below is the first page to which he was redirected after applying the filters : Type - Poleras, Fit - Classic, Size - L.

 ![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/FB-2.PNG?raw=true "Home Page")
 
As we can see, there are 282 products which matches his filters. The landing page consist of 32 products and top 8 are visible in the above screenshot. But none of these matches Mr. X's preference. Lets say he was not able to find anything that matches his preference in the first page. He jumps over to the next page, again nothing that matches his preference. He had to look over 225 items before he finally finds the t-shirts that he was looking for on the 8th page. This can result in unhappy customer and thereby leads to customer attrition.

 ![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/FB-3.PNG?raw=true "8th Page")
 
 **What do you thing would have caused this issue. What could have been done to prevent it ?**
 
 ## Reasons behind current recommendations :
The e-commerce platform generates the landing page based on recommendation engine. Following can be few reasons why the landing page was populated as we see in the snapshot.
 1. Recommender system tried to push offer products ahead of others
 2. Recommender system gave priority to popular products
 
 On the flip side, the relevant results were pushed to 8th page. It can be due to
 1. Recommender system ignored user's historical preferences.
 2. The user preferred item was new, hence not much information.
 
 ## Possible solutions :
 **1. Redesign the system to use content based recommendation :**
 
 This might solve the problem faced by Mr. X. He will be redirected to a custom tailored landing page based on his past behaviour. But this will cause a big problem for majority of users who are looking for latest trends.AFter a point, Mr. X also might get bored seeing similar t-shirts to the ones he already has. Hence this is not a correct solution.
 
 **2. Redesign the system to use hybrid recommendation system :**
 
 Hybrid recommendation system will use both collaborative filtering and content based recommendation in such a way that cons of one system is negated by the other. Using this, we will be able to provide relevant recommendations by taking into account individual preferences as well as latest trends.
 
## Solution - Hybrid Recommender System :

Hybrid Recommender System combines collaborative filtering, content-based filtering, and other approaches . Hybrid approaches can be implemented in several ways: by making content-based and collaborative-based predictions separately and then combining them; by adding content-based capabilities to a collaborative-based approach (and vice versa); or by unifying the approaches into one model. Several studies that empirically compare the performance of the hybrid with the pure collaborative and content-based methods and demonstrated that the hybrid methods can provide more accurate recommendations than pure approaches. These methods can also be used to overcome some of the common problems in recommender systems such as cold start and the sparsity problem, as well as the knowledge engineering bottleneck in knowledge-based approaches.

![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/Hybrid%20Recommender%20System.jpeg?raw=true "Hybrid")


Some hybridization techniques include:
1. **Weighted :** Combining the score of different recommendation components numerically.
2. **Switching :** Choosing among recommendation components and applying the selected one.
3. **Mixed :** Recommendations from different recommenders are presented together to give the recommendation.
4. **Feature Combination :** Features derived from different knowledge sources are combined together and given to a single recommendation algorithm.
5. **Feature Augmentation :** Computing a feature or set of features, which is then part of the input to the next technique.
6. **Cascade :** Recommenders are given strict priority, with the lower priority ones breaking ties in the scoring of the higher ones.
7. **Meta-level :** One recommendation technique is applied and produces some sort of model, which is then the input used by the next technique

## Collaborative Filtering for E-Commerce Platform

We create the utility matrix between t-shirts and users where each cell signifies whether the given user has purchased the given t-shirt. Based on this utility matrix we can calculate any similarity measure which tells us how two similar a pair of t-shirts are based on the purchase behaviour of all the users on our platform. This generates an item-item similarity matrix which shows the similarity measure between any two t-shirts.

![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/CF.png?raw=true "Item-Item CF")

Based on the above similarity matrix, we can rank other products with respect to the product purchased by our user Mr. X and the rank matrix will be as follows. Based on this, the landing page of user was designed by picking top items similar to the items already bought by him.

![alt+text](https://github.com/rinazbelhaj/Data-Science/blob/master/Images/Similar%20Item.png?raw=true "Similarity Matrix")

## Content Based Filtering for E-Commerce Platform

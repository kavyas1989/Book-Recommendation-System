# Book-Recommendation-System

## Problem Description 

In this ever expanding free and competitive market and rise of internet which has spread the access to every individual to create something and bceome producers and gain benefit from it,instead of earlier time where some big market forces where producers and gaining huge profits from thier monopoly  has raised hug benefit for producers as well as consumers as now consumers also have a variety of option to select what to consume. But this has created a situation where customers can get into confusion of what to choose and there is need to solve this problem by producers to gain maximum benefit from its customers and product and to ensure that customer is getting enough satisfaction.

Recommendation System is one of the way to deal with this kind of problem. Recommendation system is a machine learning which help to suggest best product to  users based on many factors like customer features. We can see its application in  hundred of different services - ranging from online shopping to music to movies. Recommendeation systems held very bihg importance in some industries like Spotify, Amazona, Netflix ,etc. as they can help to generate a huge amount of income for these companies when they are efficient and provide a way to do product differentiation.

In this project my main objective is to create book recommendation systems for users on various approaches to efficiently predict what books customers want to buy and provide maximum customer satisfaction and experience which will help us to generate more revenue , profit, and gain high amount of customers lifetime value(revenue which we can users during the period he is our customer) .

## Data Description 

In our Book-Crossing dataset, which consists of 3 files. They are:

### Users
-User-ID: A unique identification number for each user
- Location:It contains city,state and country to which the user belongs ,separated by commas
- Age:The age of the user

### Books

- ISBN:International Standard Book Number unique to each edition of the book
- Book-Title:Title of the book
- Book-Author:Author of the book(incase of several authors only the first is provided)
- Year-of-Publication:The year in which the particular edition of the book was published
- Publisher:Name of the Book Publishing company
- Image-URL-S: URL link to a small version of the book cover displayed on the Amazon website
- Image-URL-M: URL link to Medium version image of the book cover displayed on the Amazon website
- Image-URL-L: URL link to Large sized image of the book cover displayed on the Amazon website
- Ratings

### Ratings 

- User-ID:as mentioned above
- ISBN:as mentioned above
- Book-Rating: The rating given by the user (identified by User-ID) for the book (identified by ISBN). It is either explicit,expressed on a scale from 1-10 (higher values denoting higher appreciation), or implicit,expressed by 0.

## Data preprocessing

### Books

- Removed the columns Image-URL-S, Image-URL-M and Image-URL-L which do not provide any information for our data analysis.
- Our Books dataset contains 2 null values in Publisher column feature and one 1 null value in Book Author and we treated them by fillin right value in them with the help of internet search.
- The entries in the columns like Book-Title, Book-Author, Year-Of-Publication, and Publisher who have incorrect entries were fixed, and those entries were replaced with the correct values found through an internet search.
- Duplicates data samples row removal.

### Users 

- The null values and the invalid Age column entries were imputed with values from a normal distribution whose mean and standard deviation matched those of the valid Age column entries.
- The outliers values of age treated by replacing them with median value of age..
- Missing values of Age are treated by replacing them with mean value of age.
- Extracted the country name from the ‘Location’ column and corrected the misspelled country names and convert it to uppercase.
- Checked for duplicates

### Rating

- There are no null and duplicate values for rating fetaure.
- Created two distinct dataframes for the entries with implicit ratings (Book-Rating=0) and explicit ratings (Book-Rating!=0).

At the end step after preprocessing all of our database , we are going to merge them.

## Extrapolarotary Data Analysis

- The book which has been rated by most number of users is 'The Lovely Bones' followed by 'Wild Animus' and 'The Vinci Code'
- Stephen King has received maximum number of rating by the users. It seems he is more popular among readers followed by Nora Roberts and John Grisham.
- In Publication house,  Ballantine Books received maximum attention by the users followed by Rocket and Barkley Publishing.
-  Most of the readers are from the United States , followed by canada, germany, and UK.
- Higher Ratings are more common amongst users and ratings 8 has been given highest number of times

# Recommendation Model Building

## Simple Popularity Based Recommendation Sysytem

-This recommendation system recommend 10 most popular books in market as a recommendation to read for users.
-On basis of this system, we cam obeserve that books like Lonely bones , Wild Animus , and The Da vinci Code should be our topmost recommendation.

## Country-based book recommendation

- This recommendation system will be based on most popular books in the country of user who we want to buy books.
- Let's take example of our user is from Germany, and we want to recommend him most popular book in his region, them ooks like Russendisko , Der Vorleser, and Illuminati are most recommended books for the user who belong to Germany.

## Weighted average rating method

- In this method, we give average rating to each user and recommend books on the basis of it, and the formula for average weight to each is 

                                                       W = (Rv + Cm)/(v + m)
where ,W= Weighted Rating ,
R = Average of the Books rating , 
v = No of people who have rated the books(number of votes) , 
m = minimum no of votes to be listed , 
C = the mean rating across all the books .

- The average rating of all the books is 7.521927888218318 and the minimum number of votes required by the books to be listed is 4 .
- The book 'Harry Potter and the Chamber of Secrets Postcard Book' seems to have best book on the basis of this crietria.

## Collaborative Filtering

- This approach investigates the user’s behaviors, interests, and searches for similar users. It recommends items to users based on the ratings of similar users on various items and by predicting the missing ratings of the items

### Memory Based Approach
### USER BASED FILTERING

- In this approach, our focus will be on user mainly, and will recommend on fetaures related to them.
-74513 users are thoes who have rated books. Rest have never rated on any single book. This was filtering based on user

### Item Basd Filtering

-This approach focus doing fltering and recommendation on the basis of item features.
- Here, we try to use cosine similarity matrices.
- Books similar to '1984' are Brave New World', "The Hitchhiker's Guide to the Galaxy",'The Catcher in the Rye' .

## Model Based colloborative Filterig

- Model based approach involves building machine learning algorithms to predict user's ratings. They involve dimensionality reduction methods that reduce high dimensional matrix containing abundant number of missing values with a much smaller matrix in lower-dimensional space.

- Here, we can use method of Singular Value Decomposition(SVD) and Used KNN algorithm for memory based CF.

- On evaluating our SVD model with help of matrices like we got scores like Recall@5 of 30% and
  Recall@10 of 41%.
 




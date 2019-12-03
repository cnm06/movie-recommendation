# MOVIE RECOMMENDATION ENGINE

Based on database collected from IMDb (CSV file attached in the repository), this CONTENT BASED RECOMMENDATION SYSTEM takes in a movie that a user currently likes, as input. Then it analyzes the contents (storyline, genre, cast, director etc.) of the movie to find out other movies which have similar content. It ranks similar movies according to their similarity scores (Cosine similarity) and recommends the top 50 most relevant movies to the user.




# FUNCTIONING EXPLAINED STEP-WISE :


## 1. IMPORTING DATA -
After downloading the dataset, we import all the required libraries and then read the csv file using read_csv() method.

## 2. DATA ORGANISATION -
The dataset has many extra columns of information about a movie which are irrelevent in determining Cosine Similarity. So, we choose particular columns - keywords, cast, genres and director to use as our "feature set" . Then create a function for combining the values of these columns into a single string. After calling the function, we feed these strings to a CountVectorizer() object for getting the count matrix.

## 3. COSINE SIMILARITY / SIMILARITY SCORE -
This method of quantifying similarity between 2 strings visualises strings as vectors the coordinates (represented by the Count Matrix mentioned above) of which are decided by the feature set. The Cosine of angle between 2 vectors then represents a measure of similarity (Parrelel/identical vectors will have a 0 degree angle giving maximum or complete similarity = 1). So it can be concluded that larger value of Cosine denotes more similarity.  

## 4. RESULT -
User enters the title of the movie that he/she currently likes and we find the index (as in the database) of that movie. Now we access the row corresponding to this movie in the similarity matrix so as to get the similarity scores of all other movies w.r.t the current movie. Then enumerate through all the similarity scores of that movie to make a tuple of movie index and similarity score. 

Here, each item is in the form- (movie index, similarity score).

The list is then sorted according to similarity scores in descending order. Since the most similar movie to a given movie will be itself, we discard the first element after sorting the list and print next top 50 entries from sorted_similar_movies list.

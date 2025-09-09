**Movie Recommender System**
This project is a content-based movie recommender system that suggests movies similar to a user's choice. The recommendation is based on movie metadata like genres, keywords, cast, and crew. The core idea is to create a "tag" for each movie by combining these features and then find the most similar movies using vectorization and cosine similarity.

**How It Works**
The system follows these steps:
1)Data Loading and Merging: It starts by loading two datasets: tmdb_5000_movies.csv and tmdb_5000_credits.csv. These are then merged into a single dataframe based on the movie ID.

2)Data Cleaning and Preprocessing:
Irrelevant columns are dropped, keeping essential features like genres, keywords, title, overview, cast, and crew.
The JSON-like string format of genres, keywords, cast, and crew is parsed to extract the relevant names (e.g., genre names, actor names).
For the cast, only the top 3 actors are considered. For the crew, only the director's name is extracted.

3)Feature Engineering:
A consolidated tags column is created by combining the preprocessed text from overview, genres, keywords, cast, and crew.
Spaces are removed from multi-word strings (like "Science Fiction" becoming "ScienceFiction") to treat them as single entities.

4)Text Vectorization:
The tags for all movies are vectorized using CountVectorizer from scikit-learn. This converts the text data into a numerical format, creating a vector for each movie based on the 5000 most frequent words (stop words are removed).

5)Similarity Calculation:
The cosine similarity between all movie vectors is calculated. This results in a similarity matrix where each movie has a similarity score with every other movie.

6)Recommendation Function:
A function recommend(movie) takes a movie title as input.
It finds the similarity scores for that movie from the matrix.
It then returns the top 5 movies with the highest similarity scores.

**How to Use**
1)Prerequisites: Make sure you have Python and the following libraries installed:
NumPy
Pandas
scikit-learn

You can install them using pip:
pip install numpy 
pandas scikit-learn

2)Get the Data: You will need the tmdb_5000_movies.csv and tmdb_5000_credits.csv files in the same directory as the notebook or script.

3)Run the Code: Execute the cells in the Jupyter Notebook (recommender.ipynb) sequentially.

4)Get Recommendations: Use the recommend() function to get movie suggestions. For example:
recommend('The Dark Knight Rises')
This will output a list of 5 movies that are most similar to "The Dark Knight Rises".

**Example Output**
Top 5 recommendations for 'The Avengers':
Avengers: Age of Ultron
Captain America: Civil War
Iron Man 3
Captain America: The First Avenger
Iron Man

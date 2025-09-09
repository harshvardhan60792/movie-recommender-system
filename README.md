# Movie Recommender System

This project is a content-based movie recommender system that suggests movies similar to a user's choice. The recommendation is based on movie metadata like genres, keywords, cast, and crew. The core idea is to create a "tag" for each movie by combining these features and then find the most similar movies using vectorization and cosine similarity.

## How It Works

1) **Data Loading and Merging:**  
Load two datasets: `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`. Merge them into a single dataframe based on movie ID.

2) **Data Cleaning and Preprocessing:**  
Drop irrelevant columns and keep essential features like genres, keywords, title, overview, cast, and crew.  
Parse JSON-like strings of genres, keywords, cast, and crew to extract relevant names.  
Consider only top 3 actors for cast and only the director for crew.

3) **Feature Engineering:**  
Create a consolidated `tags` column by combining the preprocessed text from overview, genres, keywords, cast, and crew.  
Remove spaces from multi-word strings (e.g., "Science Fiction" → "ScienceFiction") to treat them as single entities.

4) **Text Vectorization:**  
Use `CountVectorizer` from scikit-learn to convert tags into numerical vectors based on the 5000 most frequent words, removing stop words.

5) **Similarity Calculation:**  
Compute cosine similarity between all movie vectors to get a similarity matrix. Each movie has a similarity score with every other movie.

6) **Recommendation Function:**  
The `recommend(movie)` function takes a movie title as input, finds its similarity scores, and returns the top 5 most similar movies.

## How to Use

**Prerequisites:** Python with NumPy, Pandas, and scikit-learn installed.  
Install using:  
pip install numpy pandas scikit-learn


**Get the Data:**  
Download `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` from [Kaggle TMDB Movie Metadata](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) and place them in the same directory as the notebook or script.

**Run the Code:**  
Open `recommender.ipynb` and execute the cells sequentially.

**Get Recommendations:**  
Use the `recommend()` function to get movie suggestions. For example:  recommend('The Dark Knight Rises')

This will output the top 5 movies most similar to "The Dark Knight Rises".

## Example Output

Top 5 recommendations for 'The Avengers':  
- Avengers: Age of Ultron  
- Captain America: Civil War  
- Iron Man 3  
- Captain America: The First Avenger  
- Iron Man

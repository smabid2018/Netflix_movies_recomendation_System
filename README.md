# Netflix Movies Recommendation System
BY Sheikh Md Abid

## Project Workflow

### 1. Importing Libraries
The necessary Python libraries such as `numpy`, `pandas`, and `ast` are imported to handle data processing and manipulation.

### 2. Loading the Datasets
The datasets `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` are loaded using Pandas. These datasets contain information about movies, including titles, genres, cast, crew, and more, which will be used to build the recommendation system.

### 3. Merging Datasets
The `movies` and `credits` datasets are merged on the movie title to combine relevant information from both datasets into a single dataframe. This step integrates movie metadata with corresponding cast and crew details, enabling a more comprehensive analysis.

### 4. Data Preprocessing
The merged dataset is reduced to the most relevant columns for building the recommendation system. The selected columns include `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, and `crew`. This reduction focuses the analysis on the essential features needed for content-based recommendations.

### 5. Handling Missing Data
To ensure clean and consistent data, rows with missing values in the selected columns are dropped. This step is crucial for maintaining the integrity of the dataset, as missing values could affect the accuracy of the recommendation system.

### 6. Data Transformation
The columns `genres`, `keywords`, `cast`, and `crew` contain nested JSON-like structures, which need to be converted into lists of strings for further processing. This transformation is done using the `ast.literal_eval()` function, along with custom helper functions, to extract the relevant information from these nested structures.

### 7. Processing Cast and Crew
The `cast` and `crew` columns are refined to focus on the most relevant information:

- **Cast:** The `cast` column is limited to the top 3 actors, as they typically have the most significant impact on a movie's identity and appeal.
- **Crew:** The `crew` column is filtered to retain only the director's name, as the director plays a crucial role in shaping the movie's vision and style.

### 8. Removing Spaces in Tags
To ensure that the vectorization process works effectively, spaces in the tags (such as actor names, genres, keywords, etc.) are removed. This step prevents issues where multi-word tags might be treated as separate tokens, which could dilute their significance in the recommendation system.

### 9. Creating the Tags Column
A new column called `tags` is created by combining the content from the `overview`, `genres`, `keywords`, `cast`, and `crew` columns into a single string. This consolidated column serves as the primary input for generating movie recommendations, as it encapsulates all the key descriptive information about each movie.

### 10. Vectorization
The `tags` column is vectorized using `CountVectorizer` from Scikit-Learn. This process converts the text data in the `tags` column into a numerical format that can be used for similarity calculations. The `CountVectorizer` is configured to handle a maximum of 5000 features and remove English stop words, which helps in focusing on the most meaningful terms.

### 11. Calculating Similarity
Cosine similarity is used to measure the similarity between movies based on their vectorized tags. This technique calculates how similar two vectors are by determining the cosine of the angle between them, providing a measure of how closely related two movies are in terms of their tags.

### 12. Building the Recommendation Function
The `recommend()` function is designed to take a movie title as input and return a list of the top 5 similar movies based on content similarity. This function uses the similarity matrix to find movies that are most similar to the input movie.

### 13. Example Usage
To get movie recommendations using the `recommend()` function, simply provide the title of a movie as input. For example, to find movies similar to "Avatar".

### Conclusion
This Netflix Movies Recommendation System effectively identifies similar movies based on content. By leveraging cosine similarity, the system ensures that the recommended movies closely match the input movie in terms of genres, keywords, cast, and crew. This approach provides users with personalized and relevant movie suggestions, enhancing their viewing experience.







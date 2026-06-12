# Content-Based Movie Recommendation System

A simple yet effective **Content-Based Filtering** recommendation system built with Python and Pandas. This project recommends movies to users based on their past preferences by analyzing movie genres and creating personalized user profiles.

![Recommendation System](https://img.shields.io/badge/Recommendation-System-blue.svg) [![Python](https://img.shields.io/badge/Python-3.6%2B-blue)](https://www.python.org/) [![Pandas](https://img.shields.io/badge/Pandas-Latest-orange)](https://pandas.pydata.org/)

##  Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Example Output](#example-output)
- [Project Structure](#project-structure)
- [Limitations & Future Improvements](#limitations--future-improvements)
- [Contributing](#contributing)
- [License](#license)

## Overview

Recommendation systems help users discover relevant items. This notebook implements a **Content-Based** recommender that suggests movies similar to those a user has liked in the past, using genre information as features.

The system:
- Processes the MovieLens "ml-latest-small" dataset
- Cleans and prepares movie titles, years, and genres
- One-hot encodes genres
- Builds a user profile from ratings
- Recommends top movies matching the user's preferences

## Features

- **Data Cleaning**: Extracts years from titles, handles missing values, optimizes memory usage
- **Genre Processing**: Splits and one-hot encodes movie genres
- **User Profiling**: Creates weighted preference vectors based on user ratings
- **Recommendations**: Generates personalized movie suggestions using dot product similarity
- **Memory Optimization**: Converts data types for efficiency

## Dataset

Uses the [MovieLens Small Latest Dataset](https://grouplens.org/datasets/movielens/latest/) containing:
- **movies.csv**: 9,742 movies with titles, genres, and extracted years
- **ratings.csv**: 100,836 ratings from users

Data is loaded directly from raw GitHub URLs in the notebook.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/content-based-movie-recommender.git
   cd content-based-movie-recommender
   ```

2. Install dependencies:
   ```bash
   pip install pandas
   ```

3. Open the Jupyter Notebook:
   ```bash
   jupyter notebook Content_Based_Filtering.ipynb
   ```

## Usage

1. Run all cells in the notebook sequentially.
2. Modify the `Lawrence_movie_ratings` list to test with different user preferences.
3. The system will output the **Top 20 recommended movies** based on the input ratings.

**Example User Input** (as shown in the notebook):
```python
Lawrence_movie_ratings = [
    {'title':'Predator', 'rating':4.9},
    {'title':'Final Destination', 'rating':4.9},
    # ... more movies
]
```

## How It Works

1. **Data Preparation**
   - Load and clean movies & ratings data
   - Extract year from title
   - Split genres into lists and one-hot encode them

2. **User Profile Creation**
   - Match user-rated movies with genre vectors
   - Compute weighted genre preferences using dot product

3. **Recommendation Generation**
   - Calculate similarity scores for all movies
   - Sort by score and return top recommendations

The core recommendation logic uses matrix operations:
```python
recommendation_table_df = (movies_with_genres.dot(Lawrence_profile)) / Lawrence_profile.sum()
```

## Example Output

**Top Recommendations for "Lawrence"** (who prefers Action, Thriller, Horror):

| Rank | Movie Title | Genres | Year |
|------|-------------|--------|------|
| 1 | Rubber | Action, Adventure, Comedy... | 2010 |
| 2 | Pulse | Action, Drama, Fantasy... | 2006 |
| ... | ... | ... | ... |

The system successfully recommends movies heavy in **Action, Thriller, Horror, and Sci-Fi** genres.

## Project Structure

```
content-based-movie-recommender/
├── README.md
├── Content_Based_Filtering.ipynb     # Main Jupyter Notebook
├── movies.csv                        # (Optional local copy)
├── ratings.csv                       # (Optional local copy)
└── requirements.txt
```

## Limitations & Future Improvements

- **Cold Start Problem**: Requires some initial ratings from the user
- **Limited Features**: Only uses genres (could incorporate tags, directors, actors)
- **Scalability**: Works well for small datasets; consider TF-IDF or embeddings for larger ones
- **Future Enhancements**:
  - Hybrid recommendation (Content + Collaborative)
  - Web interface (Streamlit/Flask)
  - Advanced NLP on plot summaries
  - Deployment as API

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.

1. Fork the project
2. Create your feature branch
3. Commit your changes
4. Push and open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


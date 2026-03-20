# 🎬 Movie Recommender System

A content-based movie recommender system built with TF-IDF vectorization, served via FastAPI and a Streamlit frontend with live TMDB data.

## How it works

The model uses TF-IDF (Term Frequency-Inverse Document Frequency) on movie metadata (genres, overview, cast) to compute cosine similarity between movies. Given a movie title, it returns the most similar movies from the dataset.

The FastAPI backend also integrates with the TMDB API to fetch real-time posters, movie details, and genre-based recommendations.

## Tech Stack

- **ML Model** — TF-IDF + Cosine Similarity (scikit-learn)
- **Backend** — FastAPI + TMDB API
- **Frontend** — Streamlit
- **Data** — TMDB Movies Metadata dataset

## Project Structure

```
movie-recommender/
├── model.ipynb          # Data preprocessing + TF-IDF model training
├── main.py              # FastAPI backend
├── app.py               # Streamlit frontend
├── requirements.txt
└── *.pkl                # Trained model artifacts
```

## API Endpoints

| Endpoint | Description |
|----------|-------------|
| `GET /health` | Health check |
| `GET /home` | Trending/popular movies feed |
| `GET /tmdb/search?query=` | Search movies by name |
| `GET /movie/search?query=` | TF-IDF + genre recommendations bundle |
| `GET /recommend/tfidf?title=` | TF-IDF recommendations only |
| `GET /recommend/genre?tmdb_id=` | Genre-based recommendations |

## Setup

1. Clone the repo
```bash
git clone https://github.com/abhaydv77/movie-recommender
cd movie-recommender
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Add your TMDB API key in a `.env` file
```
TMDB_API_KEY=your_api_key_here
```
Get a free key at [themoviedb.org](https://www.themoviedb.org/settings/api)

4. Train the model (run `model.ipynb`) to generate `.pkl` files

5. Start the FastAPI server
```bash
uvicorn main:app --reload
```

6. Run the Streamlit app
```bash
streamlit run app.py
```

## API Docs

Once the server is running, visit `http://127.0.0.1:8000/docs` for interactive API documentation.

## Note
This is a self-learning project. 
ML model is built from scratch. 
FastAPI and Streamlit implementation 
done with reference to documentation and AI assistance.

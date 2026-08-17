# Feedback Analyzer

A simple customer feedback analysis app using Streamlit and FastAPI.

The Streamlit frontend (`app.py`) accepts customer reviews one per line and sends each review to the FastAPI backend (`api.py`). The backend uses the Google Gemini API to classify sentiment, rating score, and main theme, then returns JSON results.

## Features

- Paste multiple customer reviews into a Streamlit dashboard
- Analyze each review with sentiment label, score, and theme
- Display results and summary metrics
- Save analysis results to a local SQLite database
- View saved review history in the dashboard

## Requirements

- Python 3.14+
- Dependencies are listed in `pyproject.toml`
- A `.env` file with Gemini API credentials for `google-genai`

## Install

1. Create and activate a virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -U pip
pip install -r requirements.txt
```

> If you don't have `requirements.txt`, install via `pip install .` or `pip install fastapi[standard] google-genai pydantic python-dotenv requests streamlit`.

## Run the backend

```powershell
uv run uvicorn api:app --reload
```

This starts the FastAPI service on `http://127.0.0.1:8000`.

## Run the Streamlit frontend

In a separate terminal:

```powershell
uv run streamlit run app.py
```

## Usage

1. Open the Streamlit app in your browser.
2. Paste reviews into the text area, one per line.
3. Click `Analyze`.
4. Review the results, summary, and optionally save them.
5. View saved history in the expandable section.

## Files

- `app.py` - Streamlit frontend
- `api.py` - FastAPI backend service
- `database.py` - SQLite persistence helper
- `sample_reviews.txt` - example reviews for testing
- `feedback.db` - local SQLite database file
- `pyproject.toml` - project metadata and dependencies

## Notes

- The backend expects the Google Gemini client to be configured via environment variables.
- This project is intended as a practice app for customer feedback analysis and demo purposes.

# Stack Overflow Question Tagger API

A multi-label natural language processing project for automatically assigning technical tags to Stack Overflow questions.

The project covers text preparation, label selection, sentence embeddings, multi-label classification, model evaluation and deployment through a FastAPI inference service.

## Project objective

Stack Overflow questions may belong to several technical categories at the same time. The objective is therefore to predict a set of relevant tags from the title and body of a question.

## Approach

- Cleaned HTML and normalized question text.
- Studied the distribution of labels and retained the most useful tags for experimentation.
- Encoded questions using Sentence Transformers.
- Trained and compared multi-label classification approaches.
- Improved accuracy by 5.3 percentage points and F1-score by 0.5 percentage points over the baseline.
- Exposed the selected model through a FastAPI endpoint.

## Repository contents

- `main.py`: FastAPI application and `/predict` endpoint.
- `model.py`: preprocessing and inference pipeline.
- `trained_model.pkl`: trained multi-label classifier.
- `multilabel_binarizer.pkl`: fitted label encoder.
- `requirements.txt`: runtime dependencies.

## API usage

Install the dependencies:

```bash
pip install -r requirements.txt
```

Start the API:

```bash
uvicorn main:app --reload
```

Example request:

```bash
curl -X POST "http://127.0.0.1:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{"text":"How can I sort a Python dictionary by value?"}'
```

Example response:

```json
{
  "tags": ["python"]
}
```

## Technologies

Python, scikit-learn, Sentence Transformers, pandas, FastAPI and Pydantic.

## Context

This project was completed as part of a project-based Machine Learning Engineer program.

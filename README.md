# Stack Overflow Question Tagger

An end-to-end multi-label natural language processing project for automatically assigning technical tags to Stack Overflow questions.

The repository brings together the complete workflow: corpus exploration, text preparation, label selection, representation learning, model comparison, evaluation, model export, and deployment through a FastAPI inference service.

## Project objective

Stack Overflow questions may belong to several technical categories at the same time. The objective is therefore to predict a set of relevant tags from the title and body of a question.

## Project workflow

1. Explored the question corpus and analyzed the distribution of Stack Overflow tags.
2. Selected 50 target tags and prepared question titles and bodies for modeling.
3. Evaluated unsupervised topic modeling and supervised multi-label classification approaches.
4. Compared TF-IDF, Word2Vec, Sentence Transformer, Universal Sentence Encoder, and dimensionality-reduction variants.
5. Selected a one-vs-rest logistic-regression classifier using Sentence Transformer embeddings.
6. Serialized the selected classifier and label encoder for inference.
7. Exposed the inference workflow through a FastAPI endpoint.

During project evaluation, the selected approach improved accuracy by 5.3 percentage points and F1-score by 0.5 percentage points over the project baseline.

## Repository structure

```text
.
├── notebooks/
│   ├── 01_data_exploration_and_preparation.ipynb
│   ├── 02_model_experiments.ipynb
│   └── 03_selected_model_and_export.ipynb
├── data/
│   └── README.md
├── docs/
│   └── project_presentation.pptx
├── main.py
├── model.py
├── trained_model.pkl
├── multilabel_binarizer.pkl
└── requirements.txt
```

- `notebooks/` documents the experimental workflow from data exploration to model selection.
- `main.py` defines the FastAPI application and `/predict` endpoint.
- `model.py` contains text preprocessing and inference.
- `trained_model.pkl` and `multilabel_binarizer.pkl` are the inference artifacts used by the API.
- `docs/` contains the original project presentation.

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

Python, pandas, scikit-learn, Sentence Transformers, NLTK, Gensim, XGBoost, TensorFlow, FastAPI, Pydantic and Jupyter.

## Reproducing the experiments

The raw Stack Overflow export is not stored in this repository. See [`data/README.md`](data/README.md) for the expected filenames and execution order. The experiment notebooks require additional research libraries and substantially more compute than the API.

## Context

This project was completed as part of a project-based Machine Learning Engineer program.

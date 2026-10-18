# Notebooks

The notebooks document the project from raw-data exploration to model export:

1. `01_data_exploration_and_preparation.ipynb` studies the corpus, selects the target tags, cleans the text, and creates the prepared dataset.
2. `02_model_experiments.ipynb` compares topic-modeling and supervised multi-label approaches using several text representations and classifiers.
3. `03_selected_model_and_export.ipynb` presents the selected Sentence Transformer and logistic-regression pipeline and exports the inference artifacts.

The notebooks preserve the original experimental work. Their execution requires the datasets described in `data/README.md` and additional research dependencies beyond the lightweight API requirements.

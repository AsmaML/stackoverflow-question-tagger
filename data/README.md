# Data

The modeling workflow uses a Stack Overflow question export containing titles, bodies, tags, and engagement metadata.

The raw export is not included in this repository. To reproduce the preparation workflow, place it at the repository root as `QueryResults.csv` and run `notebooks/01_data_exploration_and_preparation.ipynb`. The notebook produces `cleaned_data_stackoverflow_questions.feather`, which is used by the model-experiment notebooks.

The project retained 50 tags for the multi-label classification experiments.

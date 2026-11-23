# Fake News Classification with NLP

This repository contains an **academic Natural Language Processing coursework
deliverable**, not a production project or a deployable misinformation-detection
system. The work was completed by Sergio Martínez Olivera and Daniel Roldan
Serrano as a comparative notebook study of fake-news classification methods.

## Contents

- [`coursework/nlp/fake-news-classification/NLPSergio_Daniel.ipynb`](coursework/nlp/fake-news-classification/NLPSergio_Daniel.ipynb)
  — the complete analysis, experiments, explanations, and saved outputs.
- [`coursework/nlp/fake-news-classification/requirements.txt`](coursework/nlp/fake-news-classification/requirements.txt)
  — the Python packages imported by the notebook.

The notebook expects two input files in its working directory
(`coursework/nlp/fake-news-classification/`):

- `fake.csv` — articles labelled as fake
- `true.csv` — articles labelled as true

These external dataset files are not included in this repository. Obtain them
separately and place them beside the notebook before rerunning the experiments.

## Methods

The notebook compares:

- Count-based and TF-IDF text representations
- A Decision Tree, k-nearest neighbors, and Multinomial Naive Bayes
- Three simple Keras embedding-layer classifiers:
  - embeddings learned from the task data
  - an attempted TF-IDF-derived initialization described in the notebook as
    frozen embeddings
  - the same initialization with the embedding layer trainable

The embedding experiments should not be interpreted as using externally
pre-trained word vectors: the notebook derives the available initialization
from the corpus TF-IDF matrix.

## Reported results

The following values are the saved test-set outputs in the notebook:

| Experiment | Test accuracy | Macro F1 |
| --- | ---: | ---: |
| Decision Tree, `max_depth=5` | 99.39% | Not reported |
| k-NN, `k=2` | 64.79% | Not reported |
| Multinomial Naive Bayes, `alpha=0.1` | 95.37% | Not reported |
| Neural model 1 | 96.49% | 96.48% |
| Neural model 2 | 95.37% | 95.35% |
| Neural model 3 | 95.81% | 95.80% |

These are notebook-specific results from one train/test setup, not a
production benchmark or a guarantee of performance on new sources of news.

## Running the notebook

1. Install the dependencies:

   ```bash
   python -m pip install -r coursework/nlp/fake-news-classification/requirements.txt
   ```

2. Place the external `fake.csv` and `true.csv` files in
   `coursework/nlp/fake-news-classification/`.
3. From that directory, open `NLPSergio_Daniel.ipynb` in Jupyter or Google
   Colab and run the cells. The relative CSV paths require the notebook's
   working directory to be that directory.

The notebook records a random seed for the scikit-learn splits. Neural-network
training may still vary between environments because complete TensorFlow
determinism is not configured.

## Collaboration

This coursework was developed in collaboration with
[Daniel Roldan Serrano](https://github.com/danirold).

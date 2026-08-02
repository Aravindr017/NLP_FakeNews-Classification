# Project: Fake News Classification

## Overview
This project focuses on building a system to classify news articles as 'real' or 'fake'. It leverages Natural Language Processing (NLP) techniques to process textual data from news articles and employs a Logistic Regression model for the classification task. The primary goal is to accurately distinguish between authentic and fabricated news content, a critical challenge in the digital age.

## Dataset
The project utilizes the "Fake News Classification" dataset, obtained from Kaggle. This dataset comprises news articles, each labeled to indicate whether it is real (1) or fake (0). It is divided into training, evaluation, and test sets to ensure robust model development and validation.

**Source:** [Kaggle: Fake News Classification](https://www.kaggle.com/datasets/aadyasingh55/fake-news-classification)

**Key Features:**
*   `title`: The headline of the news article.
*   `text`: The main body content of the news article.
*   `label`: The target variable, indicating whether the news is real (1) or fake (0).

## Preprocessing & Feature Engineering
The raw text data undergoes a series of preprocessing steps to prepare it for model training. This includes:

1.  **Column Dropping**: The initial `Unnamed: 0` column (likely an index) is removed from the dataframes.
2.  **Text Combination**: The `title` and `text` columns are concatenated into a new `content` column, providing a richer text source for analysis.
3.  **Lowercasing**: All text is converted to lowercase to ensure consistency and reduce vocabulary size.
4.  **HTML Tag Removal**: HTML tags, if present, are removed from the text.
5.  **URL Removal**: URLs are identified and removed from the text.
6.  **Punctuation Removal**: Punctuation marks are removed to focus on words.
7.  **Number Removal**: Numerical digits are removed from the text.
8.  **Tokenization**: The cleaned text is broken down into individual words (tokens).
9.  **Stopword Removal**: Common English stopwords (e.g., 'the', 'is', 'a') are removed as they typically do not carry significant meaning for classification.
10. **Lemmatization**: Words are reduced to their base or root form (e.g., 'running' to 'run') to normalize vocabulary.
11. **Text Joining**: The processed tokens are joined back into a single string (`clean_text`) for each article.
12. **Label Encoding**: The categorical 'label' column (0 or 1) is encoded using `LabelEncoder` for consistency, although in this binary case, it doesn't change the values, it ensures proper data type handling.

## Model Building

1.  **Feature Split**: The preprocessed `clean_text` column serves as the feature (`X`), and the `label` column as the target (`y`).
2.  **Train-Test Split**: The training data (`X`, `y`) is split into training and validation sets (`X_train`, `X_test`, `y_train`, `y_test`) to evaluate model performance on unseen data.
3.  **TF-IDF Vectorization**: Textual features are transformed into numerical vectors using `TfidfVectorizer`. This technique assigns weights to words based on their frequency in a document and their inverse frequency across the entire corpus. The vectorizer is configured with `max_features=5000` and `ngram_range=(1, 2)` to capture unigrams and bigrams.
4.  **Logistic Regression**: A `LogisticRegression` model is chosen for classification, with `max_iter=1000` to ensure convergence, especially with the high-dimensional TF-IDF features.
5.  **Pipeline**: A `Pipeline` is used to streamline the workflow, sequentially applying TF-IDF vectorization followed by Logistic Regression.

## Evaluation Metrics
The model's performance is evaluated using standard classification metrics:
*   **Accuracy**: The proportion of correctly classified instances.
*   **Precision**: The proportion of positive identifications that were actually correct.
*   **Recall**: The proportion of actual positives that were identified correctly.
*   **F1-Score**: The harmonic mean of precision and recall, providing a balance between the two.
*   **Confusion Matrix**: A table summarizing the performance of a classification model, showing true positives, true negatives, false positives, and false negatives.

## How to Run the Project

### Prerequisites
*   Python 3.x
*   `pandas`
*   `numpy`
*   `nltk`
*   `scikit-learn`

### Installation
Install the necessary libraries using pip:
```bash
pip install pandas numpy nltk scikit-learn
```
Download NLTK data if needed:
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

### Project Workflow (as implemented in the notebook)
1.  **Mount Google Drive**: Execute the cell to mount Google Drive to access dataset files.
2.  **Import Libraries**: Run the cell to import all necessary Python libraries.
3.  **Read Datasets**: Load `train (2).csv`, `evaluation.csv`, and `test (1).csv` into pandas DataFrames, specifying `sep=';'`.
4.  **EDA (Exploratory Data Analysis)**: Review dataset information, shapes, and verify uniqueness across datasets.
5.  **Preprocessing**: Execute the sequence of cells for dropping columns, combining text, lowercasing, removing HTML/URLs/punctuation/numbers, tokenization, stopword removal, lemmatization, and joining tokens.
6.  **Label Encoding**: Apply `LabelEncoder` to the 'label' column of the training and evaluation dataframes.
7.  **Model Building**: Execute cells for splitting data, initializing `TfidfVectorizer` and `LogisticRegression`, and creating the `Pipeline`.
8.  **Model Training**: Fit the `model_pipeline` on the `X_train` and `y_train` data.
9.  **Model Evaluation**: Run the cells to predict on the test set, calculate metrics, and print the accuracy, classification report, and confusion matrix.

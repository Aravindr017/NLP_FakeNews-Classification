# NLP_FakeNews-Classification
The Fake News Classification Dataset is an English-language dataset containing just over 45,000 unique news articles. These articles are classified as true (1) or false (0), making it a valuable resource for researchers and practitioners in the field of fake news identification using Machine Learning and Deep Learning  models.

# Fake News Classification using NLP

## 📌 Project Overview

This project focuses on preprocessing textual data for a Fake News Classification system. The objective is to clean and prepare news articles so they can be used effectively for machine learning and deep learning models.

At this stage, the project covers the complete NLP preprocessing pipeline.

---

## 📂 Dataset

- *Dataset:* Fake News Classification Dataset
- *Source:* Kaggle
- *Type:* Text Classification
- *Target:* Classify news articles as *Fake* or *Real*

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- NLTK
- Regular Expressions (re)

---

## 📋 NLP Preprocessing Steps

The following preprocessing techniques have been implemented:

### 1. Lowercase Conversion
Converts all text into lowercase to maintain consistency.

Example:

This IS Fake News

↓

this is fake news

---

### 2. HTML Tag Removal

HTML tags are removed.

Example:

<p>This is fake news.</p>

↓

This is fake news.

---

### 3. URL Removal

All website links are removed from the text.

Example:

Visit https://example.com

↓

Visit

---

### 4. Punctuation Removal

Removes punctuation symbols such as:

.,!?;:"()[]{}

---

### 5. Tokenization

Splits each sentence into individual words (tokens).

Example:

This is fake news

↓

['This', 'is', 'fake', 'news']

---

### 6. Stopword Removal

Removes frequently occurring words that provide little meaning.

Example:

This is a fake news article

↓

fake news article

---

### 7. Lemmatization

Converts words into their base (dictionary) form while preserving their actual meaning.

Example:

```
running
ran
runs
```
↓

```
run

---

## 👨‍💻 Author

*Kiran*

NLP Preprocessing for Fake News Classification has done completely.

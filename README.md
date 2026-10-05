# ML-Mini-Project-HitPredict-Predicting-Billboard-Hits-Using-Spotify-Data

# HitPredict: Predicting Billboard Hits Using Spotify Data

## 1. Project Overview

**HitPredict** is a machine learning project that predicts whether a song is likely to be a Billboard Hot 100 hit using Spotify audio features.

The project combines Billboard Hot 100 song data with Spotify playlist data and constructs a binary classification dataset:

* `1` → Billboard Hot 100 song (Hit)
* `0` → Non-Billboard song used as the non-hit class

The project explores different machine learning classification algorithms and compares their performance using standard evaluation metrics.

---

## 2. Problem Statement

Predicting whether a song can become a popular hit is useful for understanding the relationship between musical characteristics and commercial success.

The objective of HitPredict is to build a machine learning model that learns from Spotify audio features and predicts whether a song belongs to the Billboard Hot 100.

---

## 3. Dataset

Two datasets were used:

### Billboard Hot 100 Dataset

The Billboard dataset contains songs that appeared on the Billboard Hot 100 along with Spotify audio features.

Important features include:

* Danceability
* Energy
* Acousticness
* Instrumentalness
* Liveness
* Loudness
* Speechiness
* Tempo
* Valence
* Key
* Mode
* Time Signature
* Song Length
* Spotify Popularity

These songs were assigned:

```text
hit = 1
```

### Spotify Playlist Dataset

A Spotify playlist dataset containing songs and their corresponding Spotify audio features was used to construct the non-hit class.

Songs matching Billboard songs were removed before assigning the non-hit label.

These remaining songs were assigned:

```text
hit = 0
```

The playlist data was restricted to years up to 2022 so that songs from years beyond the Billboard dataset's coverage were not automatically treated as non-hits.

---

## 4. Data Preprocessing

The following preprocessing steps were performed:

1. Loaded both datasets.
2. Inspected the datasets and their columns.
3. Standardized song-title formatting for matching.
4. Removed playlist songs that matched Billboard songs.
5. Restricted playlist songs to the relevant year range.
6. Selected common Spotify audio features from both datasets.
7. Renamed corresponding columns to a common format.
8. Combined the two datasets.
9. Removed rows containing missing values.
10. Created the binary target variable `hit`.

---

## 5. Features Used

The model uses Spotify-related features such as:

* Popularity
* Acousticness
* Danceability
* Energy
* Instrumentalness
* Liveness
* Loudness
* Speechiness
* Tempo
* Valence
* Key
* Mode
* Time Signature
* Song Length

The target variable is:

```text
hit
```

where:

```text
1 = Billboard Hot 100 hit
0 = Non-hit class
```

---

## 6. Machine Learning Models

Three classification algorithms were implemented and compared:

### Logistic Regression

A baseline classification model used to estimate the probability of a song belonging to the hit class.

### Decision Tree

A tree-based classification model that learns decision rules from the input features.

A maximum tree depth was used to reduce overfitting.

### Random Forest

An ensemble of decision trees used to improve generalization and reduce the tendency of a single decision tree to overfit.

---

## 7. Model Evaluation

The dataset was divided into training and testing sets using an 80:20 split with stratification.

The following evaluation metrics were used:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

The models were compared using a final performance table generated in the notebook.

---

## 8. Results

The notebook generates a comparison of the three models based on their:

* Accuracy
* Precision
* Recall
* F1-score

It also generates a feature-importance plot for the Random Forest model to identify which Spotify features contributed most to its predictions.

**The exact numerical results should be taken from the final notebook output.**

---

## 9. Project Structure

```text
HitPredict/
│
├── HitPredict.ipynb
├── HitPredict_Final_Dataset.csv
├── README.md
└── report.pdf
```

---

## 10. How to Run

### Option 1: Google Colab

1. Open the notebook in Google Colab.
2. Upload the required datasets.
3. Run the notebook cells sequentially.
4. The preprocessing, model training, evaluation and visualizations will be generated automatically.

### Option 2: Jupyter Notebook

Install the required Python libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Open the notebook using Jupyter Notebook or JupyterLab and execute the cells sequentially.

---

## 11. Limitations

The non-hit class is constructed from Spotify playlist songs that were not matched with the Billboard dataset. Therefore, the non-hit label does not guarantee that a song never appeared on Billboard.

Song matching was primarily based on normalized song titles, so differences in naming, versions or metadata may affect matching.

The model also uses a random train-test split, so temporal changes in music trends are not explicitly evaluated.

---

## 12. Conclusion

HitPredict demonstrates how Spotify audio characteristics can be used to build machine learning models for Billboard hit classification.

Logistic Regression, Decision Tree and Random Forest were implemented and compared using multiple evaluation metrics. The project also analyzes Random Forest feature importance to understand which musical characteristics have greater influence on predictions.

The complete implementation, dataset and experimental results are provided in this repository.

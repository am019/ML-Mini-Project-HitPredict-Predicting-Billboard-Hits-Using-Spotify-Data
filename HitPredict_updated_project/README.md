# HitPredict: Predicting Billboard Hits Using Spotify Data

UE24CS352A Machine Learning Mini-Project · Team A-06 · Project 21
Ahan A Mysore (PES1UG24AM019) · Bhoomika Patil (PES1UG25AM801)

Binary classifier: is a song a **Billboard Hot 100 hit (1)** or a **non-hit (0)**, from Spotify audio features? Inspired by *HitPredict* (Georgieva, Suta, Burton; Stanford CS229, 2018).

## Key result (v2)
The data is 89% hits, so "always predict hit" already scores 89% accuracy. v1 matched that and found almost no non-hits. v2 de-duplicates, class-weights the models and evaluates with stratified 5-fold CV and imbalance-aware metrics:

| Model (5-fold CV, 14 features) | Balanced acc. | ROC-AUC | Non-hit recall |
|---|---|---|---|
| Majority baseline | 0.500 | 0.500 | 0.000 |
| Logistic Regression | 0.754 | 0.806 | 0.820 |
| Decision Tree (depth 5) | 0.746 | 0.789 | 0.829 |
| Random Forest (200 trees) | 0.739 | 0.828 | 0.721 |

## Files
| File | Purpose |
|---|---|
| `HitPredict_v2.ipynb` | Full pipeline: audit, baseline, corrected evaluation, plots, `predict_song()` demo |
| `HitPredict_Final_Dataset.csv` | Merged dataset (7,713 rows; 358 exact duplicates removed inside the notebook) |
| `Report_HitPredict_v2.pdf` | 2-page write-up |
| `figures/` | Plots produced by the notebook |

## How to run
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook HitPredict_v2.ipynb      # Run All
```
The notebook loads `HitPredict_Final_Dataset.csv` if present. To rebuild it from scratch, delete that file and place `Billboard_Hot100_Songs_Spotify_1946-2022.csv` and `playlist_2010to2023.csv` (Kaggle) next to the notebook. Works in Google Colab too (upload the same files).

## Limitations
- Non-hits are playlist songs not matched *by title* to Billboard, so labels are noisy and non-hits are popular tracks, not typical ones.
- Hits span 1946-2022; non-hits start around 2000, so Loudness/Energy partly encode era.
- `Popularity` is Spotify's current score (partly a consequence of success); an ablation without it is reported.
- Random splits ignore time; a temporal split is future work.

# Olist Review-Score Prediction

**Project 2 for the Introduction to Data Science course at NES**

This repository predicts the customer **review score** (1–5 stars) for every order in the public Brazilian e-commerce dataset provided by **Olist**.
The goal is to anticipate buyer satisfaction before the actual review is written.

## 🌟 Highlights

* **Presentation:** concise Beamer slide‑deck (`presentation/slides.pdf`) summarising methodology and results.
* **Data Loading:** Reads all relevant CSV tables (orders, items, payments, reviews).
* **Feature Engineering:**
  * Numeric – delivery time, cart value, freight, number of items, payment stats, purchase weekday/month.
  * Text – concatenated review *title + message* embedded with **spaCy FastText** vectors (300 dim) and compressed to **120 dim** via Truncated SVD.
* **Class Balancing:** Equalises the five star-ratings through undersampling.
* **Models Compared:**
  1. Linear Regression → rounded & clipped to 1–5
  2. Multinomial Logistic Regression
  3. Ordinal Logistic Regression (*mord*)
* **Evaluation:** Accuracy, MAE, RMSE and full confusion matrices.
* **Lightweight:** Runs entirely on CPU – no PyTorch / Transformers required.

## 📂 Repository Structure
```
├── data/                          # Raw CSV files (download from Kaggle)
├── figures/                       # Generated PNG visualisations
├── olist_review_prediction.ipynb  # Jupyter notebook (this project)
└── README.md                      # Project overview and instructions
```

## 🚀 Getting Started

1. **Clone**

   ```bash
   git clone https://github.com/TiagoCavalcante/olist-review-pred.git
   cd olist-review-pred
   ```

2. **Install dependencies**

   ```bash
   pip install pandas numpy scikit-learn seaborn spacy mord
   python -m spacy download pt_core_news_md
   ```

3. **Run**

   ```bash
   jupyter lab olist_review_prediction.ipynb
   ```

4. **View results**

   * Confusion matrices and accuracy bar-plot are saved to `figures/`.
   * The notebook displays a metrics table and per-class diagnostics.

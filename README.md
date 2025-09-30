# Post Recommendation System

<div align="center">

##*"Connecting Users with Content, Intelligently"*

</div>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue?style=for-the-badge&logo=python)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-1.x-blue?style=for-the-badge&logo=pandas)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange?style=for-the-badge&logo=scikit-learn)](https://scikit-learn.org/)

**A hybrid recommendation engine that balances relevance, popularity, and novelty to deliver personalized post recommendations.**

[🚀 How it Works](#-how-it-works) • [📊 Features](#-features) • [📈 Evaluation](#-evaluation) • [⚙️ Setup](#️-setup)

</div>

---

## 🎯 Overview

This project is a comprehensive implementation of a hybrid recommendation system designed to suggest relevant posts to users. It moves beyond simple content matching by incorporating post popularity and a unique **Discovery Score** to ensure recommendations are not only accurate but also engaging and novel.

**Why this approach?**
- ✅ **Balanced Strategy** - Avoids the "filter bubble" by blending user interests with new, popular content.
- ✅ **Data-Driven** - Leverages EDA and model comparison to justify the final hybrid approach.
- ✅ **Insightful Metrics** - Evaluated on **Discovery Rate** and **Catalog Coverage** to measure real-world effectiveness.
- ✅ **Well-Documented** - Includes a full Jupyter notebook and a technical report explaining the methodology.

---

## 🚀 How it Works

The system generates recommendations through a multi-stage pipeline that analyzes user and content data to produce a ranked list of suggestions for each user.

### 💡 Methodology Flowchart
The core logic of the project is broken down into several key stages:

```
┌───────────────────────────────────┐
│           Data Loading            │
└───────────────────────────────────┘
               │
               ▼
┌───────────────────────────────────┐
│   Exploratory Data Analysis (EDA)   │
└───────────────────────────────────┘
               │
               ▼
┌───────────────────────────────────┐
│       Feature Engineering         │
└───────────────────────────────────┘
               │
               ▼
┌───────────────────────────────────┐
│  Model Comparison & Hybrid Model  │
└───────────────────────────────────┘
               │
               ▼
┌───────────────────────────────────┐
│     Generate Recommendations      │
└───────────────────────────────────┘
```

### 🛠️ The Recommendation Model

The final recommendation engine is a hybrid model that calculates a `final_score` for each potential user-post pair. The formula is as follows:

`final_score = (0.45 * content_score) + (0.35 * popularity_score) + (0.20 * discovery_score)`

- **`content_score`**: Measures how well a post's tags match a user's interests, calculated using TF-IDF and cosine similarity.
- **`popularity_score`**: Based on the engagement rate of each post, giving a boost to trending content.
- **`discovery_score`**: A unique component that measures the novelty of a post by calculating the proportion of its tags that are *new* to the user.

---

## 📊 Features

| Feature | Description |
|---|---|
| **Hybrid Scoring** | Blends content similarity, popularity, and novelty for balanced recommendations. |
| **Model Comparison** | Evaluates Content-Based, SVD, and KNN models to justify the final approach. |
| **User Segmentation**| Calculates an "exploration score" to segment users (e.g., "Power Explorers"). |
| **Data Visualization** | Includes comprehensive EDA and results plots for clear insights. |

---

## 📈 Evaluation

The model's performance was evaluated on two key metrics that measure the quality and diversity of the recommendations.

| Metric | Result | Description |
|---|---|---|
| **Discovery Rate** | **13.3%** | The percentage of recommended posts that fall outside a user's stated interests. |
| **Catalog Coverage**| **30.0%** | The percentage of all available posts recommended to at least one user. |

### Evaluation Flowchart

```
┌───────────────────────────────────┐
│  Top 3 Recommendations per User   │
└───────────────────────────────────┘
               │
┌──────────────┴──────────────┐
│                             │
▼                             ▼
┌───────────────────┐   ┌───────────────────┐
│ Calculate         │   │ Calculate         │
│ Discovery Rate    │   │ Catalog Coverage  │
└───────────────────┘   └───────────────────┘
│                             │
└──────────────┬──────────────┘
               │
               ▼
┌───────────────────────────────────┐
│      Summarize Final Results      │
└───────────────────────────────────┘
```

---

## ⚙️ Setup

To run this project, you will need Python and the libraries listed in `requirements.txt`.

1.  **Clone the repository**.
2.  **Place the original datasets** (`Users.csv`, `Posts.csv`, `Engagements.csv`) into the `data/` directory.
3.  **Install dependencies**: `pip install -r requirements.txt` (You may need to create this file).
4.  **Run the Jupyter Notebook**: Open and execute the `post_recommendation_system.ipynb` to see the full analysis and generate the output files.

---

## 📁 Project Structure

```
submission/
├── post_recommendation_system.ipynb      # Main notebook with all code and analysis
├── README.md                             # This overview file
├── visualizations/                       # Directory for all generated PNG files
│   ├── EDA.png
│   ├── eval_results.png
│   ├── interest_coherence.png
│   ├── model_compr.png
│   └── user_exploration.png
├── outputs/                              # Directory for all generated CSV files
│   ├── recommendations_output.csv
│   ├── user_profiles_enhanced.csv
│   └── summary_statistics.csv
└── data/                                 # Directory for the original datasets
    ├── Users.csv
    ├── Posts.csv
    └── Engagements.csv
```

---

## 🔮 Future Extensions

- **v1.1** - Incorporate Collaborative Filtering to leverage "similar user" data.
- **v1.2** - Use advanced NLP (e.g., Word2Vec) for semantic understanding of tags.
- **v2.0** - Deploy the model as a REST API and build a simple web interface for live recommendations.
---
<div align="center">

*This project was created as part of an ML internship application.*

</div>

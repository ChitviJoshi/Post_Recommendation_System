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

<img src="https://mermaid.ink/img/pako:eNplkMFuwjAURH_F8iuLCwUS0jZtJdJOSbADlziYpCmxI7YTKiL-na-QtE3bL9-599x7d-AK4xQk4d_ABkE5m_2o8hW2q8z7T4Y1QhN8k7rYlA6m8yQ4j2K1Fq9Z0i0y7D6t8T6A7b5tJ-9R1bV1i1dZ14FfKxK89s_H4V931F_U2A4Bw8eUvQ-X5lUq4n-rVvJ8Y2pB8YnE-d4hPqRck17iN81Nknu2BvH84v6-BvD-0v6-pXl_J_b_iL_iYFjS_uJm_88_Qe5xS5D9E74_mH_3xL1gB2kU0T0k2kU2lP0s9kX0g8kH0g9k3-g8kH0g9kP3p_kX-g8QG2U_S_k" alt="Methodology Flowchart">

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

<img src="https://mermaid.ink/img/pako:eNplkU1Lw0AUhf_K1GubGgta0IeIIAgiCFdduzBt22wGk0kmmW6kEP-7G1dUu_s-3HPuPTcHoq0yNBB0b5jJMKd5wS3tU-p9n22p8W40R9Hq4Dk9J5M75QW-0J5H7Z3gQvE43qO25l45q1R22X5iUa2-bU2c943K1W7W0o9D7t-42Jv8L_kYwH5sR_5WjR-r15_L3d_tT54TDPB5_dM6R5s1_iV7n5_K_a-u7rO_T8A_I-g_K-l_T8R_K-l_T9j-o_G_k-jO-D4h_8P-D9h-oP9P-j9j-kP-P-h-D9h-IP-B-h-IP-B-D9D-o_G_8B_I_Wv2w" alt="Evaluation Flowchart">

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

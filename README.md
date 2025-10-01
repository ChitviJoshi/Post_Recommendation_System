# Post Recommendation System

<div align="center">

## *"Connecting Users with Content They'll Actually Engage With"*

</div>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue?style=for-the-badge&logo=python)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-1.x-blue?style=for-the-badge&logo=pandas)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange?style=for-the-badge&logo=scikit-learn)](https://scikit-learn.org/)

**A hybrid recommendation engine that balances what users love with what they might discover.**

[🚀 Quick Start](#-quick-start) • [📊 Key Results](#-key-results) • [🛠️ How It Works](#️-how-it-works) • [📁 Project Structure](#-project-structure)

</div>

---

## 🎯 What This Does

This recommendation system suggests 3 personalized posts to each user by combining:
- **What they're interested in** (content matching)
- **What's actually good** (popularity signals)  
- **What they haven't tried yet** (discovery)

Think Spotify recommendations - mostly your vibe, occasionally something new that expands your taste.

**Built for**: ML Internship Application Task

---

## 📊 Key Results

| Metric | Value | What It Means |
|--------|-------|---------------|
| **Users Served** | 50 | Every user got 3 personalized recommendations |
| **Content Match Score** | 0.555 | Recommendations align well with stated interests |
| **Popularity Score** | 0.760 | High-quality content prioritized (not random posts) |
| **Discovery Rate** | 13.3% | ~1 in 7 recommendations introduces new topics |
| **Catalog Coverage** | 30.0% | 30/100 posts recommended (quality-first approach) |

### The Most Interesting Finding 🎵
Audio content dominated recommendations (39.3%) despite being only 12% of the catalog. Why? **The model learned that audio posts have 65% engagement vs 52% for images**. It figured out quality on its own!

---

## 🚀 Quick Start

### Prerequisites
```bash
Python 3.7+
pandas, numpy, scikit-learn, matplotlib, seaborn
```

### Run It
1. **Clone this repo**
2. **Add your data** to the `data/` folder:
   - `Users.csv` (user profiles with interests)
   - `Posts.csv` (content with tags)
   - `Engagements.csv` (interaction history)
3. **Install dependencies**:
   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn
   ```
4. **Open the notebook**:
   ```bash
   jupyter notebook post_recommendation_system.ipynb
   ```
5. **Run all cells** - outputs will be generated in `outputs/` and `visualizations/`

---

## 🛠️ How It Works

### The Pipeline

```
Data Loading → EDA & User Segmentation → Feature Engineering → Model Testing → Hybrid Model → Recommendations
```

### The Hybrid Model Formula

```python
Final Score = 0.45 × Content Match + 0.35 × Popularity + 0.20 × Discovery
```

**Example**: User interested in "sports, art, gaming"

```
Post P29 (tags: "sports, music"):
  Content:    0.333 (partial match - only sports)
  Popularity: 1.000 (everyone engaged with it!)
  Discovery:  0.500 (music is new to user)
  → Final:    0.600 (Ranked #1)
```

### Why These Weights?
- **0.45 Content**: Keep recommendations relevant
- **0.35 Popularity**: Trust the community's judgment  
- **0.20 Discovery**: Introduce novelty without being random

I tested this against pure collaborative filtering (SVD) and user-based (KNN) approaches - content-based gave the most diverse recommendations (3.8 unique tags vs 2.4 and 2.9).

---

## 📈 What I Built

### 1. **Exploratory Analysis**
- Found that users with "sports" interest engage 3× more with sports-tagged content
- Identified 3 user segments: Power Explorers (24%), Loyal Fans (18%), Medium (58%)
- Discovered huge quality variance (0-100% engagement rates)

### 2. **Feature Engineering**
- TF-IDF vectorization of interests and tags
- Engagement rate calculation per post
- Exploration scores to understand user behavior

### 3. **Model Comparison**
Tested 3 approaches on tag diversity:
- Content-Based: **3.8 unique tags** ✓ (winner)
- SVD: 2.4 unique tags
- KNN: 2.9 unique tags

### 4. **Evaluation Metrics**
- **Discovery Rate**: Measures recommendations outside stated interests
- **Catalog Coverage**: Ensures we're not stuck in filter bubbles

---

## 📁 Project Structure

```
submission/
├── post_recommendation_system.ipynb      # Full implementation + analysis
├── technical_report.pdf                  # 2-page methodology explanation
├── README.md                             # You are here!
├── visualizations/                       
│   ├── EDA.png                          # Dataset exploration
│   ├── model_compr.png                  # Model comparison results
│   ├── user_exploration.png             # User segmentation analysis
│   ├── interest_coherence.png           # Interest-tag connections
│   └── eval_results.png                 # Final metrics visualization
├── outputs/                              
│   ├── rec_output.csv                   # All 150 recommendations
│   └── summary_stats.csv                # Key metrics summary
└── data/                                 
    ├── Users.csv                        # Original user data
    ├── Posts.csv                        # Original post data
    └── Engagements.csv                  # Original engagement data
```

---

## 🔮 Future Improvements

If I had more time (or this was going to production), I'd add:

### Short-term (v1.1)
- **Segment-based weights**: Power Explorers get 0.30 discovery, Loyal Fans get 0.10
- **Explore-exploit**: 20% random sampling to boost catalog coverage
- **MMR re-ranking**: Penalize similar posts to increase diversity

### Medium-term (v1.2)
- **Real-time learning**: Thompson Sampling to adapt based on click-through rates
- **BERT embeddings**: Replace TF-IDF so "fitness" matches "exercise" semantically
- **Cold-start handling**: Demographic-based bootstrapping for new users

### Production-ready (v2.0)
- **A/B testing framework**: Test different weight combinations
- **FAISS for speed**: Sub-millisecond similarity search
- **Two-stage retrieval**: Fast candidate generation → precise re-ranking
- **REST API deployment**: Real-time recommendations via endpoint

---

## 📝 Technical Approach Summary

**Problem**: Recommend 3 posts per user balancing relevance and discovery

**Data**: 50 users, 100 posts, 1000 engagements (50% engagement rate)

**Solution**: Hybrid model combining content similarity (TF-IDF + cosine), popularity (engagement rates), and discovery (new tag ratio)

**Results**: 0.579 average final score with 13.3% discovery and 30% coverage

**Key Insight**: Audio content's over-representation (39.3% of recs) shows the model autonomously learned quality patterns

---

## 🤝 About This Project

Created as part of an ML internship application. The task was to build a recommendation system from scratch, evaluate it properly, and propose practical extensions.

**What I learned**:
- Real-world recommendation systems need more than just accuracy
- Discovery vs relevance is a constant tradeoff
- Sometimes "low" coverage (30%) is actually smart (quality-first)
- Audio content crushes it on this platform 🎧

---

<div align="center">

**Questions?** Check the technical report for detailed methodology, or dive into the notebook for the full implementation!

*Built with ❤️ and lots of sklearn*

</div>

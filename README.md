# Post Recommendation System

This repository contains a sophisticated post recommendation system designed to provide personalized content suggestions to users. The project leverages a hybrid recommendation model that combines content-based filtering, post popularity, and a unique "discovery" score to create a balanced and effective recommendation engine.

![EDA Plots](EDA.png)
![Model Comparison](model_compr.png)
![Evaluation Results](eval_results.png)

## 🚀 Project Overview

The primary goal of this project is to recommend the top 3 posts for each user based on their profile interests, past engagement, and the attributes of the content. The system is designed not only to provide relevant recommendations but also to encourage user exploration and prevent the "filter bubble" effect.

This is achieved through a multi-faceted approach:
1.  **Exploratory Data Analysis (EDA)**: A deep dive into the dataset to understand user demographics, content types, and engagement patterns.
2.  **Model Exploration**: A comparative analysis of three different recommendation models: Content-Based Filtering, SVD (Singular Value Decomposition), and K-Nearest Neighbors (KNN).
3.  **Hybrid Recommendation Engine**: A final, fine-tuned model that blends multiple recommendation strategies to provide the most relevant, popular, and novel suggestions.

## ✨ Features

* **Personalized Recommendations**: The core of the system is its ability to tailor recommendations to each user's unique interests.
* **Hybrid Model**: The final model is a sophisticated blend of:
    * **Content-Based Filtering**: Using TF-IDF and Cosine Similarity to match user interests with post tags.
    * **Popularity Score**: Leveraging the engagement rate of posts to recommend trending content.
    * **Discovery Score**: A unique feature that encourages users to explore new topics beyond their stated interests.
* **User Segmentation**: The system includes an "exploration score" to segment users into categories like "Power Explorers" and "Loyal Fans," allowing for more targeted recommendation strategies in the future.
* **Comprehensive Evaluation**: The model's performance is evaluated on key metrics like **Discovery Rate** and **Catalog Coverage**, providing a clear picture of its effectiveness.

## 📊 The Datasets

The project utilizes three distinct datasets:

* **Users.csv**: Contains user information, including their ID, age, gender, top 3 interests, and a pre-calculated past engagement score.
* **Posts.csv**: Includes details about each post, such as its ID, the creator's ID, the content type (e.g., video, image), and a list of tags.
* **Engagements.csv**: A record of user-post interactions, indicating whether a user engaged with a post (1 for engagement, 0 for no engagement).

## 💡 Methodology Flowchart

This flowchart illustrates the step-by-step process of the recommendation system.

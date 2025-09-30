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
    
    This flowchart illustrates the step-by-step process of the recommendation system, from data loading to the final output.
    
    ```mermaid
    graph TD
        A[Data Loading] --> B[Exploratory Data Analysis];
        B --> C[Feature Engineering];
        C --> D{Model Comparison};
        D --> E[Content-Based];
        D --> F[SVD];
        D --> G[KNN];
        C --> H[Hybrid Model Development];
        H --> I[Generate Recommendations];
    ```
    
    ## 🛠️ The Recommendation Model
    
    The final recommendation engine is a hybrid model that calculates a `final_score` for each potential user-post pair. The formula is as follows:
    
    `final_score = (0.45 * content_score) + (0.35 * popularity_score) + (0.20 * discovery_score)`
    
    * **`content_score`**: This is a measure of how well a post's tags match a user's interests. It is calculated using a TF-IDF vectorizer and cosine similarity.
    * **`popularity_score`**: This score is based on the engagement rate of each post, giving a boost to content that is popular among all users.
    * **`discovery_score`**: A unique and crucial component of the model. It measures the novelty of a post by calculating the proportion of its tags that are *new* to the user. This helps to introduce users to new topics and prevents their recommendations from becoming too narrow.
    
    ## 📈 Evaluation & Results
    
    The model's performance was evaluated on two key metrics that go beyond simple accuracy:
    
    * **Discovery Rate (33.3%)**: This metric measures the percentage of recommended posts that fall outside a user's explicitly stated interests. A higher discovery rate indicates that the system is successfully encouraging user exploration.
    * **Catalog Coverage (77.0%)**: This represents the percentage of all available posts that are recommended to at least one user. A high coverage rate means the system is recommending a wide variety of content and not just a few popular items.
    
    ### Evaluation Flowchart
    
    This flowchart shows how the evaluation metrics were calculated from the model's output.
    
    ```mermaid
    graph TD
        A[Top 3 Recommendations per User] --> B{For Each User};
        B --> C[Compare Recs with User Interests];
        C --> D[Calculate Discovery Rate];
        A --> E[Aggregate All Recommended Posts];
        E --> F[Count Unique Posts];
        F --> G[Calculate Catalog Coverage];
        D & G --> H[Summarize Final Results];
    ```
    
    ## ⚙️ How to Run the Project
    
    To run this project, you will need Python and the following libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, and `seaborn`.
    
    1.  **Clone the repository**:
        ```bash
        git clone https://github.com/ChitviJoshi/Post_Recommendation_System.git
        ```
    2.  **Install the required libraries**:
        ```bash
        pip install pandas numpy scikit-learn matplotlib seaborn
        ```
    3.  **Place the datasets (`Users.csv`, `Posts.csv`, `Engagements.csv`)** in the root directory of the project.
    4.  **Run the Jupyter Notebook**: Open and run the `Post_Recommendation_System.ipynb` notebook to see the full analysis and generate the recommendations.
    
    ## 🔮 Future Extensions
    
    This project provides a strong foundation for a recommendation system. Here are some potential extensions:
    
    * **Collaborative Filtering**: Incorporate collaborative filtering techniques to recommend posts based on the behavior of similar users.
    * **Content Embeddings**: Use more advanced NLP techniques like Word2Vec or BERT to create semantic embeddings for post tags and user interests, allowing for more nuanced content matching.
    * **Dynamic Weighting**: The weights in the final scoring model could be dynamically adjusted for each user. For example, "Power Explorers" could have a higher weight for the `discovery_score`.
    * **A/B Testing**: In a real-world scenario, the next step would be to deploy this model in an A/B test to measure its impact on key business metrics like user engagement and retention

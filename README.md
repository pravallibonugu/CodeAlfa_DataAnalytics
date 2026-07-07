# CodeAlpha Data Analytics Internship — Amazon Product Reviews Analysis

## 📌 Overview
This project was completed as part of the **CodeAlpha Data Analytics Internship** (June–July 2026 batch). It covers three tasks from the internship's task list:

- ✅ Task 2: Exploratory Data Analysis (EDA)
- ✅ Task 3: Data Visualization
- ✅ Task 4: Sentiment Analysis

The goal was to analyze a real-world Amazon product reviews dataset, uncover meaningful patterns, visualize them clearly, and classify review sentiment using NLP — while critically evaluating how reliable that sentiment analysis actually is.

## 📊 Dataset
**Source:** [Consumer Reviews of Amazon Products (Datafiniti) — Kaggle](https://www.kaggle.com/datasets/datafiniti/consumer-reviews-of-amazon-products)

- **34,626 reviews** (after cleaning) across Amazon devices (Fire Tablets, Echo, Kindle, Fire TV, etc.)
- Key columns used: `name`, `brand`, `reviews.rating`, `reviews.text`, `reviews.date`, `reviews.doRecommend`

## 🛠 Tools & Libraries
- Python (Google Colab)
- pandas — data cleaning & manipulation
- matplotlib, seaborn — visualization
- TextBlob — sentiment analysis (NLP)

## 🔍 Task 2: Exploratory Data Analysis — Key Findings

1. **Ratings are heavily skewed positive.** Mean rating is 4.58/5, with ~70% of all reviews being 5-star. This context matters for interpreting every other finding in this project.
2. **"Brand" isn't a meaningful grouping variable.** 83% of reviews fall under the brand "Amazon" itself (vs. actual third-party brands), so analysis was shifted to the **product name** level instead, which revealed much more useful variation (e.g., Fire Tablet 7" has 10,962 reviews alone).
3. **Negative reviews tend to be longer.** Median review length drops from ~32 words (1-star) to ~19 words (5-star) — dissatisfied customers explain their issues in more detail, while happy customers leave brief, affirming reviews.
4. **Review volume is highly uneven over time.** Most reviews are concentrated between **Nov 2015 and Sep 2017**; earlier and later periods have too few reviews to draw reliable conclusions. Within the reliable window, average rating stayed stable (4.45–4.70), with no strong upward or downward trend.

## 📈 Task 3: Data Visualization
Charts built to support the above findings:
- Distribution of review ratings (bar chart)
- Top 10 brands / top 10 products by review count
- Review length vs. rating (boxplot)
- Review volume per month (to validate data reliability)
- Average rating over time, restricted to the reliable date range
- Sentiment label vs. star rating (grouped bar chart)

Each chart was chosen to answer a specific question rather than just visualize data for its own sake.

## 💬 Task 4: Sentiment Analysis — Key Findings

- Used **TextBlob** to score each review's polarity and classify it as Positive / Neutral / Negative.
- Results: **85% Positive, 13% Neutral, 2% Negative** — consistent with the rating skew found in EDA.
- **Critical finding:** When cross-checked against actual star ratings, TextBlob mislabeled a large share of 1-star and 2-star reviews as "Positive" (39% of 1-star reviews!). Example:

  > *"We bought this... and it was never delivered. Best Buy was great."* — Rated 1 star, but classified as Positive.

  This happens because TextBlob is **lexicon-based** — it scores individual words (like "great") without understanding full sentence context (here, "great" referred to a retailer, not the product). This is a known limitation of simple sentiment models compared to context-aware approaches (e.g., transformer-based sentiment models).

## 🎯 Conclusion
This project shows that raw sentiment scores and star ratings mostly agree, but sentiment analysis using simple lexicon-based tools should be interpreted with caution, especially for negative reviews. Combining sentiment analysis with actual rating data (rather than trusting either alone) gives a more reliable picture of customer satisfaction.

## 📁 Project Structure
```
CodeAlpha_DataAnalytics/
├── data/
│   └── 1429_1.csv
├── notebooks/
│   └── analysis.ipynb
├── visuals/
│   └── (exported chart images)
├── README.md
└── requirements.txt
```

## ▶️ How to Run
1. Clone this repository
2. Open `notebooks/analysis.ipynb` in Google Colab or Jupyter
3. Install dependencies: `pip install pandas matplotlib seaborn textblob`
4. Run all cells in order

## 🙋 Author
Pravallika

---
*This project was built for educational and portfolio purposes as part of the CodeAlpha internship program.*

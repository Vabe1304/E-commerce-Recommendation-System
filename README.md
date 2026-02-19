# E-commerce-Recommendation-System
This project implements an end-to-end recommendation pipeline using the Kaggle dataset “Ecommerce Events History in Electronics Store”. It integrates exploratory analysis, feature engineering, content-based similarity modeling, and unsupervised learning to extract behavioral insights and generate product recommendations.

Dataset source: Kaggle
Distributed processing framework: Apache Spark (PySpark MLlib)

🎯 Problem Statement

Modern digital platforms rely on recommendation systems to improve personalization, conversion rates, and retention.

This project aims to:

Analyze user interaction patterns (view → cart → purchase)

Identify high-performing products and brands

Engineer scalable product representations

Compute similarity-based recommendations

Segment behavioral interaction patterns using clustering

📦 Dataset

The dataset contains event-level logs from an electronics e-commerce store, including:

event_type (view, cart, purchase)

product_id

category

brand

price

user_id

event_time

To reduce sparsity and improve modeling reliability, users with fewer than three interactions were filtered out.

🧹 Data Engineering & Preprocessing
Cleaning & Validation

Removal of null values

Standardization of categorical variables

Memory optimization

User interaction threshold filtering

Feature Engineering (PySpark ML)

StringIndexer for categorical indexing

OneHotEncoder for category, brand, and item encoding

MinMaxScaler for price normalization

VectorAssembler to construct dense feature vectors

Products are aggregated at the product_id level using:

Most frequent categorical attributes

Average price

🤖 Content-Based Recommendation

Each product is represented as a feature vector composed of:

Encoded category

Encoded brand

Normalized average price

Cosine similarity is computed between a target product and the product space to retrieve similar items.

Optional filtering excludes:

The target product itself

Products from the same brand (to increase diversity)

This produces a scalable content-based recommendation engine.

📊 Behavioral Segmentation (Unsupervised Learning)

A K-Means clustering model was trained using:

Encoded categorical features

Scaled numerical features (price, interaction day)

Configuration:

k = 13

Evaluated using Silhouette Score

This enables segmentation of interaction behavior and identification of latent engagement structures.

📁 Key Outputs

Top-selling products analysis

Purchase funnel validation

Brand-level performance insights

Similarity-based product recommendations

Cluster assignments for behavioral segmentation

Exportable CSV files for BI dashboards (Looker Studio compatible)

🛠 Technical Stack

Python

Pandas

Matplotlib / Seaborn

PySpark (MLlib)

K-Means clustering

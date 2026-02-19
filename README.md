# E-commerce Recommendation System

## Overview
This project implements an end-to-end recommendation pipeline using the Kaggle dataset  
**“Ecommerce Events History in Electronics Store.”**

It integrates:

- Exploratory Data Analysis (EDA)
- Feature Engineering
- Content-Based Similarity Modeling
- Unsupervised Learning (Clustering)

The goal is to extract behavioral insights and generate scalable product recommendations.

---

## Dataset & Infrastructure

**Dataset Source:** Kaggle  
**Distributed Framework:** Apache Spark (PySpark MLlib)

---

## 🎯 Problem Statement

Modern digital platforms rely on recommendation systems to improve:

- Personalization
- Conversion rates
- User retention

This project focuses on:

- Analyzing user interaction patterns (view → cart → purchase)
- Identifying high-performing products and brands
- Engineering scalable product representations
- Computing similarity-based recommendations
- Segmenting behavioral interaction patterns using clustering

---

## 📦 Dataset Description

The dataset contains event-level logs from an electronics e-commerce store:

- `event_type` (view, cart, purchase)
- `product_id`
- `category`
- `brand`
- `price`
- `user_id`
- `event_time`

To reduce sparsity and improve reliability, users with fewer than **3 interactions** were filtered out.

---

## 🧹 Data Engineering & Preprocessing

### Cleaning & Validation
- Removal of null values
- Standardization of categorical variables
- Memory optimization
- User interaction threshold filtering

### Feature Engineering (PySpark ML)
- `StringIndexer` → categorical indexing
- `OneHotEncoder` → encoding category, brand, and item
- `MinMaxScaler` → price normalization
- `VectorAssembler` → dense feature vector construction

Products are aggregated at the `product_id` level using:
- Most frequent categorical attributes
- Average price

---

## 🤖 Content-Based Recommendation

Each product is represented by a feature vector composed of:

- Encoded category
- Encoded brand
- Normalized average price

Cosine similarity is computed between a target product and all other products to retrieve similar items.

Optional filtering excludes:
- The target product itself
- Products from the same brand (to increase diversity)

This results in a scalable content-based recommendation engine.

---

## 📊 Behavioral Segmentation (Unsupervised Learning)

A K-Means clustering model was trained using:

- Encoded categorical features
- Scaled numerical features (price, interaction day)

**Configuration:**
- `k = 13`
- Evaluation metric: Silhouette Score

This enables behavioral segmentation and identification of latent engagement patterns.

---

## 📁 Key Outputs

- Top-selling products analysis
- Purchase funnel validation
- Brand-level performance insights
- Similarity-based product recommendations
- Cluster assignments
- Exportable CSV files for BI dashboards (Looker Studio compatible)

---

## 🛠 Technical Stack

- Python
- Pandas
- Matplotlib
- Seaborn
- PySpark (MLlib)
- K-Means Clustering

Matplotlib / Seaborn

PySpark (MLlib)

K-Means clustering

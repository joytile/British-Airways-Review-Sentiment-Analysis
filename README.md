# British Airways Review Sentiment Analysis ✈️


![GitHub](https://img.shields.io/badge/Language-Python-blue)
![GitHub](https://img.shields.io/badge/Model-Vader-purple)
![GitHub](https://img.shields.io/badge/Library-HuggingFace-Green)

## Project Overview

Analyze 3,500+ British Airways passenger reviews using **Zero-Shot Classification**, **Sentiment Analysis**, and a **rule-based fallback system** to uncover actionable business insights.

## 📌 Objective

To extract meaningful patterns from unstructured customer reviews that help British Airways:

- Identify recurring pain points (e.g., delays, seating, food)
- Measure customer sentiment by service category
- Highlight opportunities to improve operations and customer satisfaction

## 💡 Key Business Questions

This project aims to answer:

- **What are the most commonly mentioned service areas?**
- **How do customers feel about specific aspects like customer service, food, or Wi-Fi?**
- **Which categories (e.g., ‘flight delay’) are most associated with negative sentiment?**
- **Are customer complaints driven more by people (staff) or systems (delays, check-in)?**
- **How does sentiment differ across service categories?**

## 📂 Data

- Source: British Airways review dataset scraped from Skytrax (anonymized, 3,000+ reviews)
- Format: Raw text reviews in CSV

## 🧩 Key Findings

| Review Snippet | customer service | flight delay | in-flight meal | ... |
|----------------|------------------|---------------|----------------|-----|
| "The staff was rude and unhelpful" | 1 | 0 | 0 | ... |
| "Delayed for 2 hours, no Wi-Fi"    | 0 | 1 | 0 | ... |


## 📊 Sample Visualizations

- 📌 **Frequent Categories**
![Category Count](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/cat_count.png)
  
- 📊 **Sentiment Distribution**: Per category
- 🧮 **Category Co-occurrence Matrix**
![Co-occurence Matrix](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/co-occurence%20matrix.png)
---

## 🛠️ Methodology

### 1. Data Preprocessing
- **Text Cleaning**: Changing text case to lower case and removing special characters.
- **Tokenization**: Breaking the reviews into individual words.
- **Stopword Removal**: Removing unimmportant words that don't add value to the model e.g and, or, up, down, etc.
- **Lemmatization**: Reducing words to theeir basic form e.g seating -> seat.

### 2. Topic Modelling
This is a 2-step assignment of categories to the reviews. Multiple categories can be assigned to a single review.
- 🔍 **Zero-Shot Multi-Label Classification** via `facebook/bart-large-mnli` with a custom label list
  `["customer service", "flight delay", "in-flight meal", "seating", "entertainment options", "wifi availability", "check-in process", "luggage"]`
- 🧠 **Rule-Based Fallback**: Keyword-based pattern matching in the custsomer reviews. For cases where no category meets the specified threshold, the fallback function is triggered.

### 3. Sentiment Analysis
- 💬 **Sentiment Analysis** using Vader
- 💬 **Sentiment Analysis** using RoBERTa


---

## 🧠 Tools & Libraries

- [Transformers (Hugging Face)](https://huggingface.co/)
- `facebook/bart-large-mnli` for classification
- `pandas`, `matplotlib`, `seaborn` for analysis and plotting
- `re`, `scikit-learn`, `tqdm` for utilities

---

## 🔭 Future
- Add new categories
- Dashboard with filters
- Track trends over time

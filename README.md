# British Airways Review Sentiment Analysis ✈️


![GitHub](https://img.shields.io/badge/Language-Python-blue)
![GitHub](https://img.shields.io/badge/Model-RoBERTa-purple)
![GitHub](https://img.shields.io/badge/Library-HuggingFace-Green)

## Project Overview

Analyze 3,500+ British Airways passenger reviews using **Zero-Shot Classification**, **Sentiment Analysis**, and a **rule-based fallback system** to uncover actionable business insights.

![Sentiment Distribution](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/Sentiment%20distribution.png)
## Objective 📌

To extract meaningful patterns from unstructured customer reviews that help British Airways:

- Identify recurring pain points (e.g., delays, seating, food)
- Measure customer sentiment by service category
- Highlight opportunities to improve operations and customer satisfaction

## Key Business Questions 💡

This project aims to answer:

- **What are the most commonly mentioned service areas?**
- **How do customers feel about specific aspects like customer service, food, or Wi-Fi?**
- **Which categories (e.g., ‘flight delay’) are most associated with negative sentiment?**
- **Are customer complaints driven more by people (staff) or systems (delays, check-in)?**

## Data 📂

- Source: British Airways review dataset scraped from Skytrax (anonymized, 3,000+ reviews)
- Format: Raw text reviews in CSV

---

## Key Findings 🧩

### Sample Output
| Review      Snippet | customer    service | flight    delay | in-flight    meal | ... |
|--------------------|----------------------|-----------------|-------------------|-----|
| "The service was rude, full of attitude to me, the food is poorly serviced" | 1 | 0 | 1 | ... |
| "BA continues to get its mojo back starting with a classy lounge serving innovative, and interesting, quality pre-flight food"    | 0 | 0 | 1 | ... |

- **Frequent Categories**: Reviews about customer service, overall flight experience and seat comfort had the highest numbers
  
![Category Count](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/cat_count.png)
  
- **Sentiment Distribution**: Most reviews were negative (54%). Per category, customer service had the highest number of negative reviews.
  - Top complaints:
    - Customer service
    - Flight disruptions (delays, cancellations)
    - Seat comfort

  ![Sentdistbycat](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/Sentiment%20Distribution%20by%20category.png)
- **Category Co-occurrence Matrix**: Most reviews about customer service also touched on overall flight experience indicating that the interactions between customers and cabin crew is crucial for customer satisfaction.

![Co-occurence Matrix](https://github.com/joytile/British-Airways-Review-Sentiment-Analysis/blob/main/co-occurence%20matrix.png)

- Model Performance:
  - Roberta performed better in terms of understanding complex reviews and correctly assigning scores.
---

## Methodology 🛠️ 

### 1. Data Preprocessing
- **Text Cleaning**: Changing text case to lower case and removing special characters.
- **Tokenization**: Breaking the reviews into individual words.
- **Stopword Removal**: Removing unimportant words that don't add value to the model e.g and, or, up, down, etc.
- **Lemmatization**: Reducing words to their basic form e.g seating -> seat.

### 2. Topic Modelling
This is a 2-step assignment of categories to the reviews. Multiple categories can be assigned to a single review.
- 🔍 **Zero-Shot Multi-Label Classification** via `facebook/bart-large-mnli` with a custom label list
  `["customer service", "flight delay", "in-flight meal", "seating", "entertainment options", "wifi availability", "check-in process", "luggage"]`
- 🧠 **Rule-Based Fallback**: Keyword-based pattern matching in the customer reviews. For cases where no category meets the specified threshold, the fallback function is triggered.

### 3. Sentiment Analysis
- 💬 **Sentiment Analysis** using Vader
  - Lexicon improved by customizing with airline-focused lexicon e.g 'rude staff', 'comfortable seats' etc
  - Assigns scores across positive, negative, neutral and compound.
- 💬 **Sentiment Analysis** using RoBERTa
  - A transformer model, cardiffnlp/twitter-roberta-base-sentiment
  - Better at analyzing complex sentiments
  - Returns scores for positive, negative and neutral sentiments.
 
### 4. Model Comparison
- Comparative analysis betweeen Roberta and Vader models

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

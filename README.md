
# Amazon Reviews NLP Analysis Pipeline

# Sentiment and Topic Analysis of Amazon Product Reviews using NLP

## Project Overview
This project builds an end-to-end NLP pipeline to analyze sentiment and extract themes from 5,000+ Amazon product reviews. It compares rule-based and transformer-based sentiment models and uses topic modeling and clustering to uncover meaningful patterns in customer feedback.

## Methods
- VADER (rule-based sentiment analysis)
- Transformer-based sentiment model (BERT)
- BERTopic for topic modeling
- Sentence-transformer embeddings
- KMeans clustering

## Key Findings
- Transformer models produce more extreme sentiment predictions compared to VADER
- VADER tends to assign more positive sentiment to neutral or mildly negative reviews
- Product reviews naturally cluster into domain-specific categories (electronics, apparel, books, media)
- Sentiment varies significantly across clusters, indicating domain-dependent perception

## Tech Stack
Python, HuggingFace, NLTK, Sentence-Transformers, BERTopic, Scikit-learn

## Dataset
- **Source:** Amazon Polarity Dataset  
- Binary labels:
  - `0 → Negative`
  - `1 → Positive`
- Subset used: **5000 samples**






# Results & Analysis

## 1. Ground Truth Distribution
- Slight class imbalance:
  - Negative ≈ **2700**
  - Positive ≈ **2300**

**Interpretation:**
- Dataset is fairly balanced → reliable evaluation  
- No heavy bias toward a single class  



## 2. VADER Sentiment Distribution
- Continuous distribution across [-1, 1]  
- Strong density near **high positive scores (~0.8–1.0)**  
- Also spread across negative region  

**Insight:**
- Produces smooth sentiment scores  
- Tends to **overestimate positivity**  
- Struggles with contextual nuance  


## 3. Transformer Sentiment Distribution
- Highly **bimodal**:
  - Peaks near **-1 and +1**

**Insight:**
- High confidence predictions  
- Behaves like a strong classifier  
- Better captures context and semantics  


## 4. Sentiment Difference (VADER vs Transformer)

Definition:

Gap = Transformer Score - VADER Score


**Observations:**
- Centered near 0  
- Heavy tails on both sides  
- More mass in negative gap  

**Interpretation:**
- VADER often **more positive than transformer**  
- Transformer corrects:
  - Sarcasm  
  - Complex phrasing  
  - Mixed sentiment  


## 5. Topic Modeling (BERTopic)

### Discovered Themes:

| Topic | Theme |
|------|------|
| 0 | Music (album, songs, band) |
| 1 | Home products (bed, mattress) |
| 2 | Electronics (charger, adapter) |
| 3 | Books & reading |
| 4 | Clothing fit (size, waist) |
| 5 | Movies & media |
| 6 | DVDs / Blu-ray |
| 7 | Footwear (boots, shoes) |
| 8 | Writing/story |
| 9 | Audio devices (mp3, battery) |

**Insight:**
- Topics are **clean and interpretable**  
- Model captures **real product categories**  


## 6. Clustering Performance

- Method: KMeans  
- Best K = **4**  
- Silhouette Score ≈ **0.062**

**Interpretation:**
- Clusters exist but are **weakly separated**  
- Expected due to:
  - High-dimensional embeddings  
  - Overlapping semantic content  

**Meaning:**
- Useful for grouping trends  
- Not for strict segmentation  






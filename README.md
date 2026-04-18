
# Amazon Reviews NLP Analysis Pipeline

## Overview
This project implements an end-to-end **Natural Language Processing (NLP) pipeline** to analyze customer reviews using:

- Rule-based sentiment analysis  
- Transformer-based models  
- Sentence embeddings  
- Topic modeling  
- Clustering  

The objective is to move beyond basic sentiment classification and extract **semantic structure + actionable insights** from text data.



## Dataset
- **Source:** Amazon Polarity Dataset  
- Binary labels:
  - `0 → Negative`
  - `1 → Positive`
- Subset used: **5000 samples**



# Pipeline

## 1. Preprocessing
- Lowercasing  
- Removing punctuation, URLs  
- Stopword removal  



## 2. Sentiment Models

### Rule-Based
- VADER Sentiment Analyzer  

### Transformer
- DistilBERT (fine-tuned for sentiment analysis)  



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


# Key Insights

### 1. Model Behavior
- VADER → smooth, biased toward positivity  
- Transformer → confident, context-aware  


### 2. Semantic Structure
- Topics reveal clear product categories  
- Embeddings capture meaningful relationships  


### 3. Clustering Reality
- Weak separation is natural in text data  
- Still useful for aggregation and trend discovery  





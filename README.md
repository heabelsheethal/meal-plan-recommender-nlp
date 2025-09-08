# Meal Plan Recommender NLP

**Personalized weekly meal plan recommender using NLP, LDA, and BERT**

---

## Project Overview
Meal planning can be time-consuming and overwhelming. This project builds a **recommender system** that generates weekly meal plans based on:

- User cuisine preferences
- Dietary restrictions
- Available cooking time

Users complete a quiz, and the system provides a **curated weekly meal plan** along with a **shopping list**.

---

## Folder Structure

```text
meal-plan-recommender-nlp/
│
├── README.md
├── LICENSE
├── Data/
│   ├── RecipeNLG_subset.csv  
│   └── README.md  (Instructions for downloading full dataset)
├── Notebooks/
│   ├── 00 Final_combined_workflow.ipynb
│   ├── 1_Text_preprocessing.ipynb
│   ├── 2_Feature_engineering.ipynb
│   ├── 3_LDA_and_recommendation.ipynb
│   ├── 4_Shopping_list.ipynb
│   ├── 5_Hybrid_summarization.ipynb
│   └── 6_Flask_integration.ipynb
├── Summary Slides/
│   ├── 01_title.png
│   ├── 02_Problem_Definition.png
│   ├── 03_Data_Source.png
│   ├── 04_Design_Structure.png
│   ├── 05_Design_flow1.png
│   ├── 06_Design_flow2.png
│   ├── 07_Design_choices_and_rationale.png
│   ├── 08_Evaluation_Criteria.png
│   ├── 09_Findings_and_Conclusions1.png
│   ├── 10_Findings_and_Conclusions2.png
│   └── 11_Findings_and_Conclusions3.png
├── requirements.txt
```

---

## Key Features & Design

### 1. Data Preprocessing & Feature Engineering
- **Dataset:** RecipeNLG dataset (2.29 GB, structured JSON).  
- **Deduplication:** Removed duplicate recipes using **SimHash** and **MinHash LSH**.  
- **Text Cleaning:** Tokenization, lowercasing, punctuation removal, stopword removal using **NLTK & spaCy**.  
- **Feature Engineering:**  
  - Extracted cooking time from directions.  
  - Tagged cuisines and dietary restrictions using **keywords & NER**.  
  - Created full-text fields for embeddings.  

### 2. LDA Topic Modeling
- Clustered recipes into ~10 coherent topics (e.g., "baked desserts", "fried dishes").  
- Topic assignments used to recommend similar recipes.  

### 3. Recommendation System (Weighted Ensemble Model)
- **Input:** User quiz capturing cuisine preferences, diet restrictions, available cooking time, and recipe selections from sample topics.  
- **Process:**  
  - Encodes user query and recipes using **Sentence-BERT embeddings**.  
  - Computes **cosine similarity** to find relevant recipes.  
  - Scores ingredient overlap, cuisine/diet matches, topic similarity, and cooking time.  
  - Weighted scoring:  
    - 45% Semantic similarity  
    - 20% Ingredients overlap  
    - 15% Diet & Cuisine tags  
    - 10% LDA topic match  
    - 10% Normalized cooking time  
- **Output:** Top-N recipe recommendations that best match user preferences.  

### 4. Shopping List Generation
- Compiles all ingredients from recommended recipes into a **consolidated shopping list**.  
- Handles quantity normalization and deduplication for practical use.

### 5. Abstractive Summarization
- Generates **weekly meal plan previews** using **BART transformer**.  
- Applied template fallback and cleanup for coherent, human-readable summaries.  

### 6. Flask Web Interface
- Interactive **web app** to:  
  - Display weekly meal plan  
  - View full recipes  
  - Generate shopping lists automatically
  - Provide human-readable summaries
    
---

## Evaluation Metrics
**Quantitative Metrics:**  
- **Recommendation System:**
-   Precision@10: 0.68
-   Recall@10: 0.453   
- **Abstractive Summarization:**
-   ROUGE-1/L: 0.462
-   BERT F1: 0.885 

**Qualitative Metrics:**  
- User satisfaction with the accuracy of recommendations to preferences. 

---

## Technologies Used
- **Python 3.9+**
- **Jupyter Notebook / Google Colab** – Prototyping and development
- **NLTK & spaCy** – Text cleaning, tokenization, NER  
- **pandas & numpy** – Data manipulation and numerical operations
- **Gensim** – LDA topic modeling, Word2Vec embeddings  
- **scikit-learn** – Similarity calculations and evaluation metrics  
- **Sentence-BERT** – Semantic embeddings for recommendation (Encoder model) 
- **BART Transformer** – Abstractive summarization (Encoder-Decoder model) 
- **SimHash & MinHash LSH** – Deduplication of recipes  
- **regex (re module) & fractions** – Text extraction and ingredient quantity handling
- **Flask** – Web interface backend
- **HTML & CSS** – Web interface frontend  
- **Bootstrap** – Responsive design and styling

---

## Challenges & Solutions
- Large dataset (~2.3 GB) → ran preprocessing in **Google Colab** to avoid memory issues.  
- Rare cuisines/diets → synthetic ground truth used for evaluation.  
- Summarization outputs → post-processing and template fallback applied.  
- Interface Unicode & port issues → resolved with Flask and careful encoding.  

---

## Acknowledgements
Special thanks to my colleagues who contributed ideas and provided guidance:
- Amy Yeh
- Ayu Vidiantiwi
- Celine Widjaja
- Ria Chhabra

---


 

# Data Folder

This folder contains the datasets used in the **Meal Plan Recommender NLP** project.

## Dataset Used

### RecipeNLG Dataset
- **Description:** Largest publicly available collection of recipe data (2.29 GB).  
- **Provided by:** Poznan University of Technology (PUT).  
- **Purpose:** Structured and cleaned for NLP tasks and recommender system development.  

### Key Features
- **Title** – Name of the recipe  
- **Ingredients** – List of ingredients for the recipe  
- **Directions** – Step-by-step cooking instructions  
- **Link** – Reference URL if available  
- **Source** – Original source of the recipe  
- **NER (Named Entity Recognition)** – Extracted entities like ingredient names, cooking tools, etc.  
- **Procurement** – Information relevant for shopping list generation  

- **Availability:** Freely available for research and educational use.  
- **Dataset Link:** [RecipeNLG Dataset](https://recipenlg.cs.put.poznan.pl/dataset)

### Why This Dataset?
- Scalable for building **recommender systems**  
- Supports NLP tasks such as **LDA topic modeling, keyword detection, and summarization**  

### Usage Notes
- The `RecipeNLG_subset.csv` file in this folder is a smaller subset for **development and testing**.  
- Notebooks reference datasets using relative paths, e.g., `Data/RecipeNLG_subset.csv`.  
- To work with the full dataset, download it from the link above and place it in this folder.

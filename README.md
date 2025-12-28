# Code Complexity Classifier

## Overview
This project explores whether short Python code snippets can be classified as **overengineered** using simple, interpretable structural features and a machine learning model.

Rather than evaluating correctness or performance, the focus is on identifying structural patterns that often correlate with unnecessary complexity.

---

## Motivation
Overengineering is a common but subjective concept in software development.  
This project investigates the question:

> *Can a machine learning model detect overengineered code using only basic structural signals?*

To keep the analysis transparent and explainable, the project avoids complex NLP techniques and instead relies on intuitive features derived directly from the code.

---

## Dataset
The dataset consists of labeled Python code snippets categorized as:
- **Simple**
- **Reasonable**
- **Overengineered**

Each snippet is short and self-contained.  
Labels are subjective and reflect human judgment rather than formal complexity metrics.

---

## Feature Engineering
Each code snippet is converted into a small set of numeric features that approximate structural complexity:

- **Number of function definitions**
- **Number of class definitions**
- **Average line length**

The feature set was intentionally kept minimal and interpretable to:
- reduce overfitting on a limited dataset
- improve model explainability
- make results easier to reason about

---

## Problem Formulation
The task was initially framed as a **multiclass classification** problem.

However, due to:
- class imbalance
- overlap between subjective categories

the problem was reframed as a **binary classification task**:

- **Overengineered**
- **Not Overengineered** (Simple + Reasonable)

This reformulation improved model stability and interpretability.

---

## Model
A **Random Forest classifier** was trained using the extracted features.

- Train/test split: 80/20 (stratified)
- Model choice prioritizes robustness and interpretability over complexity

---

## Results
The final binary classifier achieved:

- **~86% accuracy** on held-out test data
- High precision for identifying non-overengineered code
- Reasonable recall for detecting overengineered snippets despite limited data

Feature importance analysis showed that **class and function usage** were the strongest indicators of overengineering.

---

## Limitations
- Small, subjective dataset
- Labels reflect human judgment rather than formal definitions
- Does not analyze semantic correctness or runtime complexity

Results should be interpreted as exploratory rather than definitive.

---

## Future Work
Possible extensions include:
- Expanding the dataset
- Adding nesting or indentation-based features
- Comparing against simpler linear models
- Exploring lightweight NLP-based features

---

## How to Run
1. Clone the repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt

# Analysis of Nuclear Safety Reports Using NLP

## Project Overview

This project aims to utilize Natural Language Processing (NLP) techniques to automatically extract valuable information from lengthy nuclear safety reports, specifically from the Diablo Canyon Independent Safety Committee (DCISC) reports. The goal is to classify extracted paragraphs according to associated safety traits to better understand and improve safety culture in nuclear and aviation industries.

## Problem Statement

- **Safety Culture in Nuclear and Aviation Incidents:** Many nuclear and aviation incidents arise from safety culture problems. The complexity of safety reports makes manual extraction of meaningful data extremely challenging.
- **Lengthy Safety Reports:** Reports often exceed 900 pages, making it difficult to extract and analyze relevant information manually.
- **Need for NLP:** NLP techniques are used to automatically extract and classify valuable information to identify safety culture issues from the reports.

## Primary Data Sources

- **Reports Used:** DCISC 24th (2014) and 32nd (2022) Annual Reports
- **Safety Traits:** Personal Accountability, Questioning Attitude, Effective Safety Communication, Leadership Safety Values, Decision-Making, Respectful Work Environment, Continuous Learning, Problem Identification, Environment for Raising Concerns, Work Processes

## Project Objectives

1. Automatically extract valuable paragraphs from DCISC reports.
2. Classify the extracted paragraphs by their associated safety traits.

### Example:
**Root Cause (from DCISC 24th Annual Report, 2014)**  
_"Leaders are not consistently setting, modeling, and reinforcing clear standards and expectations for conservative decision-making, resulting in a station culture that favors production-oriented interpretation of the license basis."_  
**Associated Safety Traits:** Leadership Safety Values and Actions, Decision-Making, Work Processes

## Dataset

- **Gold Standard Dataset:** The team manually labeled ~65 paragraphs from the DCISC reports with the relevant safety traits for evaluation. Multiple reviewers ensured data accuracy.
- **Labeling Method:** The team used the INPO booklet for reference, summarized paragraphs, and identified keywords.

## Exploration of Algorithms

Several algorithms were explored to extract and classify safety traits:
- **Rule-Based:** Uses predefined rules to classify extracted aspects based on cosine similarity with seed words.
- **Semi-Supervised Learning:** Labels sentences based on similarity to labeled vectors (label vectors).
- **Unsupervised Learning:** Uses techniques like Latent Dirichlet Allocation (LDA) for probabilistic text clustering.
- **BERT Iterative Model:** An attempt to train and label data using BERT, though faced issues like overfitting and catastrophic forgetting.

## Approach: Guided LDA (Latent Dirichlet Allocation)

The main technique used in this project is **Guided LDA**, a probabilistic text clustering algorithm. This model helps classify paragraphs based on a list of seed words associated with safety traits.

### Certificate:

![image](https://github.com/user-attachments/assets/4db63f91-c4f6-4a7a-a06c-8e3b881f5383)

### Steps:
1. **Input:** Extracted paragraphs and a list of words associated with each safety trait.
2. **Process:** The Guided LDA model generates topic distributions from the paragraphs.
3. **Output:** The model produces a list of likely topics (safety traits) based on topic distribution probabilities.

## Results

**Aggregated Probabilities:**
- Personal Accountability: 0.0027
- Effective Safety Communication: 0.1794
- Leadership Safety Values and Actions: 0.2636
- Continuous Learning: 0.2566
- Problem Identification & Resolution: 0.2194
- Work Processes: 0.0676

**Likely Traits:** Continuous Learning, Leadership Safety Values and Actions, Problem Identification and Resolution  
**Actual Traits:** Leadership Safety Values and Actions, Problem Identification and Resolution, Work Processes

**Metrics:**
- **Accuracy:** 0.50
- **Precision:** 0.67
- **Recall:** 0.67
- **F1-Score:** 0.67

## Future Work

- **Refining Seed Words:** Improving the list of seed words for better accuracy.
- **Improving Pre-Processing:** Enhancing text pre-processing methods for better data quality.
- **Increasing Data Size:** Expanding the dataset for training and testing.
- **Evaluating Negative Text:** Investigating the evaluation of negative sentiments in text to improve trait classification.
- **Model Generalization:** Adapting the model to handle other types of documents.

## Model Evaluation on Gold Standard

- **Average Accuracy on Test Data:** 33.48%
- **Average Precision on Test Data:** 42.87%
- **Average Recall on Test Data:** 55.15%
- **Average F1-Score on Test Data:** 48.3%

## Installation

To run the project locally, follow these steps:

### 1. Clone the Repository
```bash
git clone https://github.com/AbhishekyPhalak/Nuclear-Safety-Reports-NLP.git

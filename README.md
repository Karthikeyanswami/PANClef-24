# Oppositional Thinking Analysis: Conspiracy Theories vs. Critical Thinking Narratives

## Overview

This repository contains the solution developed by **Team Kaprov** for the **PAN @ CLEF 2024** shared task on **Oppositional Thinking Analysis**. The task focuses on distinguishing between two nuanced forms of oppositional discourse:  
- **Conspiracy narratives**: which imply secret, malicious plots by powerful groups  
- **Critical thinking**: which challenges dominant narratives through objective reasoning  

The classification is challenging due to the subtle differences in language and intent. Misclassifying critical discourse as conspiratorial can have serious societal consequences, hence the need for high-accuracy models.

---

## Task Description

The task consists of two subtasks:

### Subtask 1: Text-Level Binary Classification
- **Goal**: Determine whether an entire text is a conspiracy theory or a critical thinking narrative.

### Subtask 2: Span-Level Multi-Label Classification
- **Goal**: Identify spans in the text that correspond to either conspiracy or critical thinking cues.

---

## Solution Approach

### Subtask 1: Binary Classification

- **Model Used**: Pretrained `bert-base-uncased`  
- **Architecture**:  
  - BERT model with a classification head  
  - A **sigmoid activation function** at the output layer  
- **Input**: Full narrative text  
- **Output**: Binary label — `Conspiracy` (1) or `Critical Thinking` (0)  
- **Loss Function**: Binary Cross-Entropy Loss  
- **Training**:
  - Fine-tuned on the labeled dataset provided by PAN
  - Early stopping and model checkpointing based on validation F1 score

### Subtask 2: Span-Level Multi-Label Classification

- **Model Used**: Fine-tuned BERT-based sequence classifier  
- **Architecture**:
  - Token-level classification model  
  - Multi-label setup (tokens can belong to both, either, or none)
- **Input**: Tokenized text  
- **Output**: For each token, one or more labels: `Conspiracy`, `Critical Thinking`, or `None`
- **Loss Function**: Binary Cross-Entropy with Logits  
- **Post-processing**:
  - Spans are extracted by grouping consecutive tokens with the same label
  - Overlapping spans are merged when necessary

---

## Evaluation

- **Metrics**:
  - **Precision**, **Recall**, and **F1-score** for both subtasks
  - Span-level accuracy and partial match metrics for Subtask 2

- **Results**:
  - Detailed evaluation metrics to be shared upon final release of PAN 2024 results.

---

## Prerequisites

- Python 3.8+
- PyTorch
- HuggingFace Transformers
- scikit-learn
- pandas

---



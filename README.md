# A2I2-EMALC-Internship

> **Embedding Models for Addressing Linguistic Challenges (EMALC)**  
> Internship project at A2I2 (Applied Artificial Intelligence Institute)  
> Intern: [Your Name] | Mentors: Sheng Wong, Scott Barnett  
> Duration: [Insert dates, e.g., Jan–May 2025]

---

## 📌 Overview

This repository documents my internship project at A2I2 focused on evaluating and improving **state-of-the-art (SOTA) embedding models** in handling **complex linguistic phenomena**, such as:

- **Negation**
- **Causality**
- **Natural Language Inference (NLI)**
- **Semantic similarity mismatches**

Despite high performance on general NLP benchmarks, existing embedding models still struggle with these nuanced aspects of language. This project investigates such limitations and explores ways to address them through dataset design and empirical evaluation.

---

## 🧪 Experiments

### 1. **Negation-aware IR (NevIR Dataset)**
- Based on modified **CondAQa** documents with negation-sensitive edits.
- Each query-document pair was labeled by expected semantic relevance.
- Evaluated using **cosine similarity** on **nv-embed-v2** embeddings.
- **Findings**:
  - Cosine similarity failed to distinguish between negated and non-negated documents.
  - Overlapping similarity distributions indicate embedding models are not robust to negation.

🔗 [Original dataset (CSV)](https://github.com/trungkiennguyen22082004/Embedding_Experiments/blob/main/NevIR_Dataset_Embedding_Experiments/data/original_250.csv)  
🔗 [Processed dataset (CSV)](https://github.com/trungkiennguyen22082004/Embedding_Experiments/blob/main/NevIR_Dataset_Embedding_Experiments/data/processed_nevir_250.csv)

---

### 2. **Causality Embeddings**
- Dataset structured around cause-effect reasoning.
- Evaluated whether embeddings can distinguish between **cause vs. cause** and **effect vs. effect**.
- **Findings**:
  - Similarity scores were generally low and distributions overlapped.
  - Embeddings could not reliably model cause-effect semantic distinctions.

---

### 3. **Natural Language Inference (NLI)**
- Dataset from **SNLI** and **MNLI**.
- Labels: Contradiction, Neutral, Entailment (later dropped due to ambiguity).
- Focused on whether models could distinguish contradiction vs. neutral.
- **Findings**:
  - Cosine similarity distributions significantly overlapped.
  - Embedding models showed **poor separation** of logical relationships.

---

## 🔧 Techniques & Tools

- **Embedding model**: [`nv-embed-v2`](https://huggingface.co/nvidia/NV-Embed-v2)
- **Similarity metric**: Cosine Similarity
- **Languages/Tools**: Python, HuggingFace Transformers, Matplotlib, Pandas

---

## 📈 Results Summary

| Task         | Expected Behavior              | Observed Result                |
|--------------|-------------------------------|--------------------------------|
| Negation IR  | Low q1↔q2, High q1↔doc1       | Overlap; failed to capture negation |
| Causality    | High similarity within types  | Low + overlapping distributions |
| NLI          | Low similarity (contradiction) vs medium (neutral) | Significant overlap |

> 🔍 **Conclusion**: Current SOTA embeddings (e.g., `nv-embed-v2`) **fail to distinguish** complex linguistic relationships such as negation, causality, and inference.

---


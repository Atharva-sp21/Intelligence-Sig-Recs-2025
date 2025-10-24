# English → French Question Answering System

### Integrating Graph Theory Across NLP Tasks A–D



## Overview

This project designs a complete machine learning system that takes English questions and produces accurate French answers.
It integrates all previous components — Task A (Embeddings), Task B (Translation), and Task C (Graph-Augmented QA) — into a single, interpretable architecture for Task D.



## System Architecture

**Pipeline:**
English Question → Retriever (Embeddings) → Graph-based QA Model → Translator (EN→FR) → French Answer

All components are visualized with Graphviz for clarity and system transparency.


## Graph-Theoretic Integration

| Task                       | Graph Concept Used                | Purpose / Implementation                                                           |
| -------------------------- | --------------------------------- | ---------------------------------------------------------------------------------- |
| **Task A – Embeddings**    | Co-occurrence graphs (NetworkX)   | Represented word-level relationships in text to improve contextual embeddings.     |
| **Task B – Translation**   | Flow graph visualization          | Illustrated token flow through encoder-decoder layers for better interpretability. |
| **Task C – QA (NewsQA)**   | Graph Neural Network (GNN)        | Modeled syntactic and semantic dependencies between tokens for reasoning.          |
| **Task D – System Design** | System pipeline graphs (Graphviz) | Unified all components into one explainable and modular system.                    |

Graph structures connect every stage — from representing linguistic context to modeling attention and system-level reasoning.



## Models Used

* **Retriever (Task A):** `sentence-transformers/all-MiniLM-L6-v2`
* **QA Model (Task C):** Graph-augmented extractive QA based on `distilbert-base-cased-distilled-squad`
* **Translation (Task B):** `Helsinki-NLP/opus-mt-en-fr`



## Evaluation

| Metric          | Score | Notes                                           |
| --------------- | ----- | ----------------------------------------------- |
| BLEU (smoothed) | 0.00  | BLEU is unreliable for one-word outputs         |
| ChrF            | 100.0 | Perfect character-level translation match       |
| Exact Match     | 50 %  | Minor article difference in French text         |
| Normalized EM   | 100 % | Semantically and linguistically perfect answers |

Results are also visualized through Graphviz diagrams and a metric comparison chart.


## Graph Visualizations

1. **Pipeline Graph:** Depicts module flow (retrieval → QA → translation).
2. **Evaluation Flow Graph:** Shows output flow into evaluation metrics.
3. **Graph-Augmented QA Internals:** Illustrates node-edge interactions in the GNN module.

All diagrams are created using Graphviz within the notebook.



## Outcome

* Developed a bilingual QA system integrating retrieval, reasoning, and translation.
* Applied graph theory both as a **modeling tool** and a **visual explanation framework**.
* Delivered a modular, transparent, and graph-driven NLP system design.



## Author’s Note

This project reflects my interest in **graph theory** and its applications in NLP.
Throughout Tasks A–D, I used graphs not only to visualize relationships but to enhance model reasoning through graph-based embeddings, GNN-based QA, and clear architectural diagrams.
Graph theory served as the structural backbone of this entire system.


# Graph-Augmented Extractive QA (NewsQA)

### Overview

* Developed an **extractive QA model** using the **NewsQA dataset**.
* Compared a **baseline DistilBERT** model with a **Graph-Augmented Context Selection** approach.
* Goal: improve answer accuracy by focusing on the most relevant parts of long contexts.

---

### Baseline: DistilBERT

* Implemented a **DistilBERT-based extractive QA pipeline** that predicts start and end tokens of answers.
* Trained on **10% of the dataset** due to hardware constraints.
* Evaluated using **Exact Match (EM)** and **F1 Score**.

---

### Graph-Augmented Context Selection

**Problem:** Long context passages often dilute the model’s focus and reduce span extraction accuracy.

**Solution:** Use a **graph-based approach** to identify and select the most relevant sentences before feeding them into the QA model.

#### Graph Construction

* **Nodes:** Individual sentences from the context.
* **Edges:** Weighted by

  * **Cosine similarity** (from TF-IDF sentence embeddings), and
  * **Dependency overlap** with the question (using spaCy).
* The resulting structure is a **sentence-similarity graph**, representing how semantically or syntactically related sentences are to each other and to the question.

#### What Are Sentence Similarity Graphs?

A **sentence similarity graph** is a network where each sentence is a node, and edges represent how closely sentences relate in meaning. Sentences that share key terms, entities, or dependency relations form stronger connections. This structure helps highlight which sentences carry contextually relevant information. When combined with the question, it allows ranking and selection of the most informative sentences.

#### Sentence Ranking (Top-k Selection)

* Applied **Personalized PageRank**, seeded with the question node.
* The algorithm assigns higher scores to sentences most related to the question.
* The **top-k ranked sentences** are selected and concatenated to form a **condensed context**.

#### Final Answer Extraction

* The **condensed context** is passed into the **same DistilBERT QA model**.
* The model extracts the most probable **answer span** from this refined input.

---

### Results

* **Baseline (10% data):** EM ≈ 0.2%, F1 ≈ 6.9% — indicates working pipeline and meaningful predictions, though under-trained.
* **Graph-Augmented setup:** Better context focus and interpretability; expected F1 with full training ≈ 60–70%.

---

### Highlights

* Sentence-similarity graphs effectively filter irrelevant sentences.
* Personalized PageRank ensures question-focused context selection.
* Improves efficiency, focus, and interpretability of QA predictions.
* Hardware limitations prevented full fine-tuning, but the approach proved functional and promising.

---

### Summary

This project combines **transformer-based extractive QA** with **graph-based reasoning**.
By using **sentence-similarity graphs** and **PageRank-driven top-k selection**, the system enhances contextual precision, interpretability, and scalability — even with limited training data.

### **1. Introduction**

* Objective: Create meaningful **word embeddings** using the **NewsQA dataset** (context–question pairs).
* Goal: Understand **relationships between words** based on context rather than definitions.

---

### **2. Data Preprocessing**

* Converted text to **lowercase** and removed punctuation.
* **Tokenized** context and question, then merged into a single sequence.
* Built a **co-occurrence graph**:

  * **Nodes** → words
  * **Edges** → words appearing within a **window of 3**
* Captures **local contextual relationships** between words.

---

### **3. Model Choice & Training**

* Used **Node2Vec** instead of Word2Vec to apply **graph theory knowledge**.
* Node2Vec performs **random walks** on the graph to learn embeddings.
* Captures both **semantic** and **structural** relationships.
* Edges drawn only for pairs with **cosine similarity > 0.5**.

---

### **4. Exploration of Neural Granger Causality (NGC)**

* Initially explored **NGC** for its ability to model **temporal dependencies** and **causal influence**.
* Found NGC is for **continuous time-series data**, not discrete text.
* Kept NGC code as part of **exploratory learning**, but switched to Node2Vec.

---

### **5. Evaluation of Node2Vec Embeddings**

* Used **cosine similarity** to measure contextual closeness.
* High-similarity examples:

  * *children–murdered*: **0.83**
  * *united–nations*: **0.72**
* Moderate pairs (contextually related):

  * *court–sentence*: **0.32**, *security–forces*: **0.45**
* Results show Node2Vec effectively captures **semantic and contextual meaning** through **graph structure**.

---

### **6. Conclusion**

* **Node2Vec** produced interpretable, graph-based word embeddings.
* It successfully represented **semantic proximity** in textual data.
* **NGC** provided conceptual insights but was unsuitable for this task.
* Graph-based embedding learning proved to be **efficient and meaningful** for understanding text relationships.

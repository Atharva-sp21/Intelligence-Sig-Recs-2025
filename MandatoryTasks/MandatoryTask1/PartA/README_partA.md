1. Introduction

The goal of this task was to experiment with creating meaningful word embeddings using the NewsQA dataset, which contains context and question pairs extracted from real news articles. The objective was to understand how words relate to each other based on their usage and surrounding context rather than relying on direct definitions.

2. Data Preprocessing

The data was first cleaned by converting all text to lowercase, removing punctuation, and splitting both the context and question into individual tokens. The two sets of tokens were then combined to create a single list for each example. From this, I built a word co-occurrence graph, where each unique word was represented as a node, and edges were drawn between words appearing within a fixed window of three words. This graph effectively captures local relationships and provides an intuitive way to visualize how often and in what contexts words appear together.

3. Model Choice and Training

To learn numerical representations of these words, I trained a Node2Vec model on the co-occurrence graph. I chose Node2Vec over Word2Vec because it aligns well with my background and interest in **graph theory and geometric deep learning**. Node2Vec learns embeddings by exploring graph neighborhoods through random walks, allowing it to capture both structural and semantic relationships between words. The resulting embeddings were then evaluated using cosine similarity, and only words with similarity scores above 0.5 were connected in a directed visualization graph.

4. Exploration of Neural Granger Causality (NGC)

Initially, I also experimented with **Neural Granger Causality (NGC)**, as it models temporal dependencies and can identify causal relationships between variables. However, I later realized that NGC is designed for continuous time-series data and is regression-based, making it unsuitable for discrete textual data. I kept this section in my work to reflect my exploratory learning and to acknowledge the process of refining my approach based on new understanding.

5. Evaluation of Node2Vec Embeddings

Evaluating the **Node2Vec** embeddings showed a strong understanding of contextual and semantic relationships between words. By using cosine similarity, I was able to measure how closely related two word vectors were in the embedding space. Pairs such as “children–murdered” (0.83) and “united–nations” (0.72) achieved high similarity scores, indicating that the model successfully recognized meaningful associations frequently present in the dataset. For example, “children” and “murdered” often co-occurred in tragic news contexts, while “united” and “nations” naturally formed a strong conceptual link as part of a named entity.

Lower similarity values, like “court–sentence” (0.32) or “security–forces” (0.45), also provided useful insights. Although these words were thematically related, they appeared in broader or less consistent contexts, leading to weaker—but still relevant—connections. This variation in similarity scores demonstrated that Node2Vec embeddings could differentiate between strong, direct associations and looser, contextual ones.


6. Conclusion

Through this experiment, Node2Vec proved to be an effective approach for generating graph-based word embeddings. It successfully represented semantic relationships between words by leveraging their co-occurrence structure. While Neural Granger Causality provided valuable conceptual insights, Node2Vec emerged as the more suitable and interpretable method for text-based embedding generation.
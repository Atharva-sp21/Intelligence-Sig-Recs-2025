English → French Translation using Dependency Graphs
Objective

Developed a Transformer-based English–French translation model that integrates syntactic dependency graphs to enhance grammatical and contextual understanding in translation.

Method

Base Model: Helsinki-NLP/opus-mt-en-fr

Dataset: Opus Books (English–French)

Parser: spaCy dependency parser

Training: 10 epochs, learning rate 3e-5, batch size 32

Dependency trees were linearized into text sequences using:

[semantic relation] word child1 child2 ...


This preserved grammar and relationships between words while remaining Transformer-compatible.

Graph Neural Network Aspect

Inspired by Graph Neural Networks (GNNs), which represent data as nodes (words) and edges (relations).

Instead of directly implementing a GNN, a graph-informed linearization was used to embed syntactic structure within the Transformer input.

This approach maintained the benefits of graph reasoning while keeping model complexity low.

Results

Achieved high BLEU and similarity (ChrF) scores after only 10 epochs.

The syntax-aware preprocessing improved fluency, alignment, and semantic accuracy in translations.

Key Insights

Dependency graphs acted as a catalyst, giving the model a deeper understanding of sentence structure.

Combines linguistic structure with neural translation, leading to more coherent and accurate results.

Demonstrates how graph-inspired methods can enhance traditional sequence models effectively.
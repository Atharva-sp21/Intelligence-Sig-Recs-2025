# Semantic Dataset Comparison using Graph Based Similarity

## Overview

This project is about finding how similar two image datasets are, not just by pixels but by meaning. I used graphs made from image embeddings so it can understand what’s inside image and how it’s connected.

## Motivation

Normal similarity models just see color or pixels. I wanted something that understand relation between parts of image. That’s why I used **GIN**, a graph neural network that can read structure. It helps when two images look same in pieces but different in shape or layout.

## Method

* **Feature Extraction:** I used CLIP and ViT to get feature vectors from images.
* **Graph Building:** Each image becomes a graph. Nodes are features or regions, edges show if they appear together or nearby.
* **Models Used:**

  * **GINS:** checks if two graphs have same kind of features.
  * **GIN-S:** same as GINS but it also looks at structure and how nodes are connected.

## Experiments

1. **CIFAR-10 (Cat vs Dog, Car vs Truck):**

   * Cat and Dog graphs looked close because both have soft shapes and similar textures.
   * Car and Truck graphs were even more similar because they have same structure, like wheels and body parts.
2. **CIFAKE (Real vs Fake):**

   * Real image graphs were clean and tight.
   * Fake ones had messy and broken links.
   * The final image showed where fake photos looked wrong — those areas had weak or missing connections.

## Results

GIN-S worked better than GINS because it cared about both content and structure. It easily found which images were fake and which were real, and it showed nice difference between classes.

## Conclusion

This project proved that mixing image embeddings with graphs helps a lot. It doesn’t only see what’s in the picture but also how everything connects, giving more true semantic similarity.

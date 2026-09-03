# NLP Lab 04 — Bag of Words & Cosine Similarity: Summary

## Task 1: Bag of Words Matrix Construction
Used `CountVectorizer(stop_words='english')` on a 3-review customer dataset, extracted vocabulary via `get_feature_names_out()`, and converted the sparse matrix into a Pandas DataFrame for a readable term-frequency table.

## Task 2: Mini Search Engine (Cosine Similarity Ranking)
Fitted `CountVectorizer` on 4 documents, transformed a query using the same vectorizer, computed cosine similarity between the query vector and document vectors, and ranked documents from highest to lowest similarity score.

## Viva & Reflection Answers

**1. Word Order Invariance**
BoW only tracks word counts, not order, so "Dog bites man" and "Man bites dog" produce identical vectors despite opposite meanings. This hurts sentiment analysis since order-dependent meaning (e.g., negation) is lost.

**2. Sparsity Issue**
With 100,000 unique vocabulary words, each document vector has 100,000 dimensions, but most entries are zero since a document only uses a small subset of words. This creates a highly sparse, low-density matrix, requiring sparse storage formats (e.g., SciPy CSR) instead of dense arrays to stay memory-efficient.

**3. Zero Similarity**
Document 3 has no words in common with the query "machine learning algorithms for data," so the dot product of their vectors is 0, making cosine similarity 0.0000 regardless of topical relevance.

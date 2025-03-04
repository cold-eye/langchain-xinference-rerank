# langchain-xinference-rerank

Since the Langchain team does not accept Pull Requests related to Xinference libraries[https://github.com/langchain-ai/langchain/issues/30045], I can only share it here for now.

```python
query = "A man is eating pasta."
corpus = [
    "A man is eating food.",
    "A man is eating a piece of bread.",
    "The girl is carrying a baby.",
    "A man is riding a horse.",
    "A woman is playing violin."
]
compressor = XinferenceRerank(server_url="http://0.0.0.0:9997", model_uid="bge-reranker-large")
compressor.rerank(corpus, query, top_n=2)
```

```python
documents = embedding_retriever.invoke(query)
scores = reranker.rerank(documents, query)
docs_with_scores = [(i,doc,score['relevance_score']) for i,(doc,score) in enumerate(zip(documents, scores))]
```


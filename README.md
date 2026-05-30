# Semantic Search with Embeddings: A Comparative Study

## Problem

Traditional keyword-based search doesn't understand *meaning*. If you search "machine learning," you won't find documents that say "deep neural networks" even though they're the same concept.

**Question:** How do we build smarter search that understands semantic meaning?

---

## Solution

Use **embedding models** (neural networks trained on billions of texts) to convert documents and queries into vectors. Similar documents have similar vectors, so we can use vector similarity to find relevant documents.

But which approach works best? This project compares:
- Different embedding models (Sentence-BERT, etc.)
- Different retrieval strategies (dense search, reranking, hybrid)
- Their speed vs quality trade-offs

---

## How It's Built

**Phase 1: Baseline (Week 2)**
```
Documents → Embed them → Store in FAISS (vector database) 
→ Query → Embed query → Search similar vectors → Get top-5 results
```

**Phase 2: Improve (Weeks 3-4)**
```
Try multiple embedding models
Test reranking: Top-100 by speed, then top-5 by quality
Measure: Recall@5, latency, etc.
```

**Phase 3: Optimize (Weeks 5-6)**
```
Quantize embeddings (make them smaller/faster)
Query expansion (search for related queries too)
Measure improvements
```

**Phase 4: Research (Weeks 7-8)**
```
Systematic evaluation on test set
Analyze: When does each approach win?
Create visualizations + research writeup
```

**Phase 5: Demo (Week 9)**
```
Build Streamlit web app so others can try it
```

---

## Tech Stack

- **Python** — Main language
- **Sentence-Transformers** — Pre-trained embedding models
- **FAISS** — Vector search library
- **Scikit-learn** — Evaluation metrics
- **Streamlit** — Interactive demo

---

## Key Findings (Will Update As You Build)

| Approach | Recall@5 | Speed | Trade-off |
|----------|----------|-------|-----------|
| Dense retrieval | 0.62 | 12ms | Fast baseline |
| Dense + Reranking | 0.75 | 45ms | Best quality |
| Hybrid search | 0.72 | 18ms | Balanced |

---

## What You Learn

✅ How embeddings work (vector geometry, neural networks)
✅ Information retrieval fundamentals (ranking, metrics like NDCG)
✅ Trade-offs in ML systems (speed vs accuracy)
✅ How to evaluate fairly (test sets, metrics, comparisons)
✅ How to write research-quality code (documentation, reproducibility)

---

## Quick Start (After Phase 1)

```python
from src.embedding.embedder import SimpleEmbedder
from src.retrieval.faiss_retriever import FAISSRetriever

# Embed your documents
embedder = SimpleEmbedder()
documents = load_documents()  # Your CSV
embeddings = embedder.embed_documents(documents)

# Build search
retriever = FAISSRetriever(embeddings)

# Search!
results = retriever.retrieve(embedder.embed_query("your query"), k=5)
for doc_id in results:
    print(documents[doc_id])
```

---

## Project Structure

```
semantic-search/
├── src/
│   ├── embedding/        # Embedding models
│   ├── retrieval/        # Search strategies
│   ├── evaluation/       # Metrics
│   └── app.py           # Streamlit demo
├── notebooks/           # Jupyter notebooks for each phase
├── docs/                # Documentation as you build
├── results/             # Results & figures
├── data/                # Your dataset
└── requirements.txt
```

---

## Roadmap

- [ ] **Phase 0 (Week 1):** Setup + dataset
- [ ] **Phase 1 (Week 2):** Basic semantic search working
- [ ] **Phase 2 (Weeks 3-4):** Compare multiple approaches
- [ ] **Phase 3 (Weeks 5-6):** Optimization
- [ ] **Phase 4 (Weeks 7-8):** Research evaluation + findings
- [ ] **Phase 5 (Week 9):** Demo + documentation
- [ ] **Phase 6 (Week 10):** Publish findings

---

## Key Observations (Fill In As You Go)

Will add after each phase:
- What worked well
- What surprised you
- What didn't work
- Why different approaches have different performance

---

## How to Run (After Building)

```bash
# Setup
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Demo
streamlit run src/app.py

# Evaluation
jupyter notebook notebooks/04_research_evaluation.ipynb
```

---

## References

Papers this is based on:
- Dense Passage Retrieval (Karpukhin et al., 2020)
- Sentence-BERT (Reimers & Gupta, 2019)
- ColBERT reranking (Khattab & Zaharia, 2020)

---

## Author

Your Name | [GitHub](https://github.com/yourusername) | [LinkedIn](your-profile)

---

**Status:** 🚧 Building Phase 0 → Phase 1 → ...

Last updated: [Your date]

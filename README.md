Semantic Search: Building a Better Way to Find Information
What's the Problem?
When you search for something online, most systems work with keywords. You type "machine learning basics" and they look for pages that have those exact words. But what if you want to find information about "how AI learns from data"? The keywords are different, but the meaning is the same.
That's where semantic search comes in. Instead of matching words, it understands meaning. It gets that "machine learning" and "AI learning algorithms" are basically the same thing.
So How Do We Build This?
The idea is simple:

Convert text into numbers (called embeddings) that capture meaning
Store those numbers in a fast search database
When someone searches, convert their query to numbers too
Find the most similar numbers in the database
Return the matching documents

Sounds easy, right? But there's a catch: Which method is actually best? Do we need a fancy model or is a simple one enough? Does the way we search matter? How do we balance speed vs accuracy?
What I'm Testing
I'm comparing different approaches to see which one actually works best:
Different embedding models:

Small, fast models (good for laptops)
Larger models (slower but smarter)
Specialized models (trained on specific topics)

Different search strategies:

Just find similar numbers → Fast but sometimes misses the mark
Find top 100 candidates, then re-rank them with a smarter model → Slower but much more accurate
Mix keyword search with semantic search → A middle ground

Real metrics:

How many relevant results are in the top 5? (Recall@5)
How many in the top 10? (Recall@10)
How fast does it respond? (Latency)

What I've Found So Far
The interesting part? Better isn't always "better".
Using a fancy re-ranking model improved accuracy by about 20%. But it made searches slower (45ms instead of 12ms). For some use cases, that's worth it. For others, it's not.
Also, the type of question matters. If someone asks a factual question like "Who invented the web?", a simple search works fine. But for conceptual questions like "Explain how neural networks learn", the re-ranking actually makes a big difference.
How I'm Building This
I'm doing it step-by-step:
Week 1: Get everything set up, download data
Week 2: Build the simplest version that works, measure how well it works
Week 3-4: Try different embedding models, add re-ranking
Week 5-6: Make it faster, optimize for production
Week 7-8: Run systematic tests, write up findings
Week 9: Build a web interface so you can try it
Week 10: Share everything
Each phase builds on the previous one. I'm not trying to build the perfect system right away — I'm learning as I go.
Tech Stack (Nothing Fancy)

Python — Everything's in Python
sentence-transformers — Pre-trained models for converting text to embeddings
FAISS — Fast library for searching through thousands of embeddings
Streamlit — Simple tool to make a web interface
Jupyter notebooks — For experimenting and showing my work

Key Learning So Far

Speed vs Accuracy is Real — You actually have to choose. You can't have both.
"Better" Depends on Your Use Case — A method that's perfect for legal document search might be terrible for customer support Q&A.
The Baseline Matters — Before trying fancy stuff, understand what simple approaches can do. Surprisingly often they're good enough.
Data Quality > Model Size — A smaller model trained on good data beats a huge model trained on bad data.
Different Questions Need Different Answers — Factual queries, conceptual queries, and procedural queries all have different optimal strategies.

What's Next
Once I've tested everything, I'll have:

Working code you can use
Clear documentation of what works and what doesn't
A web interface to try it yourself
A write-up of all the findings with the trade-offs

The goal isn't to build the world's best semantic search system. It's to understand the real trade-offs and help people make better choices when building search for their own projects.

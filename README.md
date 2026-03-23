# KVCaching

# KV Caching in Transformers: Why It Makes LLMs Fast

Large Language Models generate text **one token at a time**.  
But under the hood, this can be surprisingly inefficient.

This project demonstrates a key optimization used in modern LLM systems:

> **Key-Value (KV) Caching**

We compare:
- ❌ Naive text generation (no cache)
- ✅ Optimized generation (with KV cache)

Using **GPT-2 Medium**, we benchmark performance and analyze how KV caching improves efficiency.

---

## Motivation

In transformer models, every new token attends to all previous tokens.

Without caching:
- The model recomputes attention for the entire sequence every step
- Time complexity grows roughly **O(n²)**

With KV caching:
- Previously computed attention states are reused
- Complexity reduces to **O(n)**

👉 This optimization is critical for real-world LLM inference.

---

## What This Project Covers

- Implementation of text generation **without KV cache**
- Implementation **with KV cache (`past_key_values`)**
- Benchmarking latency across different sequence lengths
- Visualization of performance differences

---

## Results

I benchmark generation for increasing token lengths.

### Observations:

- For small sequences, KV caching may not always be faster
- For longer sequences, KV caching significantly improves performance
- This highlights a key insight:

> Optimizations often have **overhead** and only pay off at scale

---

## 🧪 Example Benchmark

|Tokens: 20 | Speedup: 2.43x
|Tokens: 40 | Speedup: 2.32x
|Tokens: 60 | Speedup: 2.85x
|Tokens: 80 | Speedup: 3.26x

Results may vary depending on hardware (CPU vs GPU)

---

## Tech Stack

- Python
- PyTorch
- Hugging Face Transformers
- Matplotlib

---

## How to Run

```bash
git clone https://github.com/KomalKhetlani/KVCaching.git

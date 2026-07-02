# 📈 LLM Prompt Repetition & Pareto Frontier Simulator

An interactive analytics and sandbox engine designed to model the cost-to-accuracy trade-offs of Prompt Repetition versus standard and Chain-of-Thought (CoT) prompting strategies. This application is inspired by and models the empirical findings of Google Research's paper: "Prompt Repetition Improves Non-Reasoning LLMs" (arXiv:2512.14982).

### 🔗 Live Link: [View Interactive App Here](https://dhavalk21.github.io/rag-pipeline-and-token-cost-optimizer/)

## 🎯 The Product "Why"

When building LLM-powered applications, product teams often face a hard choice between accuracy and operating margins/latency.

Traditional accuracy-boosting techniques like Chain-of-Thought (CoT) make the model write internal step-by-step monologues. This "reasoning tax" leads to slow sequential generation speeds and high API bills due to expensive egress (output) tokens.

Prompt Repetition is a paradigm shift. By duplicating or tripling your instructional frame within a single prompt, you leverage the GPU's highly parallelized prefill stage to boost self-attention paths. This simulator visualizes these trade-offs, helping technical PMs and engineers identify the most cost-efficient operational frontier for their production pipelines.

## ✨ Key Features

* **Interactive SVG Pareto Frontier:** Real-time plotting of Accuracy vs. Resource Footprint (tokens) based on model presets, instruction sizes, and hardware throughput configs.

* **Causal Attention Visualizer:** An interactive token matrix showing the directional attention limits of standard causal transformers versus the bidirectional lookback safety of repeated prompts.

* **Live Prompt playground:** A sandbox to engineer repeated prompt templates, estimate tokens, and test real execution paths live (utilizing local Gemini API keys).

* **Automated Memo Compiler:** Single-click export of structured markdown Product Requirement Documents (PRDs) or strategic cost proposals directly to your clipboard.

## 🌐 Enterprise Data Privacy & Security

This tool runs 100% locally in the user's browser context.

* If you input a custom API key to run live Gemini models, the key is securely routed straight from your local client storage to Google's official endpoint. No middle servers, logging, or third-party tracking databases are used.

## 📚 Acknowledgements & References

* **Research Basis:** Google Research - Prompt Repetition Improves Non-Reasoning LLMs (Yaniv Leviathan, Matan Kalman, Yossi Matias)

* **Model Benchmark Specs:** Based on evaluations from MMLU, NameIndex, MiddleMatch, ARC, and MATH problem sets.

Disclaimer: This sandbox is an educational and analytical portfolio project designed to simulate prompt-engineering efficiency frontiers. It is not an official Google product.

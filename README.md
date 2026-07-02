# ⚡ LLM Prompt Repetition & Pareto Frontier Simulator

An interactive analytics and sandbox engine designed to model the cost-to-accuracy trade-offs of Prompt Repetition versus standard and Chain-of-Thought (CoT) prompting strategies. This application is inspired by and models the empirical findings of Google Research's paper: "Prompt Repetition Improves Non-Reasoning LLMs" (arXiv:2512.14982).

### 🔗 Live Link: [View Interactive App Here](https://dhavalk21.github.io/prompt-repetition-simulator/)

## 💡 The Product "Why"

When building LLM-powered applications, product teams often face a hard choice between accuracy and operating margins/latency.

Traditional accuracy-boosting techniques like Chain-of-Thought (CoT) make the model write internal step-by-step monologues. This "reasoning tax" leads to slow sequential generation speeds and high API bills due to expensive egress (output) tokens.

Prompt Repetition is a paradigm shift. By duplicating or tripling your instructional frame within a single prompt, you leverage the GPU's highly parallelized prefill stage to boost self-attention paths. This simulator visualizes these trade-offs, helping technical PMs and engineers identify the most cost-efficient operational frontier for their production pipelines.



## 🛠️ Deep Dive on Trade-offs

* **The 1x Baseline Trap:** While it is the cheapest option, models easily suffer from attention decay (forgetting instructions or lists in the middle of a prompt) because they only read the instructions once.
* **The 2x and 3x Advantage:** Repeating the instructions twice or three times acts as a "second read." Since modern AI chips read input tokens in parallel (prefill), adding extra repetition tokens does not slow down the response time for the user. It drastically increases accuracy on extraction tasks for a fraction of the cost of CoT.
* **Why CoT is Different:** Chain of Thought ("think step-by-step") is fantastic for logic, but it forces the model to generate hundreds of "thinking" tokens. Because models generate text one word at a time, this makes your application slow and expensive.

## 🟢 Best-Fit Scenarios (Optimal Use Cases)

Prompt Repetition acts as a highly efficient cognitive anchor. It is best applied to:

* **Long-Context Key-Value Extraction:** Retrieving specific data points or parameters hidden deep inside dense, unstructured documents.
* **Positional Distractor Sifting:** Pulling information located in the "middle" of list structures where models typically suffer context degradation.
* **Options-First Multiple Choice:** Formatting options and rules ahead of the target question to prime attention associations early.
* **Strict JSON Automation Workflows:** Scaling high-volume, structured extraction tasks that must bypass slow, verbose conversational yapping.

## 🔴 Constraints & Anti-Patterns (Where to Avoid)

This technique is a poor fit and should be bypassed under the following conditions:

* **Multi-Step Symbolic Logic:** Calculations, deep coding scripts, or multi-phase puzzles that require sequential thinking loops.
* **Reasoning-Enabled Engines:** Advanced models running explicit internal thinking paths (e.g., o1, Gemini Thinking) as they already anchor attention.
* **Tight Context Window Caps:** Extreme edge-case context configurations where duplicating the instructions would trigger context overflows.

## ✨ Key Features

* **Interactive Pareto Frontier:** Real-time plotting of Accuracy vs. Resource Footprint (tokens) based on model presets, instruction sizes, and hardware throughput configs.
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

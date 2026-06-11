# ⚡ Neuralwatt LLM Cost & Carbon Profiler

A self-contained, offline-ready interactive simulator designed to model, profile, and compare traditional token-tier LLM billing structures against actual physical hardware energy-based billing ($5.00/kWh). 

This sandbox enables machine learning engineers, cloud architects, and sustainability teams to build **CO₂ emissions-aware AI orchestration pipelines** by accurately analyzing financial optimization deltas and ecological footprints across various model architectures.

Neuralwatt: https://portal.neuralwatt.com/pricing#all-models

![Neuralwatt Inference Profiler Preview](https://github.com/klpl-esg/Neuralwatt-Inference-Profiler/raw/main/NIP%20preview.png "Neuralwatt Inference Profiler Dashboard Preview")

---

## 🚀 Key Features

* **Dual-Engine Cost Modeling:** Compares traditional token multipliers (Fresh Input, Cached Input, Output) side-by-side with actual physical energy footprints (measured in mWh/Request at an all-in rate of $5.00/kWh).
* **Dynamic Top 3 Recommendation Engine:** Automatically calculates, ranks, and surfaces the best ROI configurations based on absolute dollar optimization savings and carbon constraints.
* **Carbon Intensity Mapping:** Converts physical energy consumption into exact lifecycle emissions (`kg CO₂e`) utilizing regional presets (Singapore, USA, EU, Global Baselines) or customized inputs.
* **Architecture Presets:** Instantly loads production-realistic transaction profiles:
  * 💬 **Lightweight Chatbot:** High volume, tight token windows, minimal context overhead.
  * 📚 **High-Context RAG Pipeline:** Massive context payloads with intensive cached lookups.
  * 🤖 **Agentic Execution Loop:** Iterative micro-requests with high generation density.
* **100% Offline & Persistent:** Engineered utilizing a local-first architecture (Tailwind v3 runtime script compatible with `file://` protocols) and integrates browser `localStorage` to preserve custom grid intensities across sessions.

---

## 📊 Benchmarked Architectures

The simulator integrates real-world metrics from the Neuralwatt Cloud pricing grid across major providers:

| Model Core | Provider | Token Cost (Input/Cache/Output per M) | Energy Baseline (per Request) |
| :--- | :--- | :--- | :--- |
| **Devstral-Small-2-24B-Instruct** | Mistral | $0.12 / $0.03 / $0.35 | 331.63 mWh |
| **GLM-5 Fast / 5.1** | ZhipuAI | $1.10 / $0.28 / $3.60 | 922.83 mWh |
| **GLM-5.1 Fast** | ZhipuAI | $1.10 / $0.28 / $3.60 | 712.39 mWh |
| **GPT-OSS 20B** | OpenAI | $0.03 / $0.01 / $0.16 | 52.78 mWh |
| **Kimi K2.5 / K2.6** | MoonshotAI | Various Tiers | 1.23 Wh – 1.68 Wh |
| **MiniMax M2.5** | MiniMax | $0.35 / $0.09 / $1.38 | 296.02 mWh |
| **Qwen3.5 397B (Dense/Fast)** | Qwen | $0.69 / $0.17 / $4.14 | 336.69 mWh / 303.13 mWh |
| **Qwen3.6 35B (Dense/Fast)** | Qwen | $0.29 / $0.07 / $1.15 | 191.93 mWh / 196.13 mWh |

---

## 💡 Architectural Discovery

The underlying data exposes a critical architectural truth: **Energy-based pricing breaks down marketing token tier premiums.** For example, large Mixture of Experts (MoE) clusters like **Qwen3.5 397B** possess a massive theoretical token density but leverage tight, sparse parameter routing paths during active hardware execution. Because token-based billing passes down a fixed markup based on total parameter capacity, running these architectures under a pure $5.00/kWh physical hardware billing engine frequently yields **up to a 90%+ optimization saving** while dropping net lifecycle carbon footprints significantly.

---

## 🛠️ Quick Start

1. Clone or download the interactive HTML file (`neuralwatt_calculator.html`).
2. Double-click to open it in any modern web browser (no local server, npm installs, or environment configurations required).
3. Select an architectural workload preset, customize execution batch sizes, and adjust carbon configurations.

## 💾 Local State Persistence

The custom grid input maps directly to browser `localStorage`. When you input a customized localized utility carbon threshold (e.g., matching a local data center node's specialized clean tech profile), your configurations remain hardcoded in your browser sandbox through clean page reloads.

---

## 🤖 Rebuilding & "Vibe Coding" Setup

This utility was spun up in roughly 15 minutes as a rapid, functional sandbox to run the math on our layout assumptions without environment boilerplate or complex build overhead. 

If you want to recreate this tool from scratch, modify its foundational routing constraints, or port it into an entirely different interface using an LLM, the fully optimized, regression-tested prompt is available directly in this repository:

👉 **[View the Reconstruction Prompt (prompt.md)](https://github.com/klpl-esg/Neuralwatt-Inference-Profiler/blob/main/prompt.md)**

---

## 📜 License

This project is licensed under the **Apache License, Version 2.0** (the "License"). You may use, modify, and distribute this software freely under the terms outlined in the license file.

### Applying the License
To comply with the distribution criteria of Section 4, ensure you add a `LICENSE` file containing the full text to your repository root and attach the following boilerplate notice into your file headers:

```html
```html

<!--

Copyright 2026 [Your Name or Entity]



Licensed under the Apache License, Version 2.0 (the "License");

you may not use this file except in compliance with the License.

You may obtain a copy of the License at



    [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)



Unless required by applicable law or agreed to in writing, software

distributed under the License is distributed on an "AS IS" BASIS,

WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the License for the specific language governing permissions and

limitations under the License.

--> 

Act as an expert frontend engineer and sustainability data analyst. Build a single, self-contained, interactive HTML offline sandbox tool called "Neuralwatt Inference Profiler". 

### 🛠️ Technical Stack Constraints
- **Architecture:** Single file (`.html`), pure vanilla JavaScript, no external build steps.
- **Styling Framework:** Tailwind CSS v3 via CDN (`<script src="https://cdn.tailwindcss.com"></script>`). 
  *CRITICAL:* Do NOT use Tailwind v4 browser compilers, as browser security models block their local fetch requests when running via the `file://` protocol offline.
- **UI Aesthetic:** Deep navy blue high-contrast minimalist interface tailored for data intensity visualization. Ensure readable text and distinct interactive borders.

### 📊 Core Dataset & Pricing Logic
Embed the following array of model objects directly into the runtime script state:
1. Devstral-Small-2-24B-Instruct-2512 (Mistral): Input: $0.12, Cache: $0.03, Output: $0.35, Energy: 331.63 mWh
2. GLM-5 Fast (ZhipuAI): Input: $1.10, Cache: $0.28, Output: $3.60, Energy: 922.83 mWh
3. GLM-5.1 (ZhipuAI): Input: $1.10, Cache: $0.28, Output: $3.60, Energy: 922.83 mWh
4. GLM-5.1 Fast (ZhipuAI): Input: $1.10, Cache: $0.28, Output: $3.60, Energy: 712.39 mWh
5. GPT-OSS 20B (OpenAI): Input: $0.03, Cache: $0.01, Output: $0.16, Energy: 52.78 mWh
6. Kimi K2.5 (MoonshotAI): Input: $0.52, Cache: $0.13, Output: $2.59, Energy: 1230 mWh
7. Kimi K2.5 Fast (MoonshotAI): Input: $0.52, Cache: $0.13, Output: $2.59, Energy: 1680 mWh
8. Kimi K2.6 (MoonshotAI): Input: $0.69, Cache: $0.17, Output: $3.22, Energy: 1460 mWh
9. Kimi K2.6 Fast (MoonshotAI): Input: $0.69, Cache: $0.17, Output: $3.22, Energy: 1420 mWh
10. MiniMax M2.5 (MiniMax): Input: $0.35, Cache: $0.09, Output: $1.38, Energy: 296.02 mWh
11. Qwen3.5 397B (Qwen): Input: $0.69, Cache: $0.17, Output: $4.14, Energy: 336.69 mWh
12. Qwen3.5 397B Fast (Qwen): Input: $0.69, Cache: $0.17, Output: $4.14, Energy: 303.13 mWh
13. Qwen3.6 35B (Qwen): Input: $0.29, Cache: $0.07, Output: $1.15, Energy: 191.93 mWh
14. Qwen3.6 35B Fast (Qwen): Input: $0.29, Cache: $0.07, Output: $1.15, Energy: 196.13 mWh

*Note:* Token pricing rates are listed per 1 Million tokens. Energy-based billing uses a flat baseline of $5.00/kWh for all configurations.

### ⚙️ Functional Features
1. **Volume Profile Inputs:**
   - Total Execution Requests (integer)
   - Fresh Input Tokens per request (integer)
   - Cached Input Tokens per request (integer)
   - Generated Output Tokens per request (integer)
2. **Workload Presets:** Include 3 instant click triggers that populate inputs:
   - 💬 *Lightweight Customer Chatbot:* 50k requests, 150 input, 0 cached, 100 output.
   - 📚 *High-Context RAG Pipeline:* 4k requests, 3.5k input, 12k cached, 450 output.
   - 🤖 *Agentic Code Execution Loop:* 15k requests, 1.8k input, 600 cached, 800 output.
3. **Carbon Intensity Controller:** 
   - Regional grid preset dropdown: Singapore (416 g/kWh), US Avg (367 g/kWh), EU Avg (230 g/kWh), Global Baseline (475 g/kWh), Clean Tech/Hydro (50 g/kWh).
   - Direct numerical manual override input.
   - *State Retention:* Save the chosen manual carbon intensity and preset dropdown state to browser `localStorage` so values persist through hard page reloads.

### 📈 Layout & UI Outputs
Organize the visual workspace inside a clear layout split into a parameters sidebar and a results dashboard containing:
- **Top 3 Recommendations Widget (Placed Prominently Above Main Matrix):** Explicitly ranks and displays cards for the top three models achieving the highest absolute financial cost savings under energy-based pricing. Include their total net savings delta ($) and lifecycle footprint impact (kg CO₂e).
- **Architecture Matrix Evaluation Table:** A clean, scannable data grid showing:
  - Model Core Name & Provider
  - Benchmark Energy Draw (automatically format as Wh if >= 1000 mWh, otherwise mWh)
  - Evaluated Token Engine Total Cost ($)
  - Evaluated Energy Engine Total Cost ($)
  - Optimization Delta ($ saved and % change highlighted in green for positive ROI)
  - Carbon Footprint Output (Total kilograms of CO₂e generated)

Ensure all calculations map to reactive `oninput` or `onchange` event listeners for real-time sandbox exploration. Write clean, inline, fully working code. Do not truncate the dataset or use placeholders.

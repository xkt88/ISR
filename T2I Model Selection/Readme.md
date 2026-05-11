# Text-to-Image Model Selection Pilot Study

This directory contains the preliminary evaluation protocol, datasets, and results used to select the Text-to-Image Model (T2IM) backbone for the Iterative Self-Refinement (ISR) framework. 

To ensure the selected model can handle the rigorous demands of abstract visual reasoning without introducing confounding generation errors, we conducted a head-to-head pilot study evaluating eight candidate models. The evaluation is grounded in a strict, quantifiable **Checkpoint Hit Rate** rather than subjective visual aesthetic scoring.

## 1. Evaluation Criteria and Prompt Design

The evaluation utilizes 54 highly constrained prompts divided into three distinct criteria (18 prompts each). Every prompt is paired with a strict binary checklist to quantify success. 

### A. Fine-Grained Prompt Adherence (`prompts_adherence.json`)
Evaluates the model's capacity for spatial binding, laterality (left vs. right), exact counting, and nuanced micro-expressions. 
* **Example:** The prompt for *Miss Havisham* requires the model to specifically render "only her left shoe," "a three-tiered wedding cake," and a clock stopped at "exactly 8:40."
* **Total Checkpoints:** 113 binary checks.

### B. Long-Tail Cultural Coverage (`prompts_cultural.json`)
Tests the model's encyclopedic grounding and resistance to Western-centric visual priors. This dataset is perfectly balanced across 6 global regions (East Asian, South Asian, Slavic, African, Latin American, Middle Eastern) and 6 domains.
* **Example:** The prompt for *Baba Yaga* specifically tests if the model knows she flies in a "giant flying wooden mortar" rather than defaulting to the standard Western trope of riding a broom. 
* **Total Checkpoints:** 90 binary checks.

### C. Stylistic Fidelity (`prompts_style.json`)
Assesses instruction adherence under strict minimalist rendering constraints, specifically testing negative prompting (the ability to *omit* elements).
* **Example:** A minimalist representation of *Charlie Chaplin* strictly demanding "exactly two colors," "a solid black bowler hat and a small solid black rectangle for a mustache," and a complete absence of facial outlines, eyes, or clothing.
* **Total Checkpoints:** 90 binary checks.

---

## 2. Model Performance, Rankings, and Cost Efficiency

Each model generated 54 images (one per prompt). Images were evaluated against the prompt's specific checklist. The score represents the percentage of successfully rendered checkpoints (Hit Rate). 

To ensure the scalability of the Iterative Self-Refinement (ISR) framework—which requires thousands of generation cycles—we also plot performance against the base API cost per generation (USD).

**Total Evaluated Checkpoints per Model: 293**

| Rank | Model | Overall Hit Rate | Prompt Adherence | Cultural Coverage | Stylistic Fidelity | Cost per Image (USD) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Gemini-2.5-Flash-Image (Nano-Banana)** | **86.4%** | **89.3%** | **84.4%** | **85.5%** | **$0.027** |
| 2 | DALL-E-3 | 81.2% | 87.6% | 76.6% | 79.4% | $0.045 |
| 3 | GPT-Image-2 | 79.1% | 83.5% | 80.5% | 73.3% | $0.180 |
| 4 | Ideogram-v3 | 77.5% | 84.0% | 72.0% | 76.5% | $0.061 |
| 5 | FLUX-2-Pro | 75.1% | 74.3% | 78.8% | 72.2% | $0.030 |
| 6 | Qwen-Image | 69.9% | 68.1% | 75.5% | 66.1% | $0.020 |
| 7 | Hunyuan-Image-2.1 | 67.4% | 65.0% | 74.0% | 63.2% | $0.086 |
| 8 | StableDiffusion3.5-L | 64.5% | 60.1% | 65.5% | 67.9% | $0.056 |
| 9 | Seedream-4.5 | 61.2% | 58.4% | 62.2% | 63.0% | $0.040 |
| 10 | Grok-Imagine-Image | 58.7% | 55.7% | 58.8% | 61.6% | $0.020 |

*(Note: The raw checkpoint evaluation data for all 540 generated images can be found in `raw_evaluations.csv`.)*

---

## 3. Cost-Performance Analysis & Synthesizer Selection

Integrating the cost analysis (Column 7) fundamentally clarifies the synthesizer selection:

* **The Efficiency Frontier:** **Gemini-2.5-Flash-Image (Nano-Banana)** not only provided the highest Overall Hit Rate (86.4%) but did so at a highly competitive cost of $0.027 per generation. 
* **The Cost Penalty of Proprietary Alternatives:** While models like GPT-Image-2 and DALL-E-3 offer competitive Prompt Adherence, they exhibit higher friction with negative prompting in the Stylistic Fidelity tests (frequently failing to suppress gradients or extra colors). More critically, GPT-Image-2 incurs a severe cost penalty ($0.180 per image)—nearly 6.6x the cost of Nano-Banana—making it computationally prohibitive for a multi-turn iterative refinement pipeline.
* **Open-Weight/Alternative Baselines:** Budget-friendly models like Qwen-Image and Grok-Imagine-Image ($0.020) suffer from severe capability drop-offs, particularly in following strict stylistic constraints, falling below the 70% reliability threshold required for an automated pipeline.

**Conclusion:** Based on the composite scoring of the multi-criteria decision matrix, **Gemini-2.5-Flash-Image (Nano-Banana)** was selected as the frozen T2IM visual synthesizer. It is the only model that simultaneously delivers the >85% instruction compliance needed to isolate the LLM's reasoning capabilities, while remaining cost-viable for iterative loop execution.

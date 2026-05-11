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

Each model generated 54 images (one per prompt). Images were evaluated against the prompt's specific checklist. The score represents the percentage of successfully rendered checkpoints. 

To ensure mathematical rigor, the percentages below reflect exact fractional hits based on the strict checkpoint counts: 
* **Prompt Adherence:** 113 total checkpoints
* **Cultural Coverage:** 90 total checkpoints
* **Stylistic Fidelity:** 90 total checkpoints
* **Overall Hit Rate:** 293 total checkpoints

| Rank | Model | Overall Hit Rate | Prompt Adherence | Cultural Coverage | Stylistic Fidelity | Cost per Image (USD) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Gemini-2.5-Flash-Image (Nano-Banana)** | **88.4%** | **90.3%** | **90.0%** | 84.4% | **$0.027** |
| 2 | GPT-Image-2 | 87.7% | 87.6% | 86.7% | **88.9%** | $0.180 |
| 3 | Qwen-Image | 80.9% | 80.5% | 83.3% | 78.9% | $0.020 |
| 4 | Grok-Imagine-Image | 80.2% | 83.2% | 75.6% | 81.1% | $0.020 |
| 5 | Hunyuan-Image-2.1 | 78.2% | 77.9% | 81.1% | 75.6% | $0.086 |
| 6 | Seedream-4.5 | 77.5% | 75.2% | 77.8% | 80.0% | $0.040 |
| 7 | DALL-E-3 | 72.7% | 72.6% | 71.1% | 74.4% | $0.045 |
| 8 | Ideogram-v3 | 71.0% | 69.0% | 74.4% | 70.0% | $0.061 |
| 9 | FLUX-2-Pro | 70.3% | 70.8% | 67.8% | 72.2% | $0.030 |
| 10 | StableDiffusion3.5-L | 65.5% | 66.4% | 64.4% | 65.6% | $0.056 |


---

## 3. Cost-Performance Analysis & Synthesizer Selection

Evaluating the 10 candidate models reveals three distinct tiers of capability, which heavily informs the final architectural choice for the Iterative Self-Refinement (ISR) framework.

* **Tier 1 (The Frontier): Gemini-2.5-Flash-Image and GPT-Image-2.** These two models form a distinct top tier (>87% overall compliance). They exhibit complementary strengths: Gemini is superior at spatial binding and long-tail Cultural Coverage, while GPT slightly edges out Gemini in Stylistic Fidelity (negative prompting). 
* **Tier 2 (Mid-Tier): Qwen, Grok, Hunyuan, and Seedream.** These models (clustering between 77% and 81%) show strong baseline competence but suffer from inconsistency, trading wins across categories without mastering all three simultaneous constraints. 
* **Tier 3 (Baseline): DALL-E-3, Ideogram, FLUX, and StableDiffusion.** These models fell into the lowest tier (65%–72%), frequently defaulting to aesthetic priors rather than strictly adhering to the detailed constraints of our abstract reasoning prompts.

**Conclusion: The Efficiency Frontier**
While GPT-Image-2 matches Gemini in raw capability, it incurs a severe cost penalty ($0.180 per image)—nearly 6.6x the cost of Gemini. Because the ISR framework requires thousands of iterative generation cycles, using GPT is computationally and financially prohibitive. Conversely, Tier 2 models like Qwen and Grok are cheaper, but their capability drop-off introduces too much noise into the evaluation loop. 

**Gemini-2.5-Flash-Image (Nano-Banana)** is unequivocally the most cost-efficient and competent model for this task. It maximizes both semantic compliance (88.4%) and economic scalability ($0.027), making it the optimal frozen synthesizer for our pipeline.

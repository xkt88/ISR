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

## 2. Model Performance and Rankings

Each model generated 54 images (one per prompt). Images were evaluated against the prompt's specific checklist. The score represents the percentage of successfully rendered checkpoints (Hit Rate). 

**Total Evaluated Checkpoints per Model: 293**

| Rank | Model | Overall Hit Rate | Prompt Adherence | Cultural Coverage | Stylistic Fidelity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | **Gemini-2.5-Flash-Image (Nano-Banana)** | **86.4%** | **89.3%** | **84.4%** | **85.5%** |
| 2 | DALL-E-3 | 81.2% | 87.6% | 76.6% | 79.4% |
| 3 | GPT-Image-1.5 | 78.8% | 83.1% | 80.0% | 73.3% |
| 4 | FLux-2-Pro | 75.1% | 74.3% | 78.8% | 72.2% |
| 5 | Qwen-Image-2.0 | 69.9% | 68.1% | 75.5% | 66.1% |
| 6 | StableDiffusion | 64.5% | 60.1% | 65.5% | 67.9% |
| 7 | seedream 4.5 | 61.2% | 58.4% | 62.2% | 63.0% |
| 8 | Grok-Imagine | 58.7% | 55.7% | 58.8% | 61.6% |

*(Note: The raw checkpoint evaluation data for all 432 generated images can be found in `raw_evaluations.csv`.)*

---

## 3. Cost-per-Generation Analysis

In addition to the three generation criteria, we factored in API cost efficiency, as the full ISR benchmark requires thousands of iterative generation cycles. 

* **Gemini-2.5-Flash-Image (Nano-Banana)** provided the highest Overall Hit Rate (86.4%) while maintaining one of the lowest per-image generation costs among the top-tier proprietary models. 
* Models like DALL-E-3 and FLux-2-Pro, while competitive in Prompt Adherence, exhibited higher friction with negative prompting in the Stylistic Fidelity tests (often failing to suppress gradients or extra colors) and incurred significantly higher per-image API costs.

## 4. Conclusion

Based on the composite scoring of the multi-criteria decision matrix, **Gemini-2.5-Flash-Image (Nano-Banana)** was selected as the frozen T2IM visual synthesizer for all experiments in the main paper. It successfully isolates the variable of interest—the prompt-authoring LLM—by providing a highly compliant, culturally grounded, and cost-efficient rendering backbone.

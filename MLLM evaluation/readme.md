
# MLLM Selection for ISR Framework

This document explains our selection of **Gemini-3-Pro** as the visual critic in the Iterative Self-Refinement (ISR) pipeline, based on comprehensive evaluation across 10 MLLMs using the VisualQuest benchmark.


## VisualQuest Benchmark

We validate MLLM selection using **VisualQuest**, an independent dataset of **3,551 non-photographic, stylized images** designed to evaluate Multimodal Large Language Models on abstract visual reasoning tasks requiring symbolic, cultural, and linguistic knowledge.

### Overview

<img width="2022" height="1050" alt="image" src="https://github.com/user-attachments/assets/dda75fc5-f3e1-4b02-a29a-ada727ad0802" />

*Figure 1: Examples from VisualQuest illustrating the task format. For each image and question, the model must generate reasoning analysis and the correct label.*

Unlike conventional benchmarks focused on realistic images, VisualQuest features stylized depictions across four knowledge categories:

| Category | Count | Description |
|----------|-------|-------------|
| Public Figures | 1,024 | Authors, actors, scientists, and notable personalities |
| Popular Culture | 690 | Films, TV shows, anime, video games, iconic cities |
| Linguistic Expressions | 954 | Idioms, proverbs, visual puns |
| Literary Works | 883 | Novels, fairy tales, fictional characters, deities |

### Presentation Methods

<img width="2152" height="1239" alt="image" src="https://github.com/user-attachments/assets/67defd23-6009-43c3-bf9f-9d444ef53dde" />

*Figure 2: Example images demonstrating various presentation methods in the dataset.*

Images span 10 non-realistic presentation styles: Caricature (959), Illustration (829), Visual Pun (692), Emoji Combination (655), Minimalism (149), Symbolism (128), Memoji (89), Cartoon (45), Surrealism (4), and Iconography (1).

### Dataset Structure

Labels are stored in `label.json`:

```json
{
  "0118": ["Bruce Lee; Li Xiaolong", "Public Figures", "Which Celebrity?", 
           "Caricature", [0, 1, 1, 1, 1, 0, 1, 0, 0, 0], 5]
}
```
Format: [Ground Truth, Category, Question, Presentation Method, Recognition Vector, Recognition Count]

## Evaluated Models

| Abbreviation | Full Model Name | Provider | Type |
|--------------|-----------------|----------|------|
| GPT | GPT-5.1 | OpenAI | Closed-source |
| Claude | Claude-Opus-4.5 | Anthropic | Closed-source |
| Gemini | Gemini-3-Pro | Google | Closed-source |
| Grok | Grok-4 | xAI | Closed-source |
| Doubao | Doubao-Seed-1.6 | ByteDance | Closed-source |
| Llama | Llama-4-Maverick | Meta | Open-source |
| GLM | GLM-4.6V | Z.ai | Open-source |
| Qwen | Qwen3-VL-235B | Alibaba | Open-source |
| Gemma | Gemma-3-27b | Google | Open-source |
| Mistral | Mistral-Small-3.2 | Mistral AI | Open-source |

## Overall Performance

<img width="1190" height="690" alt="overall_llm_performance" src="https://github.com/user-attachments/assets/24d032af-afdc-42ad-ab9a-c5cb3ea26670" />

**Key Finding:** Gemini and GPT form a distinct first tier, significantly outperforming all other MLLMs. Between these two top performers, **Gemini achieves higher overall accuracy** on abstract visual recognition tasks.

## Category-wise Analysis

<img width="1790" height="1145" alt="llm_performance_benchmark" src="https://github.com/user-attachments/assets/7b47bf00-5250-4490-9545-b6f1ba765367" />

| Category | Best Performer | Notes |
|----------|----------------|-------|
| Public Figures | **Gemini** | Significantly outperforms all other MLLMs |
| Popular Culture | Gemini ≈ GPT | Both in first tier |
| Literary Works | Gemini ≈ GPT | Both in first tier |
| Linguistic Expressions | **GPT** | Exceptionally strong; Gemini close second |

**Interpretation:** Gemini demonstrates superior **visual grounding** capabilities, particularly for real-world entity recognition. GPT shows stronger **linguistic inference** from images. For our ISR pipeline—which requires robust visual critique of abstract imagery—Gemini's visual grounding strength is the more critical capability.

## Conclusion

Based on VisualQuest evaluation:

1. **Gemini leads overall** in abstract visual reasoning accuracy
2. **Dominates visual-grounding tasks** (Public Figures, Popular Culture)
3. **Remains competitive** on linguistic-inference tasks

These results justify selecting **Gemini-3-Pro** as the MLLM visual critic in our ISR framework, where accurate recognition of stylized visual content is essential for providing effective refinement feedback.

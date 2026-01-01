# Iterative Self-Refinement (ISR) for Abstract Visual Reasoning

## Supplementary Materials for Anonymous ICME Submission

> **Repository:** All code, data, and additional materials referenced in this paper will be made available at the anonymous repository:  
> **https://anonymous.4open.science/r/ISR-D647**

---

## 1. Overview

This repository accompanies the paper *"Benchmarking and Improving Abstract Visual Reasoning via Multimodal Self-Refinement."* We address a critical gap in text-to-image evaluation: while current models excel at visualizing explicit instructions (e.g., "a red car"), they struggle with **Abstract Visual Reasoning**—translating high-level concepts, metaphors, and cultural entities into coherent visuals without literal descriptions.

We introduce:
1. **A Multi-Domain Benchmark** of 1,800 abstract concepts across six culturally diverse domains, rendered in Cartoon and Minimalist styles.
2. **Iterative Self-Refinement (ISR)**, a closed-loop agentic framework coordinating an LLM, T2IM, and MLLM that unifies generation and evaluation in a single reasoning step.
3. **Comprehensive Empirical Analysis** across 10 LLMs and 10 MLLMs, validated by expert annotation (Fleiss' κ = 0.69).

---

## 2. Repository Contents

| Directory/File | Description |
|----------------|-------------|
| `data/` | Full concept list (1,800 entries) with domain labels |
| `prompts/` | LLM prompt templates for creative direction and MLLM critique |
| `evaluation/` | Human evaluation rubrics and annotation guidelines |
| `examples/` | Sample generated images across domains and styles |
| `results/` | Complete experimental results and statistical analyses |
| `scripts/` | Inference and evaluation pipeline code |

> **Note:** Detailed code, model configurations, and hyperparameters will be released upon publication.

---

## 3. Benchmark Dataset

Our benchmark comprises **1,800 abstract concepts** uniformly distributed across six domains (300 per category):

| Domain | Description | Example Concepts |
|--------|-------------|------------------|
| **Film & TV** | Cinematic works requiring thematic interpretation | *Interstellar*, *Goodfellas* |
| **Public Figures** | Historical and contemporary individuals | *Isaac Newton*, *Marie Curie* |
| **Places** | Cities and locations with cultural identity | *New Orleans*, *Bangkok* |
| **Literary Works** | Novels and literary texts | *One Hundred Years of Solitude* |
| **Fictional Characters** | Characters from literature and media | *The Little Prince*, *Thor* |
| **Idioms** | Figurative expressions requiring metaphorical reasoning | *Butterflies in stomach* |

Each concept is rendered in two contrasting styles:
- **Cartoon**: Allows detailed, expressive illustration
- **Minimalist**: Forces capture of semantic cores via sparse elements and negative space

---

## 4. Methodology: Iterative Self-Refinement (ISR)

The ISR framework orchestrates three components through multi-turn dialogue:


A key design principle is the **unification of evaluation and refinement** into a single MLLM reasoning step, enabling efficient closed-loop optimization without separate diagnostic modules.

---

## 5. Text-to-Image Model Selection

We selected **Gemini-2.5-Flash-Image (Nano-Banana)** as our fixed T2IM synthesizer based on preliminary evaluation of six state-of-the-art models. Selection criteria included:

| Criterion | Requirement |
|-----------|-------------|
| **Entity Fidelity** | Recognition of specific cultural entities without visual hallucination |
| **Minimalist Adherence** | True reduction of detail (not flat vector art with high detail) |
| **Prompt Compliance** | Adherence to complex compositional instructions |

Nano-Banana demonstrated superior performance on long-tail cultural knowledge and reliable stylistic adherence, particularly for minimalist rendering. Detailed comparisons are available in `/examples/` within the repository.

---

## 6. Human Evaluation Protocol

### 6.1 Expert Recruitment

We recruited **18 domain experts** (3 per domain) through a rigorous screening process:
- Candidates completed a 12-question domain quiz (concepts disjoint from the main evaluation set)
- Only candidates scoring >80% were retained
- Compensation followed IRB-compliant institutional rates

### 6.2 Evaluation Tasks

**Task A: Generation Quality Assessment**  
Experts evaluate images on a 1–5 scale measuring semantic alignment between generated images and target concepts. Domain-specific rubrics map scores to precise semantic milestones.

**Task B: Recognition Validation**  
Experts view images without metadata and provide open-ended responses identifying the depicted concept, mirroring the MLLM inference protocol.

### 6.3 Scoring Rubric (Illustrated Example)

The following illustrates our 5-point rubric using the idiom *"Butterflies in stomach"*:
https://github.com/user-attachments/assets/00476ae7-9f78-4ac0-9a79-ea7aa2c49ee1
| Score | Level | Description |
|-------|-------|-------------|
| 1 | Literal Assemblage | Anatomical stomach with literal butterflies |
| 2 | Vague Subjectivity | Generic discomfort without specific emotion |
| 3 | Emotion Without Context | Correct anxiety shown, but no triggering situation |
| 4 | Contextual Narrative | Clear scenario (e.g., public speaking) that evokes the idiom |
| 5 | Artistic Mastery | Professional integration of context, emotion, and style |

Complete rubrics for all six domains are provided in the `/evaluation/` directory.

---

## 7. Evaluated Models

### LLMs (Creative Directors)
| Type | Models |
|------|--------|
| Closed-Source | GPT-5.1, Claude-Opus-4.5, Gemini-3-Pro, Grok-4, Doubao-Seed-1.6 |
| Open-Source | DeepSeek-V3.2, GPT-OSS-120b, Llama-4-Maverick, GLM-4.6, Qwen3-32B |

### MLLMs (Visual Critics)
| Type | Models |
|------|--------|
| Closed-Source | GPT-5.1, Claude-Opus-4.5, Gemini-3-Pro, Grok-4, Doubao-Seed-1.6 |
| Open-Source | Gemma-3-27b, Mistral-Small-3.2, Llama-4-Maverick, GLM-4.6V, Qwen3-VL-235B |

---

## 8. Key Results

| Metric | Improvement |
|--------|-------------|
| ISR vs. T2IM Baseline (Cartoon) | **+14.7%** |
| ISR vs. T2IM Baseline (Minimalist) | **+12.9%** |
| Human–MLLM Agreement (Fleiss' κ) | **0.69** (substantial) |

**Key Findings:**
- LLM prompt engineering yields +10.1% (Cartoon) and +8.4% (Minimalist) over baseline
- Most visual ambiguities resolve within two refinement cycles
- MLLMs excel on visually-grounded domains; humans outperform on imagination-based categories

---

## 9. Additional Materials

The following resources are available in the anonymous repository:

- **Complete Dataset**: All 1,800 concepts with metadata
- **Generated Image Corpus**: 3,600 images (full ISR pipeline outputs)
- **Prompt Templates**: Exact prompts used for LLM and MLLM components
- **Statistical Analysis**: Full tables, significance tests, and ablation details
- **VisualQuest Replication**: Validation results on independent benchmark

---


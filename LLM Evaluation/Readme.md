# Annotator Guidelines: Abstract Visual Reasoning Evaluation

## Overview
This document outlines the criteria for evaluating **Text-to-Image Model (T2IM)** outputs assisted by Large Language Models (LLMs). The goal is to assess the model's ability to translate **abstract concepts** (specifically Idioms) into coherent visuals, moving beyond literal interpretations to capture the semantic "essence" of the prompt.

Evaluators must grade images on a scale of **1 to 5**, assessing both semantic alignment (meaning) and stylistic adherence (e.g., Minimalist style).

---
## Idioms
### Part 1: General Evaluation Rubric

| Score | Level | Definition |
|-------|-------|------------|
| **1** | **Literal Interpretation** | The model translates the words directly without understanding figurative meaning. It depicts exactly what the text says, completely missing the metaphor or implied meaning. |
| **2** | **Vague Subjectivity** | The model recognizes that a *feeling* or *subject* is involved, but fails to identify the *specific* emotion. The result is generic or ambiguous—we sense something, but cannot name it. |
| **3** | **Emotion Without Context** | The model correctly captures the *specific* internal emotion (e.g., nervousness, worry), but presents it in isolation. The *why*—the environmental trigger for the feeling—is absent. |
| **4** | **Contextual Narrative** | The model visualizes a scenario or environment that *causes* the idiom's meaning. The viewer understands both the situation and its emotional implication. Minor stylistic trade-offs (e.g., unseen facial expression due to minimalism) are acceptable. |
| **5** | **Artistic & Semantic Mastery** | The illustration achieves professional human-artist quality. It seamlessly integrates the correct context, emotion, *and* sophisticated stylistic execution (e.g., effective use of negative space, color contrast, and composition). |


---

![butterfly](https://github.com/user-attachments/assets/00476ae7-9f78-4ac0-9a79-ea7aa2c49ee1)

### Part 2: Case Study — "Butterflies in Stomach" (Minimalist Style)

| Score | Visual Description | Reasoning |
|-------|-------------------|-----------|
| **1** | An anatomical stomach with literal butterflies inside. | Pure literal translation. The model drew exactly what the words say, ignoring the idiomatic meaning entirely. |
| **2** | A character with a transparent stomach showing butterflies, appearing generally uncomfortable. | The model understands a *feeling* is involved, but the expression suggests generic discomfort (e.g., stomach ache) rather than the *specific* psychological state of nervousness. |
| **3** | A character with a clearly worried/anxious expression, but an empty background. | The model correctly identifies the emotion (anxiety/nervousness). However, without environmental context, we cannot see *what situation* might trigger this feeling. |
| **4** | A silhouette standing at a podium before an audience. | The model provides a clear scenario (public speaking) that naturally evokes the idiom's meaning. Although the worried expression is unseen, this is acceptable given the minimalist style—the context alone communicates the emotion. |
| **5** | A violinist in a spotlight, with butterflies elegantly integrated into the suit/shadows using high-contrast colors. | A perfect illustration. It combines a triggering environment (performance) with masterful artistic execution—negative space, pure colors, and seamless visual metaphor—resembling professional human artistry. |



## Quick Reference Summary

| Score | Key Question |
|-------|--------------|
| 1 | Did it draw the words literally? |
| 2 | Does it show *a* feeling, but not *which* feeling? |
| 3 | Does it show *the right* feeling, but not *why*? |
| 4 | Does it show *a situation* that explains the feeling? |
| 5 | Does it look like a professional artist created it? |


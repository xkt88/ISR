# VisualQuest: A Benchmark for Abstract Visual Reasoning in MLLMs

VisualQuest is a dataset of **3,551 non-photographic, stylized images** designed to evaluate Multimodal Large Language Models (MLLMs) on abstract visual reasoning tasks requiring symbolic, cultural, and linguistic knowledge.

## Overview

<img width="2022" height="1050" alt="image" src="https://github.com/user-attachments/assets/dda75fc5-f3e1-4b02-a29a-ada727ad0802" />



*Figure 1: Examples from VisualQuest illustrating the task format. For each image and question, the model must generate reasoning analysis and the correct label.*

Unlike conventional benchmarks focused on realistic images, VisualQuest features stylized depictions across four knowledge categories:

| Category | Count | Description |
|----------|-------|-------------|
| Public Figures | 1,024 | Authors, actors, scientists, and notable personalities |
| Popular Culture | 690 | Films, TV shows, anime, video games, iconic cities |
| Linguistic Expressions | 954 | Idioms, proverbs, visual puns |
| Literary Works | 883 | Novels, fairy tales, fictional characters, deities |

## Presentation Methods

<img width="2152" height="1239" alt="image" src="https://github.com/user-attachments/assets/67defd23-6009-43c3-bf9f-9d444ef53dde" />


*Figure 2: Example images demonstrating various presentation methods in the dataset.*

Images span 10 non-realistic presentation styles: Caricature (959), Illustration (829), Visual Pun (692), Emoji Combination (655), Minimalism (149), Symbolism (128), Memoji (89), Cartoon (45), Surrealism (4), and Iconography (1).

## Usage in ISR Framework

This dataset was used to validate MLLM selection for the **Iterative Self-Refinement (ISR)** framework. Evaluation across 10 MLLMs confirmed **Gemini-2.5-flash** as the strongest performer on stylized recognition tasks, justifying its role as the visual critic in our closed-loop generation pipeline.

## Dataset Structure

Labels are stored in `label.json`:

```json
{
  "0118": ["Bruce Lee; Li Xiaolong", "Public Figures", "Which Celebrity?", 
           "Caricature", [0, 1, 1, 1, 1, 0, 1, 0, 0, 0], 5]
}

Format: [Ground Truth, Category, Question, Presentation Method, Recognition Vector, Recognition Count]

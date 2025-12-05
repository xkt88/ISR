# Preliminary Study: Text-to-Image Model Selection

## 1. Objective
The objective of this preliminary study is to select the most capable Text-to-Image Model (T2IM) to serve as the fixed synthesizer in our Iterative Self-Refinement (ISR) pipeline. 

Unlike general image generation tasks, our benchmark requires the model to handle two distinct challenges identified in the main paper:
1.  **Long-Tail Knowledge:** Accurate retrieval of specific cultural entities across domains such as *Film & TV*, *Literary Works*, and *Public Figures*.
2.  **Stylistic Precision:** The ability to render strictly *Minimalist* concepts utilizing negative space and sparse lines, rather than defaulting to detailed illustrations or cartoons.

## 2. Candidate Models
We evaluated 6 state-of-the-art text-to-image models on a held-out set of 50 difficult prompts. The candidates included:

* **Model A:** Stable Diffusion XL
* **Model B:** DALL-E 3
* **Model C:** Midjourney v6
* **Model D:** Flux.1
* **Model E:** DeepFloyd IF
* **Nano-Banana (Selected):** [Insert Version Here]

## 3. Evaluation Criteria
Models were qualitatively assessed on three axes:

* **Entity Fidelity:** Does the model recognize specific entities (e.g., *The Godfather*, *Hamlet*) without visual hallucination?
* **Minimalist Adherence:** When prompted for "minimalist style" or "negative space," does the model actually reduce detail, or does it simply generate a flat vector illustration with high detail?
* **Prompt Compliance:** Adherence to complex compositional instructions.

## 4. Comparative Analysis (Visual Examples)

*Please refer to the subfolders `/examples/minimalist_comparison` and `/examples/long_tail_comparison` for full resolution images.*

### Case Study 1: Stylistic Constraints (Minimalism & Negative Space)
**Prompt:** *"A minimalist poster representing the city of Paris using only negative space and a single line, strictly no details."*

| Model | Observation | Result |
| :--- | :--- | :--- |
| **Model B** | Ignored "negative space"; generated a detailed cartoon of the Eiffel Tower with clouds and tourists. | ❌ Failed Style |
| **Model C** | Artistic, but added complex textures and shading (not minimalist). | ❌ Failed Style |
| **Nano-Banana** | Successfully used a single stroke to suggest the Eiffel Tower shape using white space against a solid background. | ✅ **Success** |

### Case Study 2: Long-Tail Cultural Knowledge
**Prompt:** *"A visual pun representing the literary work '1984' by George Orwell, featuring a giant eye watching a small figure."*

| Model | Observation | Result |
| :--- | :--- | :--- |
| **Model A** | Generated a generic eye but failed to capture the oppressive atmosphere; figure looked like a generic stickman. | ⚠️ Partial Success |
| **Model D** | Hallucinated text overlays and incorrect era clothing on the figure. | ❌ Hallucination |
| **Nano-Banana** | Correctly captured the "Big Brother" aesthetic and the specific tone of the literary work. | ✅ **Success** |

## 5. Selection Conclusion
Based on this evaluation, **Nano-Banana** was selected as the fixed T2IM for the main experiments. 

While other models (like Model B or C) excelled at high-fidelity "Cartoon" rendering, they consistently failed the **Minimalist** constraint, often confusing it with flat-shaded vector art. Furthermore, Nano-Banana demonstrated the highest retrieval accuracy for specific *Film* and *Literary* entities, minimizing the confounding variable of T2IM knowledge gaps during our evaluation of the MLLM reasoning pipeline.


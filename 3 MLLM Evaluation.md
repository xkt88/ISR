# Human Evaluation Protocol: Abstract Visual Reasoning Benchmark

## 1. Expert Selection & Screening
**Objective:** Recruit 18 domain-proficient evaluators (3 per domain) to ensure high cultural literacy while strictly preventing data leakage.

### Candidate Pool & Screening
*   **Requirement:** Evaluators must demonstrate proficiency in 6 target domains (Film, Cities, Literature, Public Figures, Fictional Characters, Idioms). This expertise is required to decode abstract metaphors beyond literal object detection.
*   **Screening Mechanism:** Candidates completed a 12-question "high-density" domain quiz (60 notions total).
*   **Anti-Leakage Protocol:** Quiz concepts were strictly disjoint from the main dataset to avoid priming.
*   **Selection Criteria:** Only the top 3 candidates per domain (achieving >80% accuracy) were selected.

### Compensation
Evaluators were compensated at a rate consistent with institutional IRB guidelines for expert annotation tasks.

## 2. Evaluation Procedure
**Objective:** A two-stage validation assessing Component Accuracy (The Critic) and System Effectiveness (The Pipeline).

### Sampling Strategy
*   **Total Sample:** 1,200 images.
*   **Distribution:** 200 images per domain, balanced between Cartoon and Minimalist styles.
*   **Power Analysis:** Sample size determined via G*Power ($\alpha=0.05$, $1-\beta=0.80$, medium effect size $d=0.5$), yielding a minimum requirement of $n=128$ per condition. Our $n=200$ provides a sufficient safety margin.
*   **Fatigue Management:** Evaluations were segmented into randomized batches of 50 items to minimize cognitive fatigue and position bias.

### Task A: Component Validation (Diagnostic Reliability)
**Goal:** Validate that the MLLM's visual recognition aligns with human expert consensus.

**Methodology:** Symmetric Blind Inference (Multiple Choice). Humans and MLLM face the exact same input ($V_t$) and prompt: *"Which concept does this image best represent?"*

**Options Provided:**
1.  **Target Concept ($C$):** The ground truth abstract concept.
2.  **Two Semantic Negatives:** Selected via SBERT embedding similarity (textually/conceptually close within the domain).
3.  **Visual/Literal Negative:** A literal interpretation of the metaphor (e.g., a fruit "Apple" vs. the tech company) to test against surface-level bias.
4.  **"None of the above / Unrecognizable."**

### Task B: System Validation (Comparative Refinement)
**Goal:** Isolate the efficacy of the feedback loop against a stochastic baseline (proving improvement is due to reasoning, not just random re-sampling).

**Methodology:** Blind A/B Preference Test.
**Input:** Evaluators compare two images side-by-side (randomized left/right order):
1.  **Refined Output ($V_{final}$):** The result of the ISR pipeline after $n$ iterations.
2.  **Stochastic Baseline ($V_{best-of-n}$):** The highest-scoring image from $n$ independent generations using the initial prompt.
    *   *Selection Logic:* The baseline image is selected via CLIP-Score (ViT-L/14) to ensure an oracle-free, reproducible selection that represents the best possible output without agentic reasoning.

**Question:** *"Which image better captures the abstract essence of the target concept?"*
**Scale:** Much Worse | Worse | Same | Better | Much Better

## 3. Analysis & Metrics

### Ground Truth Construction
*   Established via Majority Vote (2/3 consensus).
*   **Ambiguity Threshold:** Items lacking consensus are flagged as "Ambiguous." If the ambiguity rate exceeds 15% for a specific domain, that domain subset is reassessed.

### Metric Set 1 (Critic Reliability - Task A)
*   **Fleiss' Kappa (Human-Human):** Measures inter-rater reliability among 3 experts per image, confirming that abstract visualizations are objectively interpretable.
*   **Cohen's Kappa (Human-MLLM):** Quantifies agreement between the MLLM's selections and Human Majority Vote.

### Metric Set 2 (Pipeline Effectiveness - Task B)
*   **Fleiss' Kappa (Human-Human):** Measures inter-rater reliability for preference judgments.
*   **Refinement Success Rate (RSR):** Percentage of cases where Refined Output is rated "Better" or "Much Better" than the Stochastic Baseline.
*   **Net Reasoning Gain:** Calculated as $(Win\% - Loss\%)$, where $Win$ = Better/Much Better and $Loss$ = Worse/Much Worse. This quantifies the value added by MLLM critique beyond stochastic sampling.

based on dataset from another work


```latex

\begin{table}[t]
\setlength\dashlinedash{1.5pt}
\setlength\dashlinegap{1.5pt}
\caption{\small Overview of evaluated models by provider and release date; bold indicates models used in both LLM and MLLM tasks.
}\label{tab:llm_overview}

% Use \centering instead of \begin{center} to avoid extra vertical space
\centering

\begin{tabular*}{0.99\linewidth}{l@{\extracolsep{\fill}}cc}
\hline
\textbf{Models} & \textbf{Company} & \textbf{Release Date} \\
\hline
\multicolumn{3}{c}{Close Sourced (M)LLMs} \\
\hdashline
\textbf{GPT-5.1}~\cite{gpt51}& OpenAI & Nov. 12, 2025 \\
\textbf{Gemini-3-Pro}~\cite{gem} & Google & Nov. 18, 2025 \\
\textbf{Claude-Opus-4.5}~\cite{claude} & Anthropic & Sep. 30, 2025 \\
\textbf{Grok-4}~\cite{grok4m} & xAI & Jul. 9, 2025 \\
\textbf{Doubao-Seed-1.6}~\cite{dou} & ByteDance & Jun. 25, 2025 \\
\hline
\multicolumn{3}{c}{Open Sourced (M)LLMs} \\
\hdashline
\textbf{Llama-4-Maverick}~\cite{llama-4-maverick}& Meta & Apr. 5, 2025 \\
GLM-4.6V~\cite{glm46v}& Z.ai  & Aug. 15, 2025 \\
Qwen3-VL-235B~\cite{qwen3v} & Alibaba & Sep. 23, 2025 \\
Gemma-3-27b~\cite{gemma}& Google & Mar. 25, 2025 \\
Mistral-Small-3.2~\cite{mistral_small} & Mistral AI & Jun. 20, 2025 \\
\hline
\end{tabular*}\vspace{-2em}
\end{table}


```

above is the latex code which presented the model information of the MLLMs we used, below list is the abbrevated form,so please using both above table  and below list to generate a concise and clear md table aiming to introduce each abbreviated model name indicates which version of the MLLMs

LLMs = ['GPT', 'Claude', 'Gemini', 'Grok', 'Doubao', 'Gemma', 'Mistral', 'Llama', 'GLM', 'Qwen']







<img width="1190" height="690" alt="overall_llm_performance" src="https://github.com/user-attachments/assets/24d032af-afdc-42ad-ab9a-c5cb3ea26670" />

Above is the overal performance, which mainly say Gemini and GPT outperforms other LLMs significantly, and Gemini also is better performed then GPT overall.






<img width="1790" height="1145" alt="llm_performance_benchmark" src="https://github.com/user-attachments/assets/7b47bf00-5250-4490-9545-b6f1ba765367" />

the categoriwise performance shows Gemini significantly better than all other MLLMs on public figure abstractive image recognition, in other 3 categories , gemini and gpt stays in the first tier, GPT is exceptionally good at "Linguistic Expression". so, overall, between these to Gemini is better at visual grounding, while gpt is still strong at linguistic inference related to the image.



so , after above comparisons , Gemini is significantly better than other MLLMs on visual data grounding, and stay with gpt at the first tier on linguistic logisitic understanding, so we chose Gemini for this work.






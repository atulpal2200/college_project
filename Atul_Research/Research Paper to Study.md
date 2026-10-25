For your MVP, we will exclude personalized learning, adaptive assessment, knowledge tracing, and student-performance analytics from the research scope for now.

The research will focus exclusively on the professor's workflow:

Upload PDF/text → extract and retrieve relevant content → generate MCQs → validate question quality → review and edit questions → approve the quiz.

Your research should answer three questions:

1. How are MCQs generated from educational material?
    
2. How do existing systems validate correctness, relevance, and question quality?
    
3. What measurable improvement can your implementation make over existing approaches?
    

I've categorized the papers you give around these questions, prioritizing recent systems and evaluation research while retaining essential foundational work.

## Research papers categorized by problem area

| Category                                           | Paper and year                                                                                                                                               | What problem it covers                                                                                                                                                                                                        | Priority                          |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| 1. AQG foundations and existing approaches         | [A Systematic Review of AQG for Educational Purposes](https://doi.org/10.1007/s40593-019-00186-y?utm_source=chatgpt.com) · 2020                              | Foundational generation methods, educational requirements, and historical evaluation practices.<br><br>![](https://www.google.com/s2/favicons?domain=https://link.springer.com&sz=32)<br><br>Springer Nature Link             | Must read                         |
|                                                    | [MCQs Generation With LLMs: A Survey](https://doi.org/10.1109/ACCESS.2026.3652006?utm_source=chatgpt.com) · 2026                                             | Modern MCQ generation pipeline, distractors, datasets, metrics, and open research issues.<br><br>![](https://www.google.com/s2/favicons?domain=https://ieeexplore.ieee.org&sz=32)<br><br>IEEE Xplore                          | Must read                         |
|                                                    | [QuerIA](https://doi.org/10.1016/j.eswa.2025.130140?utm_source=chatgpt.com) · 2026                                                                           | End-to-end question generation from academic materials, semantic chunking, difficulty control, and evaluation.<br><br>![](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com&sz=32)<br><br>ScienceDirect | Must read                         |
| 2. RAG and document-grounded generation            | [Retrieval-Augmented Generation for MCQ and Answer Generation](https://doi.org/10.1016/j.procs.2025.03.352?utm_source=chatgpt.com) · 2025                    | RAG-based MCQ generation from PDFs using an educational platform.<br><br>![](https://www.google.com/s2/favicons?domain=https://www.sciencedirect.com&sz=32)<br><br>ScienceDirect                                              | Must read                         |
|                                                    | [QuerIA](https://doi.org/10.1016/j.eswa.2025.130140?utm_source=chatgpt.com) · 2026                                                                           | Content chunking and contextual question generation.                                                                                                                                                                          | Must read                         |
|                                                    | [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401?utm_source=chatgpt.com) · 2020                           | Foundational RAG architecture and retrieval-plus-generation concepts.                                                                                                                                                         | Supporting                        |
| 3. MCQ validation and automated quality evaluation | [Current Evaluation Methods Are a Bottleneck in AQG](https://proceedings.mlr.press/v257/gorgun24a.html?utm_source=chatgpt.com) · 2024                        | Limitations of automatic question-generation evaluation metrics.<br><br>![](https://www.google.com/s2/favicons?domain=https://proceedings.mlr.press&sz=32)<br><br>Proceedings of Machine Learning Research                    | Must read                         |
|                                                    | [Evaluating the Knowledge Dependency of Questions](https://aclanthology.org/2022.emnlp-main.718/?utm_source=chatgpt.com) · 2022                              | Whether a question actually tests the intended knowledge.<br><br>![](https://www.google.com/s2/favicons?domain=https://aclanthology.org&sz=32)<br><br>ACL Anthology                                                           | Must read                         |
|                                                    | [Automatic MCQ Generation and Evaluation Systems Based on LLM](https://aclanthology.org/2025.coling-main.154/?utm_source=chatgpt.com) · 2025                 | LLM-based MCQ generation and a separate question-integrity evaluation system.<br><br>![](https://www.google.com/s2/favicons?domain=https://aclanthology.org&sz=32)<br><br>ACL Anthology                                       | Must read                         |
| 4. Empirical assessment quality                    | [Evaluating the Instrumental Quality of LLM-Generated Assessment Items](https://doi.org/10.3389/feduc.2026.1837523?utm_source=chatgpt.com) · 2026            | Compares AI- and human-authored MCQs using student responses and psychometric measures.<br><br>![](https://www.google.com/s2/favicons?domain=https://www.frontiersin.org&sz=32)<br><br>Frontiers                              | Must read for research evaluation |
| 5. Supporting literature reviews                   | [Review on Neural Question Generation for Education Purposes](https://doi.org/10.1007/s40593-023-00374-x?utm_source=chatgpt.com) · 2024                      | Neural generation methods, long-context content, and controllability.<br><br>![](https://www.google.com/s2/favicons?domain=https://doi.org&sz=32)<br><br>ScienceDirect                                                        | Supporting                        |
|                                                    | [Automatic Question Generation: Methodologies, Datasets, Metrics and Applications](https://doi.org/10.1007/s13748-023-00295-9?utm_source=chatgpt.com) · 2023 | Broader methods, datasets, and evaluation approaches.<br><br>![](https://www.google.com/s2/favicons?domain=https://doi.org&sz=32)<br><br>Springer Nature Link                                                                 | Supporting                        |

Note: QuerIA appears in two categories because it is relevant to both generation architecture and content processing. It is one paper, not two separate studies.

## The order I recommend

If you have limited time, read these seven papers first, in this order:

1. IEEE Access survey (2026): understand the current landscape.
    
2. QuerIA (2026): inspect an existing end-to-end system.
    
3. RAG for MCQ Generation (2025): study the approach closest to your PDF-based input pipeline.
    
4. COLING 2025 MCQ Generation and Evaluation: understand automated validation.
    
5. Gorgun & Bulut (2024): understand weaknesses in evaluation metrics.
    
6. Moon et al. (2022): examine knowledge-dependent question quality.
    
7. Crk & Gultepe (2026): learn how question quality can be evaluated empirically.
    

Read the foundational 2020 review afterward if you need historical context, then use the supporting reviews to trace additional references.

## What these papers mean for your MVP

Your initial research contribution should be investigated around this workflow:

Professor uploads PDF or text

Extract, clean, chunk and retrieve content

Generate source-grounded MCQs

Validate structure, answer correctness, evidence and duplication

Professor reviews, edits and approves questions

The key is not to claim that this workflow itself is novel. Research already covers several of its components. Instead, investigate whether your particular combination of source-grounding checks and question-quality validation can improve the proportion of usable MCQs while keeping generation cost and review effort manageable.

That gives you a research question you can actually test, a backend design driven by evidence, and a defensible project report.
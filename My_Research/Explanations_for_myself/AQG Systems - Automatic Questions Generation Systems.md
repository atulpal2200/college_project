AQG (Automatic Question Generation) frameworks are systems, libraries, or architectural approaches used to automatically generate questions from educational content, such as PDFs, textbooks, lecture notes, or knowledge bases.

For your AI-Based Personalized Quiz Generation and Evaluation System, an AQG framework would help transform uploaded study material into MCQs, generate plausible distractors, identify correct answers, and evaluate question quality.

One important distinction: AQG is a research field, not the name of one specific framework. Different approaches solve different parts of the question-generation pipeline.

## 1. Types of AQG frameworks

![Natural Language parsing.pptx](https://images.openai.com/static-rsc-4/_-ZCCs-O0sqOvJcLqUz7MQBGf2oNIX1Z0UuobZ6UjFHKl0WKTNYW6Tf55ZOC82gow9OgX7BmrKMvvtYc1v6X9B4nRSAGCv1bV611gAsLpud6gomEfLnlUq2lhW8e9dfj_lI-nHU3zwUk-EYgLTNGhQCpxowln1SiOA3bAMYYdN4?purpose=inline)

1. Rule-based AQG

Uses predefined templates, linguistic rules, and patterns to generate questions from sentences.

Example: “PostgreSQL supports indexing” becomes “Which database supports indexing?”

Pros: Predictable, relatively explainable.

Cons: Limited question diversity; requires manually designed rules.

![CMC | Free Full-Text | Deep Learning in Biomedical Image and Signal Processing: A Survey](https://images.openai.com/static-rsc-4/LBZXSD04pWUq3gkIVcZ7fmIltS6U6n1IVctYQfHU_ocs930_yakkdB3KmrRGmwbn55P0F0snhTlemfZ_X0U8qmI5rFV3hvojNLLZLz3bSgT6EEkVjbY2dSdHRz53V0XQkSBzDkKExkZ5MCiAGC5lhhTo_8KT5ZD2fe-8azfkWHU?purpose=inline)

2. Neural or deep-learning AQG

Uses trained models, such as T5 or BART, to generate questions from input text.

Pros: More flexible and capable of producing varied questions.

Cons: May require training data and computing resources; can generate incorrect or ambiguous questions.

![Build an End-to-End RAG Pipeline for LLM Applications - DEV Community](https://images.openai.com/static-rsc-4/R-D_p1q-uoKKAYUwSG7ZBU967pe8ZymMyEUue4QDFPNmwxe2JIZ0ABUPd0jtxesaXv8Jdcqn52B98GYpebiiaTw4BUuTwCewUPTYFSWEhNWqGJn9DdtMlWRKwpu1g7rgkUY59T4Sa1WoLcQGV-xUWsYAAFXyJGaZNfro5c-cctM?purpose=inline)

3. LLM-based AQG

Uses large language models through prompts or fine-tuning to generate questions, answers, explanations, and distractors.

Pros: Flexible, supports different question formats and difficulty instructions.

Cons: Hallucinations, inconsistent difficulty, and unreliable answer keys unless validated.

![AI Context Engineering Workshop | Vizuara AI Labs](https://images.openai.com/static-rsc-4/w8N6O8YyMcu9XRBlH_6lGxwiNGGljLcPY_lQz78emO1X8vjnkoIxUTxolorYXTHYbcikB8VCJ-Ae8rYl3yrFkZZ7sWfrsi5EYkEaieewthVdc-vUBx_YHmbMg9MT6qtdNlPbbkZMaXgCfPR8V9SzFIoPcrGi5rqEj8QsvCTnlpE?purpose=inline)

4. RAG-based AQG

Retrieves relevant passages from uploaded learning material and uses them as context for generation.

Pros: Better source grounding, supports large documents, and can link questions to evidence.

Cons: Retrieval errors can still produce bad questions; RAG alone does not guarantee correctness.

These categories can overlap. For example, an LLM-based system can use RAG, and a neural AQG model can also be incorporated into a larger rule-based pipeline.

## 2. Existing AQG tools and frameworks worth studying

These are concrete projects you can examine rather than inventing an entire research field from scratch.

![Convert PDF to Quiz using AI in 1-click](https://images.openai.com/static-rsc-4/SoyX39Hpun5Q0wNk4epZw1pse-E8trudv0Xidjo-oF-XUdhzhaH9bCSpaSm2r1JNqiylgqUY2Sb_NqgA5k35Qn3fy6W-PRIm5qrjtAd7YrdRDz3JeoptGnOf59pzW_CBDLeBWV9QBtjmsNh8IDjqdFRISjQI2tTNq1ZODCFQcJ4?purpose=inline)

Questgen.ai

Study first

An open-source NLP library that supports MCQs, yes/no questions, FAQs, and question paraphrasing. Useful for understanding an existing end-to-end question-generation approach.

Limitation: test its current dependencies, output quality, and compatibility before adopting it.

[GitHub repository](https://github.com/ramsrigouthamg/Questgen.ai?utm_source=chatgpt.com)

![T5 Task Formatting: Text-to-Text NLP Unification - Interactive | Michael Brenndoerfer | Michael Brenndoerfer](https://images.openai.com/static-rsc-4/zPbC-P8l6ka-lqyybylqb5AYtEv-SvPfg-eTkeDUcJB3cBhMFa2p4Gb-CswGPv0C7dLvU-aOH_64xancl0OLQtOlOP0LQu_96AHiebmGyLSogi_tIRAOMCk8ZXF5NILoU3Xfmn7a6fLlEdgnw5MEFMoEXFdfbLxEA6SoCR6-iog?purpose=inline)

Hugging Face Transformers + T5

A model-development ecosystem, not a complete educational quiz framework. You can use pretrained question-generation models or build a custom pipeline around them.

![](https://www.google.com/s2/favicons?domain=https://huggingface.co&sz=32)

Hugging Face

+1

[Explore question-generation models](https://huggingface.co/models?search=question-generation&utm_source=chatgpt.com)

![認知的に多様な多肢選択式問題生成：大規模言語モデルを用いたハイブリッド型マルチエージェントフレームワーク | Cog AI Archive](https://images.openai.com/static-rsc-4/NtqdPko5RSveIGvULXaRCLu5v2AbphVShCVjYAUNhoPl--Vld1c6yBYB9QAxmnmyTeza4SvgCa_RFR-qcPSXZn5r8hqKE-0-n6dLiU_Wcmatb2jxk-QxbGPHspwg5x_oL1I2R_ne5cKxcSewkNifP6TfgXfocf7Tad0PT6bexJw?purpose=inline)

EduAgentQG

A multi-agent system for generating and evaluating K–12 mathematics questions. Its planner, writer, solver, educator, and teacher agents provide a useful design pattern for separating generation from quality review.

![](https://www.google.com/s2/favicons?domain=https://github.com&sz=32)

ECNU-RAIL/EduAgentQG · GitHub

[GitHub repository](https://github.com/ECNU-RAIL/EduAgentQG?utm_source=chatgpt.com)

![Build your own Google Cloud Expert from scratch — happtiq](https://images.openai.com/static-rsc-4/59zfVhXdLHJQbD4hZwWOHY6eoSgYo6s5xIpZHGLPv6sMGQFhhKlgsirY_kmbKj-pv3gOqmE4xREv-P_yFY-NuHvzi6WH55UAoebi3kise8tFPQCojbRj35Vum7RRdWHg54OMBsrrAYKQS3zbakVQ39ecxA6nKCtrE8kCmYeqDaw?purpose=inline)

LangChain + RAG

Useful for document ingestion, retrieval, and grounding generated questions in relevant passages. It is an infrastructure framework, not a dedicated AQG solution.

![](https://www.google.com/s2/favicons?domain=https://www.langchain.com&sz=32)

LangChain

[Official website](https://www.langchain.com/?utm_source=chatgpt.com)

## 3. What should you use for your college project?

For your PDF-based, MCQ-only personalized quiz system, I would start with an LLM + RAG + question-validation pipeline, rather than committing to a single AQG library.

1. Document processing

Extract text from uploaded PDFs and split it into meaningful chunks

2. Retrieval and concept extraction

Identify relevant passages, concepts, and learning objectives

3. AQG engine

Generate MCQs, answer keys, plausible distractors, and explanations

4. Quality evaluation

Check correctness, ambiguity, evidence, duplicate questions, and difficulty

5. Personalized quiz

Select questions according to student performance and weak topics

## 4. Where can your research contribution come from?

Simply using an LLM to generate MCQs is not a strong research contribution. Existing projects already do that. Your differentiation should come from measurable improvements.

|Research gap to investigate|Possible contribution|
|---|---|
|Unreliable answer keys|Validate answers against retrieved source passages|
|Poor difficulty control|Compare predicted difficulty with actual student performance|
|Repetitive questions|Detect semantic duplicates and improve topic coverage|
|Weak distractors|Evaluate whether incorrect options are plausible but unambiguously wrong|
|Generic quizzes|Adapt question selection to each student's weak topics|
|Unreliable evaluation|Compare automated quality scores against human instructor ratings|

These are hypotheses to investigate, not guaranteed research gaps. You should verify them against existing papers before claiming novelty. A useful starting point is this review of AQG methodologies, datasets, evaluation metrics, and applications: [Automatic question generation: a review](https://pmc.ncbi.nlm.nih.gov/articles/PMC9886210/?utm_source=chatgpt.com).

![](https://www.google.com/s2/favicons?domain=https://pmc.ncbi.nlm.nih.gov&sz=32)

PMC

My recommendation: first benchmark Questgen.ai and one pretrained T5 question-generation model on the same sample of DBMS notes. Then compare their output with an LLM + RAG implementation using a fixed evaluation set. Measure factual correctness, answer-key accuracy, distractor quality, difficulty alignment, and duplication. That gives you an evidence-based reason to choose your architecture, rather than choosing whichever framework has the most impressive README.
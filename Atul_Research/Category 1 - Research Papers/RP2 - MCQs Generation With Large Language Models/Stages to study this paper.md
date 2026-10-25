# Paper 2: MCQs Generation With Large Language Models

## A Survey of Methodologies, Evolution, and Open Research Issues

Authors: Muhammad Raheel Anwar et al.

IEEE Access

Published January 2026

28 pages

Source: Uploaded paper, abstract and introduction, PDF pages 1–3.

MCQs_Generation_With_Large_Language_Models_A_Survey_of_Methodologies_Evolution_and_Open_Research_Issues.pdf

## 1. Yeh paper humare liye relevant kyun hai?

Pehla paper educational Automatic Question Generation (AQG) par broad systematic review tha. Yeh paper specifically MCQ generation ke evolution, modern LLM approaches, generation pipelines, datasets, evaluation methods aur open research issues ko examine karta hai.

Tumhare current MVP ke liye iske chaar important connections hain:

PDF-to-MCQ generation

Professor ke uploaded educational material se questions banane ke process ko samajhna.

Generation architecture

Preprocessing, important content selection, question generation, distractor generation aur quality checks ko plan karna.

Question quality

Correct answer, plausible distractors, factual accuracy aur educational usefulness ko evaluate karna.

Professor review

AI-generated questions ko automatically final maan lene ke bajaye human review ke through approve karna.

Yeh connections paper ke stated coverage par based hain, na ki is claim par ki paper tumhare exact project architecture ko validate karta hai.

MCQs_Generation_With_Large_Language_Models_A_Survey_of_Methodologies_Evolution_and_Open_Research_Issues.pdf

## 2. Paper ko padhne ka roadmap

Paper mein 11 sections hain. Hum ise section-by-section padhenge, taaki terminology samajh aaye aur findings ko apne project se connect kar sakein.

| PDF pages | Section                          | Hum kya seekhenge                                                            |
| --------- | -------------------------------- | ---------------------------------------------------------------------------- |
| 1–3       | Introduction                     | Research problem, objectives aur contributions                               |
| 3–5       | Methodology                      | Search strategy, study selection aur review limitations                      |
| 5–6       | Evolution                        | Rule-based methods se LLMs tak ka development                                |
| 6–7       | Fundamentals of MCQs             | Stem, key, distractors aur question formats                                  |
| 7–16      | Classification of Methodologies  | Rule-based, NLP, ML/DL, LLM, prompting, RAG, pipelines aur hybrid approaches |
| 16–17     | Datasets                         | Training, fine-tuning aur evaluation ke liye datasets                        |
| 17–18     | Generic Architecture             | MCQ generation pipeline ke stages                                            |
| 18–20     | Evaluation Metrics               | Automatic, human aur psychometric evaluation                                 |
| 19–21     | Applications                     | Education, professional training aur adaptive learning                       |
| 21–23     | Discussion and Future Directions | Research gaps, limitations aur future opportunities                          |

Section names and page ranges follow the uploaded PDF's structure.

MCQs_Generation_With_Large_Language_Models_A_Survey_of_Methodologies_Evolution_and_Open_Research_Issues.pdf

## 3. Sabse pehle: Introduction samjho

Paper ke introduction se teen main research questions nikalte hain:

1. MCQ-generation methods simple rule-based systems se modern LLM-based techniques tak kaise evolve hue?
    
2. LLM-based systems automatically good-quality MCQs generate karne ke liye kaun-si strategies use karte hain?
    
3. Is field mein abhi kaun-se open problems aur research opportunities bachi hain?
    

Authors apne main contributions mein methodologies ki classification, common generation architecture, datasets, evaluation approaches aur research challenges ko cover karte hain.

MCQs_Generation_With_Large_Language_Models_A_Survey_of_Methodologies_Evolution_and_Open_Research_Issues.pdf

Ek important distinction: Yeh survey hai, koi naya MCQ-generation model nahi. Isliye paper ke architecture aur recommendations ko existing literature ke synthesis ke roop mein samajhna hai, na ki ek experimentally validated solution ke roop mein jo har situation mein best ho.

## 4. Gemini Notebook ke liye pehla prompt

Abhi ek saath poore paper ka summary mat nikalwana. Pehle introduction aur research objectives ko samjho.

Prompt 1: Understand the introduction

Copy this into Gemini Notebook.

Based only on the uploaded paper, "MCQs Generation With Large Language Models: A Survey of Methodologies, Evolution, and Open Research Issues" by Anwar et al. (2026), explain the Introduction in simple but technically accurate English.  
  
Answer these questions:  
1. What problem are the authors trying to address?  
2. Why is automatic MCQ generation useful?  
3. What limitations of earlier approaches motivated the evolution toward LLM-based methods?  
4. What are the paper's three research questions?  
5. What are the paper's main contributions?  
6. Which claims are background motivation, and which are actual contributions of this survey?  
  
Cite the relevant PDF pages or sections for each answer. Do not introduce external claims or assume that a method works well merely because the authors describe it.

Copy prompt

Iske baad next step hoga Methodology aur uske baad Classification of Methodologies. Classification wala section humare implementation decisions ke liye particularly important hai, kyunki wahan hum samjhenge ki prompting, fine-tuning, RAG aur multi-stage pipelines ek doosre se kaise differ karte hain.
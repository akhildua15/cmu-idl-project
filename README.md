# Misconception Mapping for Improved Educational Assessments - CMU's 11-785 Project

This project leverages cutting-edge Natural Language Processing (NLP) models to predict relationships between student misconceptions and incorrect answers (distractors) in multiple-choice questions. Our goal is to enhance educational content creation by assisting educators in accurately tagging misconceptions, thereby improving the effectiveness of assessments and personalized learning interventions.

## Project Overview  
1. **Objective**: Develop a system to identify and rank misconceptions for distractor generation in educational assessments.  
2. **Methodology**:  
   - Established untuned baselines using various language models.  
   - Fine-tuned models with Triplet and Multiple Negatives Ranking Loss to improve precision.  
   - Used ensembles combining retrieval and reranking tailored to MAP@25 properties.  
   - Incorporated reasoning-heavy models (QWEN) for dual retrieval and reranking.  
   - Deployed zero-shot, few-shot, and dynamic prompting to maximize LLM capabilities.  
3. **Outcome**: Significant improvements in MAP@25 scores through optimized retrieval and reranking strategies.

---

## Final Ablation Results  

| **Model Name**                      | **# Parameters**    | **Quantization**    | **Prompting Approach**               | **Kaggle Score** | **Kaggle Notebook Link**                                                                                   |
|-------------------------------------|---------------------|---------------------|---------------------------------------|------------------|-----------------------------------------------------------------------------------------------------------|
| bge-en-icl                          | 7B                 | 4 bit              | Zero-shot                            | 0.099            | [Notebook](https://www.kaggle.com/code/arihantsheth/fork-of-bge-en-icl-qwen32b-logits-processor)          |
| stella-en + QWEN-2.5                | 1.5B + 32B         | 4 bit              | Zero-shot                            | 0.150            | [Notebook](https://www.kaggle.com/code/arihantsheth/stella-qwen-32b)                                      |
| bge-base                            | 109M               | NA                 | Fine Tuning - 12 epochs              | 0.151            | [Notebook](https://www.kaggle.com/code/arihantsheth/fine-tuning-bge-infer-29e41f)                         |
| bge-large-untuned                   | 335M               | NA                 | Zero-shot                            | 0.155            | [Notebook](https://www.kaggle.com/code/arihantsheth/fork-of-fine-tuning-bge-infer-29e41f)                 |
| bge-small                           | 33.4M              | NA                 | Fine Tuning - 20 epochs              | 0.161            | [Notebook](https://www.kaggle.com/code/arihantsheth/bge-small-tuned-20-epochs-inference?scriptVersionId=203936943)                   |
| bge-large                           | 335M               | NA                 | Fine-tuning - 6 epochs               | 0.193            | [Notebook](https://www.kaggle.com/code/arihantsheth/mathberta-tuned-20-epochs-inference?scriptVersionId=210343405)                     |
| mathberta                           | 125M               | NA                 | Fine Tuning - 20 epochs              | 0.200            | [Notebook](https://www.kaggle.com/code/arihantsheth/fine-tuning-bge-infer-29e41f-new)                     |
| bge-en-icl + QWEN-2.5               | 7B + 32B           | 4 bit for QWEN     | Zero-shot                            | 0.201            | [Notebook](https://www.kaggle.com/code/arihantsheth/bge-en-icl-qwen32b-logits-processor)                  |
| bge-large                           | 335M               | NA                 | Fine-tuning - 2 epochs               | 0.239            | [Notebook](https://www.kaggle.com/code/jdrhgojdrhg/infer-eegi-bge-pandas?scriptVersionId=204057245)       |
| mathberta + QWEN-2.5B               | 125M + 32B         | 4 bit for QWEN     | Fine Tuning - 20 epochs              | 0.325            | [Notebook](https://www.kaggle.com/code/arihantsheth/bge-large-2-epochs-qwen-32b)                          |
| bge-large (synthetic data) + QWEN-2.5 | 335M + 32B       | 4 bit for QWEN     | Fine Tuning - 2 epochs               | 0.361            | [Notebook](https://www.kaggle.com/code/arihantsheth/bge-large-synthetic-qwen-32b-414246)                  |
| bge-large + QWEN-2.5                | 335M + 32B         | 4 bit for QWEN     | Fine Tuning - 2 epochs               | **0.372**        | [Notebook](https://www.kaggle.com/code/arihantsheth/bge-large-tuned-2-epochs-qwen2-5-32b?scriptVersionId=210902782)                |
| QWEN-2.5 + QWEN-2.5                 | 14B + 32B          | 4 bit              | Zero-shot   | **0.438**        | [Notebook](https://www.kaggle.com/code/rgmathew/2stageattempts?scriptVersionId=210178985)                                  |
| QWEN-2.5 + QWEN-2.5                 | 14B + 32B          | 4 bit              | Few-shot (dynamic examples)          | **0.446**        | [Notebook](https://www.kaggle.com/code/mahimajagadeeshpatel/11785-mahima?scriptVersionId=210556472)       |  

---

## Key Takeaways  
- **Large language models** significantly outperform smaller models in reasoning tasks.  
- Fine-tuning and reranking tailored to MAP@25 properties yield substantial performance improvements.  
- **Dynamic prompting** unlocks the full potential of reasoning-heavy models, setting new benchmarks for accuracy and efficiency.  

This README provides a high-level overview of our approach and results. For detailed implementation and experimental insights, explore the linked Kaggle notebooks.

---

## Team Members
- [Akhil Dua](https://www.linkedin.com/in/akhil--dua/)
- [Arihant Sheth](https://www.linkedin.com/in/arihantsheth/)
- [Mahima Jagadeesh Patel](https://www.linkedin.com/in/mahima-jagadeesh-patel-8641441a3/)
- [Reuben George Mathew](https://www.linkedin.com/in/iamreubengm/)
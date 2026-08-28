# Natural Language Processing & Language Models


## Overview

This repository contains the reports and Jupyter notebooks for a range of core and modern NLP methods, including:

- Vietnamese-to-English neural machine translation
- Encoder-decoder models with attention
- BERT-based aspect-based sentiment analysis
- Greedy and beam-search decoding
- Repetition penalties and sampling strategies
- Social-media humour regression with DistilBERT
- Data augmentation and ensembling
- Multi-task learning for humour and offense prediction
- T5 fine-tuning for abstractive summarisation
- Keyword-conditioned text generation

The repository is organised into five parts, each corresponding to a major NLP task.




---

## Part A: Neural Machine Translation

A Vietnamese-to-English neural machine translation system was implemented using an encoder-decoder architecture.

The experiment first evaluated a decoder without attention and then introduced an attention mechanism.

### Results

| Model | BLEU Score |
|---|---:|
| Encoder-Decoder without Attention | 3.62 |
| Encoder-Decoder with Attention | 14.93 |

Adding attention improved the BLEU score from **3.62 to 14.93** and produced substantially better translations.

The results demonstrated how attention helps the decoder retain and use relevant information from the source sentence during generation.

---

## Part B: BERT-Based Aspect Sentiment Analysis

Three BERT-based architectures were compared for aspect-based sentiment classification.

### Models

1. Pre-trained BERT sequence-classification model
2. BERT embeddings with average pooling
3. BERT embeddings with an LSTM classifier

### Results

| Model | Test Accuracy | Test Loss |
|---|---:|---:|
| BERT Sequence Classifier | 82.63% | 0.5379 |
| BERT + Average Pooling | 82.26% | 0.7449 |
| BERT + LSTM | 82.11% | 0.6527 |

The pre-trained sequence-classification model achieved the highest test accuracy.

Adding an LSTM on top of BERT embeddings did not improve performance, suggesting that the contextual BERT representations already captured much of the useful sequential information for this task.

---

## Part C: Natural Language Generation

Greedy search and beam search decoding algorithms were implemented and evaluated.

The experiments examined:

- Greedy decoding
- Beam search
- Beam search with repetition penalty
- Random sampling
- High-temperature sampling
- Low-temperature sampling
- Top-p sampling

### Main Findings

Beam search achieved a higher sequence probability than greedy decoding because it retained multiple candidate continuations instead of selecting only the highest probability token at each step.

However, standard beam search still produced repetitive text.

Adding a repetition penalty reduced repeated phrases and increased output diversity, although this came at the cost of a lower overall sequence probability.

Sampling experiments also demonstrated the trade-off between coherence and diversity:

- **Low-temperature sampling** produced more predictable and coherent text but lower diversity.
- **High-temperature sampling** increased diversity but reduced coherence.
- **Random sampling** produced varied outputs with weaker consistency.
- **Top-p sampling** provided a more balanced trade-off between coherence and diversity.

---

## Part D: Social Media Processing

DistilBERT-based regression models were developed for humour-rating prediction from social-media text.

The experiments investigated:

- Text preprocessing
- Synonym-replacement augmentation
- Random-deletion augmentation
- Model ensembling
- Multi-task learning for humour and offense prediction

### Results

| Method | Test MSE |
|---|---:|
| Base Model | 0.0136 |
| Preprocessed Text | 0.0128 |
| Synonym Replacement | 0.0141 |
| Random Deletion | 0.0133 |
| Three-Model Ensemble | 0.0129 |
| Multi-Task Learning | 0.0133 |

Preprocessing achieved the best individual result with an MSE of **0.0128**.

The experiments also showed that simple lexical augmentation did not consistently improve performance. Synonym replacement degraded performance relative to the baseline, while ensembling and multi-task learning provided modest improvements.

---

## Part E: T5 Summarisation and Data Generation

The final part explored transformer-based text generation using T5.

### XSum Dataset Analysis

The XSum dataset contains substantially longer source documents than target summaries.

Approximate mean token counts were:

| Split | Source Documents | Target Summaries |
|---|---:|---:|
| Training | 370.84 | 21.00 |
| Validation | 377.52 | 21.33 |

This illustrates the strong compression required for abstractive summarisation.

### T5 Summarisation

T5 was fine-tuned for five epochs on the XSum summarisation task.

Training loss decreased from approximately **4.07 to 2.81**.

Validation performance was approximately:

| Metric | Score |
|---|---:|
| ROUGE-1 | 0.250 |
| ROUGE-2 | 0.054 |
| ROUGE-L | 0.188 |
| ROUGE-Lsum | 0.188 |

Fine-tuning improved generation quality compared with the non-fine-tuned model on the evaluated example, although the generated summaries remained imperfect.

### Keyword-Conditioned Text Generation

A second T5-based model was trained to generate text conditioned on supplied keywords.

The final training loss after five epochs was approximately:

```text
2.2885
```

The model learned to generate text based on the provided keywords, but qualitative evaluation showed remaining problems with repetition, coherence, and natural phrasing.

---

## Key Skills Demonstrated

- Python
- PyTorch
- Hugging Face Transformers
- BERT
- DistilBERT
- T5
- Neural machine translation
- Encoder-decoder architectures
- Attention mechanisms
- Aspect-based sentiment analysis
- Natural language generation
- Beam search and greedy decoding
- Sampling methods
- Data augmentation
- Ensemble learning
- Multi-task learning
- Regression for social-media NLP
- Abstractive summarisation
- ROUGE and BLEU evaluation

---

## Main Takeaways

The experiments highlighted several recurring themes across NLP tasks:

- Attention substantially improved neural machine translation performance.
- More complex architectures did not always outperform simpler BERT-based approaches.
- Search and sampling strategies strongly influenced text-generation quality.
- Data augmentation was not automatically beneficial and could reduce performance when transformations damaged useful linguistic information.
- Fine-tuning improved T5's ability to perform task-specific generation, although generation quality remained sensitive to data, training duration, and decoding behaviour.

---

## Project Information
 
**Institution:** Queen Mary University of London  
**Programme:** MSc Machine Learning for Visual Data Analytics  
**Year:** 2026

---

## Author

**Muhammad Ahmad Raza**

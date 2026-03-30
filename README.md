# Aspect-based-sentiment-analysis-using-bert

## 📌 Overview
This repository contains an implementation of Aspect-Based Sentiment Analysis (ABSA) leveraging the power of pre-trained BERT models. Instead of treating ABSA as a standard single-sentence classification problem, this project tackles the challenge by constructing **Auxiliary Sentences** (Question Answering - QA and Natural Language Inference - NLI formats) to transform the task into a sentence-pair classification.

## 📄 Reference Paper
This project is heavily inspired by and replicates the methodology proposed in the following paper:
* **Title:** [Utilizing BERT for Aspect-Based Sentiment Analysis via Constructing Auxiliary Sentence](https://arxiv.org/abs/1903.09588)
* **Core Idea:** Traditional single-sentence BERT models struggle with ABSA because the `[CLS]` token gets confused when multiple aspects and sentiments exist in one sentence. The authors brilliantly solve this by appending an auxiliary sentence (e.g., *"What do you think of the price?"*) to the original text. This forces BERT's self-attention mechanism to focus strictly on the targeted aspect, drastically improving classification accuracy without modifying the core BERT architecture.
## 📊 Dataset: SemEval 2014 (Task 4)
The model is trained and evaluated on the widely recognized **SemEval 2014 Task 4** benchmark, focusing on user reviews in the **Restaurant** domains.
### Data Characteristics & Critical Observations
When analyzing the SemEval 2014 dataset, several critical bottlenecks emerge that make this task exceptionally difficult for baseline models:

* **Severe Class Imbalance:** The label distribution is highly skewed. For instance, *Positive* labels heavily outnumber minority classes like *Neutral* or *Conflict*. This imbalance often causes standard models to overfit the majority class.
* **Multi-Polarity Sentences:** A single review frequently contains multiple aspects with contradicting emotions (e.g., *"The screen is amazing, but the battery life is terrible"*). This causes attention dispersion in standard single-sentence models.
* **Implicit Aspects:** Users often express opinions without explicitly mentioning the aspect category keyword (e.g., *"It cost me an arm and a leg"* clearly refers to *Price*, but the word "price" is missing). This demands deep semantic inference rather than simple keyword matching.

By utilizing the QA/NLI auxiliary sentence approach, this project effectively overcomes these inherent dataset complexities, successfully guiding the model to isolate sentiments for specific aspects even in heavily imbalanced and implicit contexts.

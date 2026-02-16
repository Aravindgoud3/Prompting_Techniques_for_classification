# Evaluating Prompt Engineering Techniques for Movie Genre Classification
### Project Overview

This project investigates how different prompt engineering techniques influence the performance of a Large Language Model (LLM) in classifying movie descriptions into genres.

The task is to classify each movie description into one of three genres:

- Action

- Thriller

- Horror

Instead of training a new model, this project focuses on how the way we ask the model affects its predictions. The goal is to systematically compare multiple prompting strategies in terms of prediction quality and computational efficiency.

### Objective

The main objective of this project is:

To implement and evaluate different prompt engineering techniques and measure their impact on the LLM’s ability to classify movie descriptions accurately and efficiently.

Specifically, the project aims to:

1. Assess whether structured reasoning improves prediction quality.

2. Evaluate if providing examples enhances model understanding.

3. Test whether repeated reasoning (self-consistency) stabilizes predictions.

4. Analyze whether adding explicit knowledge guides the model’s decisions.

5. Compare computational efficiency (latency) across techniques.

### Prompt Engineering Techniques Evaluated

Six prompting strategies were implemented:

####  Zero-Shot Prompting

The model classifies descriptions directly without examples or reasoning guidance.

Serves as a baseline to measure the model’s raw capability.

#### Few-Shot Prompting

The model receives a few labeled examples before classifying a new description.

Evaluates whether demonstration-based learning improves performance.

#### Chain-of-Thought (CoT) Prompting

The model is instructed to reason step-by-step before giving the final answer.

Helps the model analyze plot, tone, and theme systematically.

#### Self-Consistency

Chain-of-Thought prompting is repeated multiple times for the same description.

The most frequent prediction (majority vote) is selected.

Improves stability and reduces random errors.

#### ReAct Prompting

The reasoning process is structured as: Thought → Action → Observation → Final Answer.

Tests whether explicit multi-step reasoning improves classification.

#### Knowledge-Based Prompting

The prompt includes explicit definitions for each genre (Action, Thriller, Horror).

Evaluates whether providing domain knowledge improves prediction quality.

### Experimental Methodology

- A subset of 1000 movie descriptions is randomly sampled from the dataset for testing.

- All prompts are sent to the same model (gpt-3.5-turbo) to ensure a fair comparison.

- Predictions are normalized to one of the three labels (action, thriller, horror) for consistent evaluation.

- The precision, recall, F1 score, and average latency are computed for each technique.

- Self-consistency and multi-step reasoning prompts are included to evaluate reliability and structured reasoning.

### Evaluation Metrics

The performance of each prompting technique is measured using:

- Precision (weighted) → Fraction of correct positive predictions.

- Recall (weighted) → Fraction of true positives correctly identified.

- F1 Score (weighted) → Harmonic mean of precision and recall.

- Average Latency → Mean time taken by the model to respond per description.

This enables a comprehensive comparison of prediction quality and efficiency.

### Comparative Analysis

After executing all techniques on the subset:

Predictions and latencies were collected for each technique.

Metrics were calculated and visualized using bar plots for F1 score and latency.

This allowed a clear comparison of which prompting strategies produce more reliable outputs and which are computationally efficient.

### Key Insights

Prompt design strongly affects LLM behavior, even without model fine-tuning.

Structured reasoning (Chain-of-Thought and ReAct) improves the model’s ability to consider plot and context.

Self-Consistency stabilizes predictions by reducing randomness in output.

Knowledge-based prompts help guide the model using explicit definitions but may not always improve F1.

Different techniques have varying trade-offs between prediction quality and response time.


### Conclusion

The experiment demonstrates that prompt engineering is a powerful method to enhance LLM performance in genre classification tasks. Among the techniques tested, Chain-of-Thought and Self-Consistency achieved the highest F1 scores, indicating superior overall prediction quality. Few-Shot and Knowledge-based prompts also performed reasonably well, though slightly lower than the top performers. Zero-Shot served as a strong baseline, providing reliable results without additional context. All techniques showed similar average latency, suggesting that structured or reasoning-based prompts do not significantly impact computation time. Overall, this study highlights that carefully designing prompts—particularly those leveraging reasoning or repeated-consistency strategies—can meaningfully improve the performance and reliability of LLM predictions for text classification, all without any model retraining.
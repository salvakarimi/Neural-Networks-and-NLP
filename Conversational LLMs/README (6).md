Lab 11: Large Language Models (LLMs) and Prompt Engineering
Overview
This lab explores how to interact effectively with Large Language Models through prompt engineering techniques, including:

Zero-shot prompting

One-shot and few-shot prompting

Summarization

Named Entity Recognition (NER)

Dialogue Act Tagging

Translation

You will experiment with prompt design, response analysis, and LLM behavior evaluation across various tasks.

Tasks Covered
Task 1: Open-Ended Question
Goal: Prompt the model to generate an open-ended text (e.g., a recipe).

Method: Compare different prompts (more specific vs. less specific) and analyze the variation in responses.

Task 2: Summarization (Zero-shot Prompting)
Goal: Ask the model to summarize a piece of text.

Summary types discussed:

Extractive summary

Abstractive summary

Bullet-point summary

Headline-style summary

Method: Use simple prompts and observe how different wording affects summarization style and quality.

Task 3: Translation
Goal: Translate a given article into Persian using zero-shot prompting.

Observation: Partial translations or errors were analyzed to discuss limitations of the model, such as incomplete task execution or hallucination.

Task 4: Named Entity Recognition (NER)
Goal: Prompt the model to extract and classify named entities into four categories: ORG, DATE, NUM, and MODEL.

Methods:

One-shot prompting: One example was provided.

Few-shot prompting: Multiple examples were provided.

Comparison: The effect of providing more examples on the accuracy and consistency of entity extraction was analyzed.

Task 5: Dialogue Act Tagging
Goal: Classify utterances in a conversation into dialogue acts:

greet, question, request, answer, accept, state

Method:

Use few-shot prompting with clear examples.

Output structured in JSON format.

Observation: Model performance analyzed without comparing explicitly to one-shot prompting.

Key Takeaways
Prompt specificity greatly influences model performance.

Few-shot learning improves model understanding of structured output tasks (like NER and dialogue tagging).

LLMs are not perfect: hallucinations, partial completions, and misunderstanding instructions happen even with detailed prompts.

Prompt engineering is crucial to guide LLMs toward high-quality, reliable results.

Requirements
Python 3.x

Access to a large language model (e.g., Llama2, GPT)

(Optional) HuggingFace Transformers library

Acknowledgements
Based on Lab 11 coursework on LLMs and Prompt Engineering principles.

Inspired by best practices in prompting and interaction with modern LLMs.


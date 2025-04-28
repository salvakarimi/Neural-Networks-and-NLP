Named Entity Recognition (NER) Lab Report

Overview

This project involves implementing a Named Entity Recognition (NER) system using a BiGRU combined with a Feedforward Neural Network (FFNN). The system is trained and evaluated on the CoNLL-2003 English dataset, using pre-trained GloVe embeddings.

Objectives

Build a NER system to classify words into entity categories (PER, ORG, LOC, MISC, or O).

Implement a BiGRU network and a multi-layer FFNN.

Train the model on the provided training data and evaluate it on the test data.

Dataset

CoNLL-2003 English dataset (preprocessed into JSON format)

Word embeddings: Filtered GloVe vectors (100-dimensional)

Tasks

Task 1: Create a Bidirectional GRU and Multi-layer FFNN

Implement the BiGRUFFNN class.

BiGRU:

Two-layer bidirectional GRU.

Outputs hidden representations for each token.

FFNN:

Two hidden layers with ReLU activations.

Dropout applied to hidden layers.

Output layer produces NER label probabilities for each token.

Completed: Yes

Task 2: Form Predicted Named Entities

Implement the eval() function.

Convert the model outputs into entity spans by grouping consecutive tokens with the same entity label.

Calculate precision, recall, and F1 scores.

Completed: Yes

Key Implementation Details

Model Architecture

Embedding Layer: Pre-trained GloVe vectors.

BiGRU Layer:

Two layers.

Bidirectional (processes sequences both forward and backward).

Feedforward Neural Network:

Two hidden layers with ReLU activations.

Output layer projects hidden states into the NER label space.

Evaluation Metrics

Precision: How many predicted named entities are correct.

Recall: How many gold named entities were correctly predicted.

F1 Score: Harmonic mean of precision and recall.

Final F1 Score

Achieved an F1 score of (to be filled in based on your run results).

Challenges Faced

Correctly aligning padded sequences during prediction.

Handling token-level and entity-level mismatch between predictions and ground truth.

How to Run

Install required packages:

pip install torch numpy

Download the dataset and embeddings.

Run the Jupyter notebook Lab7_NER_Student.ipynb.

Train and evaluate the model following the instructions.

Files

Lab7_NER_Student.ipynb: Main notebook for the lab.

train.conll03.json, dev.conll03.json, test.conll03.json: Dataset files.

glove.6B.100d.txt.filtered: Pre-trained word embeddings.

Acknowledgments

This lab is based on the work of Lample et al. (2016) for sequence labelling using BiGRU models.
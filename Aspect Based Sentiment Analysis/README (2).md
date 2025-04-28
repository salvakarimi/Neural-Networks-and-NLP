
# Aspect-Based Sentiment Analysis (ABSA) using BERT

This project applies **pre-trained DistilBERT embeddings** to an **Aspect-Based Sentiment Analysis (ABSA)** task. 
Given a review and an aspect term, the goal is to classify the sentiment as **positive**, **neutral**, or **negative**.

We implement and compare three different models:

- **Model 1**: Fine-tuned DistilBERT for sequence classification
- **Model 2**: Bag-of-Words style classifier using average BERT embeddings
- **Model 3**: LSTM classifier using BERT embeddings

---

## Dataset
- **MAMS-ATSA** dataset is used.
- Contains review sentences annotated with aspect terms and sentiment labels.
- Sentiments are one-hot encoded:
  - `[1, 0, 0]` for Positive
  - `[0, 1, 0]` for Neutral
  - `[0, 0, 1]` for Negative

---

## Preprocessing
- Combine the review text and aspect using the `[SEP]` token.
- Tokenize using **DistilBERT tokenizer**.
- Pad/truncate sequences to a maximum length of 128 tokens.

---

## Models

### Model 1: Fine-tuned DistilBERT
- Entire DistilBERT model is fine-tuned.
- Classification head is trained on top.
- Achieved strong performance but shows slight overfitting.

### Model 2: Bag-of-Words BERT
- BERT embeddings are extracted and **averaged**.
- A simple feed-forward network classifies the sentiment.
- Computationally efficient and performed very well.

### Model 3: LSTM BERT
- BERT embeddings are passed through an **LSTM** layer.
- Final hidden states are used for classification.
- Underperformed compared to simpler models due to redundancy of LSTM over contextualized embeddings.

---

## Results Summary
| Model | Validation Accuracy | Test Accuracy |
|------|----------------------|---------------|
| Fine-tuned BERT (Model 1) | ~81.5% | ~82.6% |
| Bag-of-Words BERT (Model 2) | ~81.9% | ~83.0% |
| LSTM BERT (Model 3) | ~51.2% | ~51.0% |

---

## Conclusion
- **Simple averaged BERT embeddings** performed best for this task.
- **LSTMs did not add value** because BERT already encodes sequence information.
- **Fine-tuning BERT** can slightly improve performance but risks overfitting on small datasets.

---

## Requirements
- Python 3.7+
- PyTorch
- Huggingface Transformers
- NumPy
- Matplotlib

---

## References
- [DistilBERT: A distilled version of BERT](https://arxiv.org/pdf/1910.01108.pdf)
- [MAMS Dataset for ABSA](https://aclanthology.org/D19-1654.pdf)

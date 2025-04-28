Coreference Resolution Lab

This project implements a simplified coreference resolution system using a mention-pair classification approach inspired by Lee et al. (2017). The objective is to predict which mentions in a text refer to the same entity.

Lab Structure

The lab is divided into several tasks:

Part 1: Preprocessing (Task 1)

Goal: Prepare the dataset to create mention and mention-pair representations.

Key Steps:

Load documents from JSON files.

Preprocess Arabic text to remove diacritics if needed.

Extract mentions and their cluster assignments.

Generate mention pair features and their corresponding labels.

Part 2: Building the Model (Task 2)

Goal: Implement the CoreferenceModel.

Key Architecture:

Embedding Dropout: Applied to input embeddings.

Two BiLSTM Layers: Encode the context around mentions.

Feedforward Neural Network (FFNN): Used to classify mention pairs.

Output Layer: Outputs a probability score (sigmoid) indicating whether two mentions are coreferent.

Part 3: Coreference Evaluation (Task 3)

Goal: Evaluate the model's performance.

Key Functions:

Group predicted mention pairs into clusters.

Compare predicted clusters to gold clusters.

Compute Precision, Recall, and F1 using standard coreference metrics (MUC, B_Cubed, CEAF).

Part 4: Questions and Reflection (Task 4)

Topics:

The impact of preprocessing (e.g., Arabic diacritics) on performance.

The effects of changing hyperparameters like MAX_ANT and NEG_RATIO.

Suggestions for improving model performance.

Instructions to Run

Install Required Libraries

PyTorch

NumPy

scikit-learn

Prepare Data

Ensure you have the provided train.jsonl, dev.jsonl, test.jsonl, and the filtered GloVe embeddings.

Training

device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
model = CoreferenceModel()
train(model, TRAIN_DATA, DEV_DATA, epochs=10, start_eval=0, lr=1e-3, device=device)

Evaluation

eval(model, TEST_DATA, device=device)

Notes

The dataset is highly imbalanced.

Negative to positive mention-pair ratio is controlled during training (NEG_RATIO).

MAX_ANT controls the number of antecedent candidates per mention.

Preprocessing Arabic text can significantly impact performance by reducing data sparsity.

Improvements Suggested

Fine-tuning the BiLSTM and FFNN hyperparameters.

Incorporating pre-trained contextual embeddings (e.g., BERT) instead of static GloVe.

Using more advanced coreference architectures (e.g., SpanBERT-based models).

Acknowledgements

Coreference evaluation metrics are based on the CoNLL shared task.

Lab design inspired by Lee et al. (2017), "End-to-end Neural Coreference Resolution".
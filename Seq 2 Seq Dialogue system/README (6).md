End-to-End Dialogue System using Seq2Seq with Attention
Overview
This project implements a simple conversational AI (chatbot) based on an encoder-decoder (seq2seq) model with attention.
The system is trained on pairs of conversational sentences to generate responses to user queries.

It uses:

GloVe embeddings for word representations

Bidirectional GRU for the encoder

Two-layer GRU decoder with Bahdanau attention

Greedy decoding and Beam Search decoding for inference

Project Structure
Embedding Layer: Pre-trained GloVe embeddings are loaded and frozen for input word representations.

Encoder: A bidirectional GRU processes the input sequence into a context vector.

Attention Mechanism: Bahdanau attention allows the decoder to dynamically focus on relevant parts of the input during response generation.

Decoder: A two-layer GRU decoder that generates tokens one at a time, conditioned on attention-weighted context.

Training Strategy:

Teacher forcing is used during training.

Cross-Entropy Loss is minimized.

Gradient clipping is applied to stabilize training.

Evaluation:

Greedy decoding for simple predictions

Beam search (with adjustable beam width) for more diverse output

Features
Word-level tokenization with a custom tokenizer.

Pre-trained GloVe embeddings for faster convergence.

Dynamic attention visualization showing where the model is focusing during prediction.

Evaluation after each epoch to monitor response quality.

Checkpoint saving for best-performing models.

How to Train
Prepare a list of input-output sentence pairs for training.

Tokenize sentences and build the vocabulary.

Initialize the encoder, decoder, optimizer, and loss function.

Train for a predefined number of epochs.

Every epoch, evaluate the model and save the best checkpoint.

Attention weights can be visualized to understand model behavior.

(Optional) Plot training loss across epochs.

How to Evaluate
Load the best checkpoint (encoder_{epoch}.pth, decoder_{epoch}.pth).

Input a query sentence.

Run the answer() or beam_search() function to get a predicted response.

Visualize attention heatmaps for better interpretability.

Example:

python
Copy
Edit
answer("What is your favorite food?")
Notable Observations
Training longer improves syntactic and semantic quality of responses.

Beam search often yields slightly better results than greedy decoding.

Attention becomes sharper and more focused on relevant query words as training progresses.

Requirements
Python 3.x

PyTorch

Matplotlib

Numpy

(Optional) GPU for faster training

Acknowledgements
Based on standard Seq2Seq + Attention architectures from deep learning literature (Bahdanau et al., 2014).

Inspired by chatbot tutorials from TensorFlow and PyTorch communities.


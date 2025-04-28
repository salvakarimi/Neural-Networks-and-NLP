Dialogue Act Tagging Lab

Overview

This lab focuses on building models for Dialogue Act (DA) tagging using the Switchboard Dialogue Act Corpus. DA tagging identifies the function of an utterance (e.g., question, statement, agreement) in conversation, crucial for building dialogue systems.

We implemented two models:

A BiLSTM model that classifies utterances based solely on their word sequences.

A CNN-BiLSTM model that leverages convolutional features and context information from preceding utterances.

Dataset

Switchboard Dialogue Act Corpus downloaded from here.

Data Preprocessing:

Mapping original act tags to 43 simplified DAMSL tags.

Tokenization and indexing of words.

Padding sequences to a maximum length of 150 tokens.

Tasks and Implementations

Task 1: BiLSTM Model

Model Architecture:

Embedding Layer

2 stacked BiLSTM layers

Fully Connected Layer

Training:

Cross-Entropy Loss

Adam Optimizer

Weight balancing experimented using class_weight from sklearn.

Observations:

Unbalanced training achieved ~30% accuracy.

Balanced training struggled; weighted loss did not significantly improve performance in this setting.

Task 2: Evaluation and Error Analysis

Evaluation:

Overall accuracy was computed.

Specific focus on minority classes ('br' and 'bf').

Confusion matrix built.

Findings:

Accuracy for 'br' improved with context.

'bf' accuracy remained low.

Example corrections showed how context improved classification of signals like "Excuse me" or "Pardon me".

Task 3: CNN-BiLSTM Context Model

Model Architecture:

Embedding Layer

CNN with multiple filter sizes (3, 4, 5)

Max Pooling

Fully Connected Layer

Two BiLSTM layers for sequential modeling

Final Dense Output Layer

Training:

Similar setup as the BiLSTM model.

Evaluation:

Overall accuracy evaluated.

Notable improvements on certain minority classes (e.g., 'br').

Provided examples where context fixed mistakes made by the base model.

Key Results

Context helped disambiguate utterances that depend on previous dialogue history.

Minority class 'br' (signal non-understanding) improved after context modeling.

'bf' (summarize/reformulate) remained difficult, likely due to very low sample size.

Example Fixes by Context Model

Sentence

True Label

Base Model Prediction

Context Model Prediction

Excuse me.

br

ad

br

Pardon me.

br

qy^d

br

The ones that what?

br

qy^d

br

Challenges Faced

Severe class imbalance.

Minor classes like 'bf', 'aap_am', 'arp_nd' very underrepresented.

Weighted loss training was sensitive and difficult to stabilize.

Future Improvements

Try data augmentation for minority classes.

Use pretrained language models (e.g., BERT) for better sentence embeddings.

Apply techniques like Focal Loss for handling imbalance more effectively.
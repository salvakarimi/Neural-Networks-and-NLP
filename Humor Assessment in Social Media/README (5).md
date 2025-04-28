
# Humor and Offense Rating Prediction with DistilBERT (Multi-Task Learning)

## Project Overview

This project explores predicting humor ratings from social media posts using DistilBERT models. It progressively applies different machine learning techniques to improve performance, including data preprocessing, augmentation, ensembling, and multi-task learning (MTL). 

The tasks are based on the **SemEval2021 HaHackathon** dataset.

Dataset Link: [HaHackathon Dataset](http://smash.inf.ed.ac.uk/hahackathon_data/hahackathon_data.zip)

Competition Site: [SemEval 2021 HaHackathon](https://competitions.codalab.org/competitions/27446)

---

## Tasks Completed

### Task 1: Single-Task DistilBERT Regression
- Trained a DistilBERT-based model to predict humor rating.
- Used Mean Squared Error (MSE) as the loss function.
- Optimizer: AdamW, Learning Rate: 2e-5.
- Performance: **Test MSE ~ 0.0119**

### Task 2: Preprocessing with Ekphrasis
- Applied social media-specific text cleaning using the Ekphrasis library.
- Result: Slightly worsened performance (**Test MSE ~ 0.0124**).

### Task 3: Data Augmentation
- Augmented training data using:
  - (a) **Synonym replacement** from WordNet.
  - (b) **Random word deletion**.
- Conclusion: Random deletion produced better generalization (**lower MSE**) compared to synonym replacement.

### Task 4: Ensembling
- Trained 3 different DistilBERT models with different random seeds.
- Averaged predictions across models.
- Result: Small improvement in stability but **slightly worse MSE (~0.0122)** compared to single model.

### Task 5: Multi-Task Learning (MTL)
- Trained a model to predict both **humor rating** and **offense rating** simultaneously.
- Balanced the two tasks by averaging their losses.
- Result: After fix, MTL slightly improved generalization compared to the original single-task model.

---

## How to Run

1. **Install dependencies:**
```bash
pip install torch transformers sklearn ekphrasis nlpaug tqdm
```

2. **Download and unzip dataset:**
```bash
wget http://smash.inf.ed.ac.uk/hahackathon_data/hahackathon_data.zip
unzip hahackathon_data.zip
```

3. **Train models by running each task notebook:**
- Task 1: Base single-task model
- Task 2: Preprocessing
- Task 3: Data augmentation
- Task 4: Ensemble training
- Task 5: Multi-task model training

---

## Main Dependencies
- Python 3.11+
- PyTorch
- Huggingface Transformers
- Scikit-learn
- Ekphrasis
- Nlpaug
- TQDM

---

## Project Structure

```
.
├── train_single_task.py       # Task 1: Train base regression model
├── preprocess_ekphrasis.py    # Task 2: Preprocessing with Ekphrasis
├── augment_data.py            # Task 3: Data augmentation
├── train_ensemble.py          # Task 4: Ensemble 3 models
├── train_multitask_model.py   # Task 5: Multi-task learning model
├── utils.py                   # Helper functions (tokenization, dataloaders)
├── README.md                  # Project documentation
└── hahackathon_data/          # Downloaded dataset
```

---

## Author
- Developed for Social Media Processing coursework.
- Based on guidelines and starter code provided in university labs.

---

## Notes
- **GPU is highly recommended** for training (e.g., Colab, local CUDA machine).
- Preprocessing, data augmentation, and MTL approaches have varying impact depending on the noise level and structure of social media text.
- Humor and offense are complex, subjective tasks that require careful handling of the dataset and models.

---

## License
MIT License (or educational use as per course guidelines).

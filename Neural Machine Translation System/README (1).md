
# Neural Machine Translation (NMT) — Vietnamese to English

This project implements a **Neural Machine Translation (NMT)** system using a **sequence-to-sequence (seq2seq)** model with **Luong-style attention**. It translates Vietnamese sentences into English using an LSTM-based encoder-decoder architecture.  
The project follows the design proposed in research papers by **Sutskever et al. (2014)** and **Cho et al. (2014)**.

---

## 📚 Project Structure
- `nmt_model.py`: Defines the `NmtModel` class, which includes:
  - Embedding layers for source (Vietnamese) and target (English) languages.
  - Encoder LSTM.
  - Decoder LSTM.
  - Optional Attention Layer (`Luong Attention`).
  - Training (`train_model`) and evaluation (`eval_process`) methods.
- `attention_layer.py`: Defines the custom `AttentionLayer` used when `use_attention=True`.
- `utils.py`: Includes data loading (`load_dataset`), sequence padding, and vocabulary dictionary (`LanguageDict`).
- `Lab1_2_NeuralMachineTranslation_Student.ipynb`: The Jupyter notebook where tasks are implemented.
- `data/`: Folder containing the source (`data.30.vi`) and target (`data.30.en`) datasets.

---

## 🛠 Key Features
- **Encoder**: Processes Vietnamese input sentences using an LSTM.
- **Decoder**: Generates English output sentences one word at a time.
- **Teacher Forcing** during training.
- **Luong Attention Mechanism** to dynamically focus on relevant parts of the input.
- **Evaluation using BLEU Score** to measure translation quality.

---

## 📺 Installation & Setup
```bash
# Clone the repository
git clone https://github.com/your_username/nmt-vietnamese-english.git
cd nmt-vietnamese-english

# Install required packages
pip install torch numpy sacrebleu
```

---

## 🚀 How to Run
1. **Prepare the Data**:  
   Ensure you have `data.30.vi` and `data.30.en` in a `data/` folder.

2. **Run Training and Evaluation**:
```bash
python main.py --source_path data/data.30.vi --target_path data/data.30.en --use_attention True
```
Or, if using the notebook:
- Open `Lab1_2_NeuralMachineTranslation_Student.ipynb`.
- Follow the tasks to train and evaluate the model.

---

## 📈 Results
| Model Version | Attention | BLEU Score |
|---------------|-----------|------------|
| Baseline (no attention) | ❌ | ~4.0 |
| With Attention | ✅ | ~12.0 |

✅ **Attention dramatically improves translation performance.**

---

## 🧠 Sample Translations
```
Input (Vietnamese): tôi yêu bạn
Predicted Translation: i love you
Reference Translation: i love you

Input (Vietnamese): bạn khỏe không ?
Predicted Translation: how are you ?
Reference Translation: how are you ?
```

---

## 📝 Tasks Completed
- **Task 1**: Implemented the encoder embeddings and LSTM layers.
- **Task 2**: Implemented the decoder inference loop (`decode_step`) and trained the model.
- **Task 3**: Implemented Luong-style attention mechanism.

---

## 📚 References
- Sutskever, Ilya, Oriol Vinyals, and Quoc V. Le. (2014) *Sequence to Sequence Learning with Neural Networks*.
- Cho, Kyunghyun et al. (2014) *Learning Phrase Representations using RNN Encoder-Decoder for Statistical Machine Translation*.
- Luong, Minh-Thang, Hieu Pham, and Christopher D. Manning. (2015) *Effective Approaches to Attention-based Neural Machine Translation*.

---

## 📩 Contact
For any questions or suggestions, feel free to reach out:
- **Email**: your_email@example.com
- **GitHub**: [your_username](https://github.com/your_username)

---

# 🌟 Thank you for checking out this project! 🌟

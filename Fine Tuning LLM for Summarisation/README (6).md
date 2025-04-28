
# T5 Fine-Tuning for Summarisation and Controlled Text Generation

This project demonstrates how to fine-tune a T5 model using the HuggingFace Transformers library for two main tasks:
1. **Summarisation** of BBC news articles from the XSum dataset.
2. **Controlled Text Generation** based on extracted keywords.

## Project Structure
- **Summarisation Task**: Fine-tune T5-small to generate single-sentence summaries of BBC articles.
- **Data Generation Task**: Fine-tune T5-small to generate new summaries from randomly extracted keywords.
- **Evaluation**: ROUGE metrics were used to evaluate the quality of generated summaries.

## Dataset
- [XSum Dataset](https://arxiv.org/pdf/1808.08745.pdf) - Extreme summarisation dataset consisting of BBC articles.

## Key Steps
1. **Exploratory Data Analysis**: Token count distributions and basic statistics.
2. **Preprocessing**:
   - For summarisation: Prefix input with `"summarize: "`.
   - For data generation: Randomly select 20 words from each summary.
3. **Fine-Tuning**:
   - Fine-tuned T5-small for 5 epochs.
   - Used AdamW optimizer and a learning rate of 2e-5.
4. **Evaluation**:
   - Summarisation evaluated with ROUGE-1, ROUGE-2, ROUGE-L, and ROUGE-Lsum.
   - Final loss after 5 epochs (data generation): ~3.78.

## Results
### Summarisation Task
- Fine-tuned model produced more focused but sometimes repetitive summaries.
- Fine-tuning improved ROUGE scores compared to the generic model.

### Data Generation Task
- Final loss after five epochs: **3.78**
- Generated text from keywords was not meaningful (keywords were echoed without natural sentence formation).
- Suggests that better keyword extraction and more structured training data are needed for effective data generation.

## Example Outputs

### Summarisation (Fine-tuned Model)
- **Input**: Full BBC article text.
- **Output**: "A flood warning has been issued in the area after the floods in Newton Stewart caused a flood warning and a flood warning."

### Data Generation from Keywords
- **Input Keywords**: `"damage ongoing Hawick disruption Lamington viaduct commercial thoroughfare multi-agency neglected"`
- **Generated Output**: `"Hawick disruption Lamington viaduct commercial thoroughfare multi-agency neglected"`

## Future Improvements
- Use phrase or key chunk extraction instead of random words for data generation.
- Fine-tune for more epochs with better regularization.
- Apply advanced decoding techniques like beam search to improve output quality.

## Installation Requirements
```bash
pip install torch transformers datasets evaluate nltk
```

## Acknowledgments
- Hugging Face for the pre-trained T5 model and datasets.
- BBC for the XSum dataset used for summarisation tasks.

---

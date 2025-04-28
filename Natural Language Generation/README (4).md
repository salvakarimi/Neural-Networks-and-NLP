
# Natural Language Generation Project

This project explores different text generation methods using the GPT-2 language model from Hugging Face's `transformers` library. We implement and compare various decoding strategies, including greedy search, beam search, and sampling-based approaches.

## Project Structure

- **Task 1: Greedy Search**
  - Implemented a greedy search algorithm that selects the most probable next word at each timestep.
  - Compared the output and log probability with Hugging Face's built-in greedy search.

- **Task 2: Beam Search**
  - Implemented beam search maintaining top-k hypotheses.
  - Compared generated sequences and their log probabilities with greedy search.
  - Observed that beam search reduced repetition slightly but sometimes still led to repetitive outputs.

- **Task 3: Beam Search with Repetition Penalty**
  - Extended beam search to apply a repetition penalty by heavily penalizing previously used tokens.
  - Compared outputs with Hugging Face's `no_repeat_ngram_size=2` feature.
  - Noted that while repetition was reduced, coherence sometimes suffered.

- **Sampling Methods:**
  - **Random Sampling:** High diversity, low coherence.
  - **High Temperature Sampling:** Very high diversity, chaotic output.
  - **Low Temperature Sampling:** High coherence, low diversity (repetitive).
  - **Top-p (Nucleus) Sampling:** Best balance of coherence and diversity.

## Key Observations

- Greedy search is fast but prone to local repetition.
- Beam search improves probability optimization but can still repeat without penalties.
- Repetition penalties help reduce loops but must be carefully balanced to maintain coherence.
- Sampling strategies (especially Top-p) are effective at balancing creativity and fluency.

## How to Run

1. Install necessary packages:
   ```bash
   pip install torch transformers
   ```
2. Run the provided Python scripts for each task individually.

## Credits

- Based on course materials and Hugging Face's GPT-2.
- Research references: Paulus et al. (2017), Klein et al. (2017).

---

*Created as part of a university assignment on Natural Language Generation (NLG).*

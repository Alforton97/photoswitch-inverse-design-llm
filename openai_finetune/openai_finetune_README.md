# OpenAI Fine-Tuning (GPT-4o-mini)

This folder documents the process of fine-tuning a GPT-4o-mini model using the OpenAI API platform for inverse molecular design on the Photoswitch dataset.

## Model Used

- `gpt-4o-mini-2024-07-18`

## Fine-Tuning Runs

Two fine-tuning runs were conducted using JSONL-formatted SMILES–wavelength pairs prepared via preprocessing.

### Run 1
- Trained tokens: 144,445
- Epochs: 5
- Batch size: 2
- Learning rate multiplier: 0.1
- Seed: 42

### Run 2
- Trained tokens: 86,667
- Epochs: 3
- Batch size: 2
- Learning rate multiplier: 0.05
- Seed: 42

## Prompt-Based Generation

After fine-tuning, the model was used via the OpenAI Chat API to generate SMILES strings conditioned on desired E isomer π–π* absorption wavelengths.

The prompt history is documented in [`prompt_history.md`](prompt_history.md), which includes a set of example prompts and generated outputs. This helps evaluate how well the fine-tuned model adheres to wavelength constraints in inverse molecular design.

## Notes

- All fine-tuning and generation were done via the [OpenAI API Platform](https://platform.openai.com/).
- No API keys or private data are included in this repository.
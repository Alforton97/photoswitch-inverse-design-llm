# Kaggle Fine-Tuning Attempt (DeepSeek R1)

This notebook documents an attempt to fine-tune an open-source LLM model on the Photoswitch dataset using the Kaggle notebook environment.

## Contents

- **Data Preprocessing**: The notebook begins by loading the original CSV-formatted Photoswitch dataset and transforming it into the JSONL format required by OpenAI-compatible fine-tuning.
- **Fine-Tuning Trial**: The fine-tuning process uses the model [`deepseek-ai/deepseek-r1-distill-qwen-1.5b`](https://huggingface.co/deepseek-ai/deepseek-r1-distill-qwen-1.5b), a 1.5B parameter distilled model designed for general-purpose tasks.

## Environment

This experiment was conducted in a Kaggle notebook environment (2 × T4 GPUs).  
Due to compute limitations, the training process could not be completed within the available kernel time.

## Notes

Although the model was not successfully fine-tuned to completion, this experiment allowed exploration of:

- Prompt and SMILES formatting for inverse design
- Token and memory footprint of different prompt templates
- GPU memory and batch size trade-offs
- Dataset preparation under open LLMs

See [`photoswitch.ipynb`](photoswitch.ipynb) for full code.
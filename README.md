# Photoswitch Inverse Design via LLM Fine-Tuning

## Overview

This project explores the use of large language models (LLMs) for inverse molecular design, specifically focusing on the Photoswitch dataset. It follows and partially reproduces the approach presented in the following paper:

> Jablonka, K.M., Schwaller, P., Ortega-Guerrero, A. et al.  
> *Leveraging large language models for predictive chemistry.*  
> *Nat Mach Intell 6, 161–169 (2024).*  
> https://doi.org/10.1038/s42256-023-00788-1

The paper describes how an LLM can be fine-tuned on molecular structure–property pairs (e.g., SMILES + absorption wavelength) to learn inverse mappings. My goal in this project was to test this methodology using the publicly available **Photoswitch Dataset**, and evaluate the fine-tuned model's ability to generate molecules matching desired optical properties.

## Dataset

This project uses the Photoswitch Dataset provided by Ryan-Rhys Griffiths et al.  
GitHub: [Ryan-Rhys/The-Photoswitch-Dataset](https://github.com/Ryan-Rhys/The-Photoswitch-Dataset)

If you use the dataset, please cite:

> Griffiths, R.-R. et al.  
> *Data-driven discovery of molecular photoswitches with multioutput Gaussian processes.*  
> *Chemical Science, 13(45), 13541–13551 (2022).*  
> https://doi.org/10.1039/D2SC03840C

BibTeX:

@article{2022Griffiths,
  title={Data-driven discovery of molecular photoswitches with multioutput Gaussian processes},
  author={Griffiths, Ryan-Rhys et al.},
  journal={Chemical Science},
  volume={13},
  number={45},
  pages={13541--13551},
  year={2022},
  publisher={Royal Society of Chemistry}
}

## What This Project Does

- Converts the Photoswitch dataset into OpenAI fine-tuning format (`prompt` + `completion` JSONL)
- Tries to fine-tune DeepSeek R1-1.5B on Kaggle (failed due to time/memory limits — included for transparency)
- Successfully fine-tunes OpenAI GPT-4o-mini using their web UI and API
- Generates SMILES strings conditioned on target E isomer π–π* absorption wavelengths
- Trains a Gaussian Process model to predict absorption from SMILES (based on the dataset author's official notebook)
- Uses the model to evaluate generated SMILES by checking whether the predicted wavelength falls within ±20nm of the prompt

## Folder Structure

photoswitch-inverse-design-llm/

├── kaggle_finetune/       # DeepSeek R1 trial (not completed)  
├── openai_finetune/       # OpenAI fine-tune and generation  
├── evaluation/            # Gaussian Process property prediction  


## Motivation

This project was conducted as a personal attempt to connect modern LLM techniques with real chemical data, and explore the practical pipeline from inverse design to data-driven evaluation. Despite limited computational resources, I was able to complete the fine-tuning and validation using open tools, and learned extensively about prompt design, model evaluation, and property conditioning via language.

## Status

✅ Fine-tuning on OpenAI GPT-4o-mini completed  
✅ Sample generation tested  
✅ Evaluation pipeline with GP regression validated  
❌ Fine-tuning on DeepSeek (Kaggle) was attempted but not successful due to time/resource limits

## License and Credits

All molecular data is from the [Photoswitch Dataset](https://github.com/Ryan-Rhys/The-Photoswitch-Dataset), licensed by the original authors.  
All fine-tuning performed on public tools (OpenAI, Kaggle). This repository is for academic demonstration and learning purposes only.
# Evaluation via Gaussian Process Regression

This folder documents the evaluation of LLM-generated SMILES using a Gaussian Process Regression (GPR) model trained to predict E isomer π–π* absorption wavelengths.

## Method

The GPR model was implemented based on the official example from the Photoswitch Dataset repository:

> https://github.com/Ryan-Rhys/The-Photoswitch-Dataset/blob/master/examples/gp_regression_on_molecules.ipynb

- Input: SMILES strings
- Output: Predicted π–π* transition wavelength (E isomer)
- Model performance:
  - **Average Validation R²: 0.883 ± 0.023**

## Evaluation of Fine-Tuned Models

The trained GPR model was used to evaluate the outputs of the fine-tuned LLMs by checking whether the predicted absorption wavelength fell within ±20nm of the conditioning prompt.

### GPT-4o-mini fine-tuning results:

#### Run 1
- Trained tokens: 144,445
- Epochs: 5
- Batch size: 2
- LR multiplier: 0.1
- **Hit rate (±20nm): 66.7%**

#### Run 2
- Trained tokens: 86,667
- Epochs: 3
- Batch size: 2
- LR multiplier: 0.05
- **Result: Many generated SMILES were invalid or unparsable**

## Conclusion

The evaluation shows that a well-tuned LLM can generate molecules matching desired optical properties at a reasonable success rate. The GP-based model provided a lightweight but effective method to validate SMILES when experimental spectra are unavailable.

See [`gp_regression.ipynb`](gp_regression.ipynb) for full code and results.
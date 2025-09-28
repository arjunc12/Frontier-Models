# Evaluating GPT on Mathematical Sciences Problems

This repository is an experimental prototype exploring how well GPT models can solve a mathematical optimization problem from my recent paper in *Mathematics Magazine*, supported by the NSF Division of Mathematical Sciences.  

The goal is not only to test whether GPT can reproduce the analytic solution, but also to prototype an **evaluation loop** for mathematical problem-solving with large language models (LLMs). This includes prompt design, reproducibility, sensitivity to hyperparameters, and manual scoring of outputs.  

---

## Motivation

Mathematics poses a unique challenge for LLMs: correctness requires precise symbolic reasoning rather than approximate or stylistic answers. By testing GPT on a published problem where the analytic solution is known, this project aims to:

- Explore whether GPT can derive (or approximate) the solution.
- Investigate how prompt design and token limits affect output quality.
- Prototype a lightweight evaluation workflow combining LLM outputs with human scoring.
- Demonstrate how AI evaluation methods can be connected to established problems in the mathematical sciences.

This kind of experiment illustrates how one might begin developing **benchmarks for LLMs in theoretical domains**, a key challenge for scientific deployment of AI.

---

## Repository Contents

- **`FrontierModels.ipynb`** — Jupyter notebook containing the core evaluation workflow.  
- **`gpt_math_evan.csv`** — Data file where prompt/response pairs, scores, and hyperparameters are logged.  
- **`README.md`** — This document.  

---

## Dependencies

- Python 3.11  
- [openai](https://pypi.org/project/openai/) version 1.109.1  
- [pandas](https://pandas.pydata.org/)  
- [seaborn](https://seaborn.pydata.org/)  

I recommend using [conda](https://docs.conda.io/) with the `-c conda-forge` channel to set up your environment.

---

## Setup

1. Create an OpenAI account: [https://platform.openai.com/](https://platform.openai.com/).  
2. Generate an API key from your account settings.  
3. (Optional but recommended) Save the key as a system environment variable:  
   ```bash
   echo 'export OPENAI_API_KEY="sk-..."' >> ~/.zshrc
   source ~/.zshrc
4. Launch JupyterLab and open `FrontierModels.ipynb`.

Usage
- Customize your prompts inside the notebook.
- Call the evaluate_prompt method to:
    - Run your prompt through GPT,
    - View the model’s response,
    - Assign a manual score (0, 0.5, 1),
    - Provide feedback on the response.
- Each run appends a row to gpt_math_evan.csv, logging:
    - Prompt
    - Response
    - Score
    - Feedback
    - Hyperparameters (temperature, max tokens)

At the end of the notebook, you can visualize how hyperparameters affect performance using pandas and seaborn.

## Preliminary Observations
- GPT often produces partial reasoning or descriptive solutions rather than the full analytic formula.
- Increasing token limits sometimes improves the completeness of responses, but does not guarantee correctness.
- Prompt phrasing has a significant effect on whether the model attempts symbolic derivations.

## Citation

If you use this repo as inspiration, please cite the original publication:

Altman, K., Koenig, A., Julkowska, M., Lobet, G., Chandrasekhar, A., & Richards, K. (2025). Gottfried Green Tomatoes: Using Leibniz’s Rule to Find the Roots of Tomato Plant Equations. *Mathematics Magazine*, 1–12.  

Supported by the NSF Division of Mathematical Sciences.

### BibTeX
```bibtex
@article{altman2025gottfried,
  title={Gottfried Green Tomatoes: Using Leibniz’s Rule to Find the Roots of Tomato Plant Equations},
  author={Altman, K. and Koenig, A. and Julkowska, M. and Lobet, G. and Chandrasekhar, A. and Richards, K.},
  journal={Mathematics Magazine},
  pages={1--12},
  year={2025}
}
```
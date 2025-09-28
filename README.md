# Frontier-Models
Experimental repository to partially automate testing how well AI can solve a problem from [a recent paper in Mathematics Magazine](https://www.tandfonline.com/doi/full/10.1080/0025570X.2025.2506969).

# Dependencies

This code uses python 11 and it uses openai version: 1.109.1. I am also using Pandas and Seaborn for data curation and analysis.

# Setup

After creating the right environment, you must do the following:
1. Set up an account on [https://platform.openai.com/](https://platform.openai.com/) and create an access token.
2. (Optional but recommended) run the following code to create a system variable for your access token.
```
echo 'export OPENAI_API_KEY="sk-..."' >> ~/.zshrc
source ~/.zshrc
```
3. Customize your own prompts and run the cells in `FrontierModels.ipynb`. Whenever you call the `evaluate_prompt` method, it will run your prompt through Chat GPT and then ask you to evaluae that prompt on a score from 0-1, and give feedback on the prompt. At the end it will write information to the file `gpt_math_evan.csv`, including the prompt, response, score, feedback, as well as the temperature and max tokens used as hyperparameters for constraining the GPT model responses.
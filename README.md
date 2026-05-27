# True-but-misleading LLM pragmatic reasoning 

This repository contains code, data, and results for a small-scale evaluation of true-but-misleading response selection in instruction-tuned language models. The project tests whether models recognise misleading pragmatic inferences, whether they select true-but-misleading responses under goal conflict, and whether prior listener-side evaluation modulates later speaker-side response selection.

# Contents: 

true-but-misleading-llm/
  README.md
  requirements.txt
  data/
    pilot_scenarios.json
  notebooks/
    01_run_qwen7b_main.ipynb
    02_run_neutral_control.ipynb
    03_analysis.ipynb
  results/
    qwen7b_randomised_results.csv
    qwen7b_neutral_control_results.csv

# Data 

The scenario dataset is stored in:

data/pilot_scenarios.json

# Models

All models were run locally through Ollama. 

The main reported model is:

Qwen2.5-7B-Instruct

Preliminary runs were also carried out with:

Qwen2.5-3B-Instruct

# Setup

Install dependencies:

pip install -r requirements.txt

Install Ollama from: 

https://ollama.com

Pull the main model: 

ollama pull qwen2.5:7b-instruct

# Reproducing experiments

Run notebooks in the following order: 

01_run_qwen_7b.ipynb,
02_run_neutral_2_step.ipynb,
03_results_analysis.ipynb,
04_boostrap_ci.ipynb

# Output files

The main output files are: 

results/qwen7b_randomised_results.csv
results/qwen7b_neutral_control_results.csv

The CSV files contain the prompts, raw model responses, parsed choices, randomised letter-to-option mappings, and scored option identifiers.

# Decoding and randomisation

Experiments used deterministic decoding with temperature set to 0.0.
Answer-option order was randomised using a fixed random seed. The letter-to-option mapping was stored for every trial so that responses could be scored by option type rather than by surface letter.

# Notes

The saved result files are included so that the main analyses can be reproduced without rerunning the model.

# quantum-forge
  

Quantum Forge is a small hybrid quantum-classical experiment built using the Moth Quantum API. 

  

The idea is simple: use the Moth QPU to generate different candidate configurations, then use classical Python code to check those configurations against a problem and choose the best one. 

  

**How it works** 

  

The workflow used in this notebook is: 

  

Problem definition -> QPU-generated candidates -> Classical evaluation -> Best feasible configuration 

  

For this first experiment, I used a small resource-selection problem. 

  

There are four resources: 

  

- Solar Panel 

- Battery 

- Sensor 

- Controller 

  

Each resource has a value and a cost, and the total budget is 6. 

  

A 4-bit string represents a possible selection. For example: 

  

"1010" 

  

means: 

  

- Solar Panel: selected 

- Battery: not selected 

- Sensor: selected 

- Controller: not selected 

  

The Moth "graph-v1" QPU generates different bitstrings with different probabilities. I then evaluate those candidates classically by calculating their total value and cost and removing configurations that exceed the budget. 

  

**Example result**

  

In the final QPU run, the most frequently measured configuration was: 

  

"0011" -33.59% 

  

However, the best feasible configuration was: 

  

"1010" - 3.91% 

  

This configuration selected: 

  

- Solar Panel 

- Sensor 

  

with: 

  

- Total value: 15 

- Total cost: 6 

- Budget: 6 

  

So Quantum Forge selected "1010" as the forged result even though it was not the most frequently measured configuration. 

**Important note** 

This experiment does not claim that the QPU directly solved the optimization problem or demonstrated quantum advantage. 

The purpose of this prototype is to explore a hybrid workflow where QPU measurements provide candidate configurations and classical computation evaluates those candidates for a specific problem. 

**Running the notebook** 

You need: 

Python 

Jupyter Notebook or Google Colab 

requests 

A Moth Quantum API key 

Set your API key as an environment variable: 

MOTH_API_KEY=your_api_key 

The notebook uses the key through: 

os.environ["MOTH_API_KEY"] 

Do not put your actual API key inside the notebook or commit it to GitHub. 

**Notebook**

The complete experiment is available in: 

quantum_forge.ipynb

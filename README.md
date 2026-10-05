# quantum-forge
  

Quantum Forge is a small hybrid quantum-classical experiment built using the Moth Quantum API. 

  

The idea is simple: use the Moth QPU to generate different candidate configurations, then use classical Python code to check those configurations against a problem and choose the best one. 

  

How it works 

  

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

  

Example result 

  

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

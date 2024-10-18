---
title: "GRI Mechanism Reduction"
excerpt: "Mechanism Reduction using Python "
collection: portfolio
---

**Reaction Mechanisms:** 

In chemistry, a reaction mechanism is the step by step sequence of elementary reactions by which overall chemical change occurs. It is a theoretical compilation that explains in detail what happens at every stage of a chemical reaction. This mechanism is chosen because it is thermodynamically feasible, and has experimental support in isolated species (Intermediate) or other quantitative and qualitative characteristics of the reaction.
 
In the current project, we are using GRI 3.0 reaction mechanism which is an optimized mechanism designed to model natural gas combustion, including NO formation and reburn chemistry.
 
**Mechanism Reduction:**

Mechanism Reduction is a process where we remove redundant reactions from the mechanim with respect to our problem parameters. This helps us to customize or tune the mechanism to our specifc requirements so that we have the accurate results pertainning to the problem we are solving. For example, we can reduce a mechanism depending on the specific range of operating conditions we want for the fuel.
Based on the study of hydrocarbons combustion using detailed reaction mechanisms, is an important research area of combustion chemistry. The detailed mechanisms consist of hundreds of chemical species and thousands of reaction steps.
The size of the detailed combustion kinetics mechanisms for surrogates of real fuels makes impossible massive design studies with CFD tools.
 
Types of Mechanisms and their Applications: 

1. Detailed:
	- Hundreds of species, thousands of reactions for typical Hydrocarbon fuels
	- Supposed to work in a wide range of conditions
	- But further work is to be implemented with tests
2. Skeletal:
	- Tens of species, Thousands of reactions for typical Hydrocarbon fuels
	- Derived from detailed mechanism by removing redundant species and reactions
	- Derived for narrow range of conditions, sometimes for specific problems
	- Should be tested at desired range of conditions
3. Reduced:
	- Tens of species and reactions for typical Hydrocarbon fuels
	- Derived from Detailed/Skeletal mechanisms by application of Quasi Steady State or Quasi Equilibrium approximations
	- Derived for narrow range of conditions, sometimes for specific problem
	- Should be tested at desired range of conditions
4. Global:
	- Can not be directly derived from previous mechanisms, just a simple model
	- Can be applied for restricted range of conditions, only for one type of problem
	- Must be tested every time before applications

The project entails a Python program which performs a chemical reaction mechanism reduction using the Cantera library. 
This is an introductory code on reduction and its effects on different cases. 

It does the following:

1. **Parses Reduction Parameters:** It reads reduction parameters like temperature, pressure, and equivalence ratio from a file `Reduction_Parameters.txt`, storing these in a dictionary.
2. **Simulates Ignition Delay and Temperature:** For different initial conditions (temperature, pressure, and fuel mixture), it sets up a constant pressure reactor to simulate the ignition process,         calculates the ignition delay (time it takes for a significant temperature rise), and records the maximum temperature.
3. **Sensitivity Analysis:** The program uses sensitivity analysis for reactions in the mechanism to determine their importance.
4. **Mechanism Reduction:** It removes unimportant reactions to create a reduced chemical mechanism and reruns the simulation with this reduced mechanism.
5. **Plots Results:** It generates and saves plots comparing ignition delay and maximum temperature against the number of reactions for each test case.

The resulting test cases data is shown below:

| Case number | Temperature (Kelvin) | Pressure (Bar) | Equivalence Ratio (No Units) | Reduced mechanism for Ignition Delay (Number of reactions) | Reduced mechanism for Maximum Temperature (Number of reactions) |
|-------------|----------------------|----------------|-----------------------------|-------------------------------------------------------------|------------------------------------------------------------------|
| 1           | 950                  | 3              | 0.5                         | 72                                                          | 163                                                              |
| 2           | 950                  | 3              | 1                           | 62                                                          | 164                                                              |
| 3           | 950                  | 3              | 1.5                         | 63                                                          | 245                                                              |
| 4           | 950                  | 4              | 0.5                         | 71                                                          | 155                                                              |
| 5           | 950                  | 4              | 1                           | 65                                                          | 199                                                              |
| 6           | 950                  | 4              | 1.5                         | 58                                                          | 230                                                              |
| 7           | 950                  | 5              | 0.5                         | 65                                                          | 157                                                              |
| 8           | 950                  | 5              | 1                           | 67                                                          | 208                                                              |
| 9           | 950                  | 5              | 1.5                         | 60                                                          | 244                                                              |
| 10          | 1050                 | 3              | 0.5                         | 49                                                          | 180                                                              |
| 11          | 1050                 | 3              | 1                           | 43                                                          | 167                                                              |
| 12          | 1050                 | 3              | 1.5                         | 99                                                          | 218                                                              |
| 13          | 1050                 | 4              | 0.5                         | 57                                                          | 208                                                              |
| 14          | 1050                 | 4              | 1                           | 44                                                          | 164                                                              |
| 15          | 1050                 | 4              | 1.5                         | 63                                                          | 240                                                              |
| 16          | 1050                 | 5              | 0.5                         | 83                                                          | 147                                                              |
| 17          | 1050                 | 5              | 1                           | 52                                                          | 158                                                              |
| 18          | 1050                 | 5              | 1.5                         | 65                                                          | 231                                                              |
| 19          | 1150                 | 3              | 0.5                         | 50                                                          | 149                                                              |
| 20          | 1150                 | 3              | 1                           | 72                                                          | 257                                                              |
| 21          | 1150                 | 3              | 1.5                         | 66                                                          | 262                                                              |
| 22          | 1150                 | 4              | 0.5                         | 57                                                          | 192                                                              |
| 23          | 1150                 | 4              | 1                           | 57                                                          | 212                                                              |
| 24          | 1150                 | 4              | 1.5                         | 63                                                          | 261                                                              |
| 25          | 1150                 | 5              | 0.5                         | 48                                                          | 173                                                              |
| 26          | 1150                 | 5              | 1                           | 68                                                          | 226                                                              |
| 27          | 1150                 | 5              | 1.5                         | 69                                                          | 252                                                              |

If you are interested more, check out my project [here](https://github.com/UjjwalKanthN/GRI-Mechanism-Reduction).
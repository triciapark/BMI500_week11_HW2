# BMI500 Week 11 Homework

Name: Tricia Park

Contact: tricia.park@emory.edu

*Disclaimer: No generative AI (in any form) has been used to complete this homework.*

## HW Question: #2 Agent-Based Modeling of Pandemic Spread

### Methods

To keep track of the agents and their positions, a `pandas DataFrame` object was created and populated with the agents and random starting positions. Next, methods for random movement, transmission with probability *p*, and recovery with probability *q* were implemented, as well as methods for simulation over *n* steps and plotting the number of agents in each of the three subgroups over time. For sentivity analysis, different values of *p* (0.05, 0.1) and *q* (0.02, 0.05) were tested. Different starting proportions of infected agents were also compared.

A second movement method was implemented to simulate movement with social distancing, adding a probability of staying in place (*m*) and avoidance behavior. The sensitivity analysis for the social distancing simulation tested different values of *m* (0.1, 0.5, 0.7).

Simulations were run for a 75x75 grid with 100 agents and also with 1000 agents to increase the probability of agents running into each other.

### Key insights

Simulating the agent-based model over 200 steps with 100 agents (5% started infected) showed that the model eventually reached a stable recovered state where there were no more infected agents, and that the number of infected agents and the number of recovered agents were inversely related (Plot 1). The number of susceptible agents did not change much due to the low probability of the agents running into each other, so an additional simulation with 1000 agents (5% started infected) was performed. More agents were infected compared to when there were only 100 agents, as shown by Plot 2, but as before a stable state was eventually reached once there were no more infected agents.

The sensitivity analysis for different values of *p* and *q* demonstrates that increasing values of *p* increase the number of infections (Plot 3) and decreasing values of *q* slow down the overall population recovery (Plot 4), causing the model to reach the steady state slower. Additionally, a comparison of simulations with different starting proportions of infected agents also slowed down overall population recovery (Plots 5, 6, and 7).

Introducing social distancing measures changed the model. The following table shows some metrics comparing the expanded social distancing model (Plot 8) with the original base model (Plot 2):

|  | Social Distancing Model | Base Model |
| ----------- | ----------- | ----------- |
| Peak infected | 56 | 126 |
| Step at peak infected | 4 | 20 |
| Peak recovered | 150 | 595 |
| Step at peak recovered | 135 | 240 |

From the table, it is clear that implementing social distancing decreased the peak number of infected agents and that the peak was reached faster than without social distancing. Furthermore, social distancing resulted in the model reaching the stable state much faster than in the base model. Because the agents were more likely to stay in place and avoided infected agents, there was a lower chance of agents running into each other and less transmission. This is applicable to real-world public health interventions because it shows that social distancing decreases the spread of infectious diseases, allowing experts and officials to encourage people to stay home during pandemics such the COVID-19 pandemic.

The sensitivity analysis for varying values of *m* demonstrates that as more agents stay in place, the overall population recovery increases. The final number of recovered agents at the steady state was lower in Plot 10 (*m*=0.5) than in Plot 9 (*m*=0.1), and lower in Plot 11 (*m*=0.7) than in Plot 10 (*m*=0.5). 1000 agents (30% started infected) were used to simulate the sentivity analysis to better show the effectiveness of social distancing, especially for areas with greater population density.

### Comparative model performance

This agent-based model simulates the spread of infections diseases through the use of agents, which represent individuals with certain behaviors. Compared to other models that simulate pandemic spread dynamics (e.g. compartmental model as in HW question #1), agent-based models are better for examining community-level dynamics and is easier to understand for those who are not experts on compartmental models, which use potentially confusing mathematical equations. On the other hand, it has some limitations in that the simulations may differ greatly depending on the initial conditions, meaning that it may potentially be easy to manipulate to show certain conclusions. Also, statistical analysis such as confidence intervals is more difficult to do compared to compartmental models.

### Relevance to model-based machine learning

This agent-based model can be used in machine learning models. For example, the simulation results could be used to train a model that determines the optimal initial parameters given certain criteria. In addition, the model could be used to generate simulated data so that researchers do not need to gather real-world data, which can be expensive, time-consuming, and unethical.

### Suggestions for future modeling improvements

The following are some implementation ideas for further modeling improvements:
- Agents becoming susceptible again after recovery
- Mask wearing
- Vaccination status
- Agent death due to pandemic
- Changes in social distancing measures (e.g. relaxed at first but then becomes strict)
- Certain agents living together
- Hotspot areas (e.g. grid position that represent school, office, etc.)
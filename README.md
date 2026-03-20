# Reinforcement Learning on Cliff Walking (SARSA vs Q-Learning)

## Overview

This project implements and compares two fundamental reinforcement learning algorithms—SARSA (on-policy) and Q-Learning (off-policy)—using the Cliff Walking environment from Gymnasium. The goal is to train an agent to navigate a grid world from start to goal while avoiding falling off a cliff, highlighting how different learning strategies impact behavior and performance.

## Objectives

- Implement SARSA and Q-Learning algorithms from scratch using Python.
- Understand the difference between on-policy and off-policy learning.
- Analyze how agents behave in risky environments like Cliff Walking.
- Compare convergence, stability, and path selection of both algorithms.

## Tools & Technologies

- **Python**: Core programming language
- **NumPy**: Numerical computations and Q-table handling
- **Gymnasium**: Reinforcement learning environment (CliffWalking-v1)
- **Jupyter Notebook**: Development and experimentation

## Dataset / Environment

### Name
Cliff Walking Environment

### Source
Gymnasium (CliffWalking-v1)

### Grid Size
4 × 12 (48 states)

### Start State
Bottom-left corner

### Goal State
Bottom-right corner

### Cliff Region
Cells between start and goal

### Rewards
- **Step**: -1
- **Cliff**: Large negative reward + reset to start
- **Goal**: Episode termination

## Methodology

1. **Environment Setup**
   - Created using Gymnasium's toy-text environment.
   - Agent interacts with states, actions, rewards, and transitions.
   - ε-greedy policy used for balancing exploration vs exploitation.

2. **SARSA (On-Policy Learning)**
   - Updates Q-values based on actual actions taken.
   - Formula:
     $$
     Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma Q(s', a') - Q(s,a)]
     $$
   - Learns safer paths by considering exploration behavior.
   - Key Behavior:
     - Avoids cliff region
     - More stable but slower convergence

3. **Q-Learning (Off-Policy Learning)**
   - Updates Q-values using the best possible next action.
   - Formula:
     $$
     Q(s,a) \leftarrow Q(s,a) + \alpha [r + \gamma \max_{a'} Q(s', a') - Q(s,a)]
     $$
   - Learns optimal policy independent of actual actions taken.
   - Key Behavior:
     - Chooses shortest path (often near cliff)
     - Faster convergence but riskier

4. **Training Process**
   - Initialize Q-table with zeros
   - Run multiple episodes
   - Update Q-values iteratively
   - Apply ε-greedy strategy
   - Track rewards and convergence

## Model Evaluation

| Metric              | SARSA          | Q-Learning     |
|---------------------|----------------|----------------|
| Learning Type       | On-policy      | Off-policy     |
| Path Behavior       | Safer (avoids cliff) | Risky (near cliff) |
| Convergence Speed   | Slower         | Faster         |
| Stability           | More stable    | Less stable in risky env |

## Key Insights & Findings

- **Policy Difference Matters**: SARSA learns based on actual experience, while Q-learning assumes optimal actions.
- **Risk Sensitivity**: SARSA avoids dangerous states due to exploration influence, whereas Q-learning aggressively optimizes reward.
- **Environment Impact**: In risky environments like Cliff Walking, on-policy methods can outperform in safety-critical scenarios.
- **Exploration Strategy**: ε-greedy plays a crucial role in balancing learning efficiency and safety.

## Future Scope

- Implement Deep Q-Networks (DQN) for larger state spaces
- Compare with Monte Carlo methods
- Tune hyperparameters (α, γ, ε) for performance optimization
- Visualize learned policies using heatmaps
- Extend to more complex environments like FrozenLake or Taxi

## Repository Structure

```
├── SARSA_CliffWalking.ipynb
├── QLearning_CliffWalking.ipynb
├── README.md
```

## Q-Learning Training Phase Video

Below is a video showcasing the Q-Learning training phase (reward accumulation, policy evolution, and episode performance curves).

<video controls width="640">
  <source src="Qlearning_training.mp4" type="video/mp4">
  Your browser does not support HTML5 video. Alternatively, [click here to open the video](Qlearning_training.mp4).
</video>


## Working Demo Image

![CliffWalking Working Demo](cliffwalking_demo.png)

> Screenshot of the trained agent navigating the Cliff Walking environment (working code execution view).

## Conclusion

This project demonstrates how different reinforcement learning strategies influence agent behavior. While Q-Learning finds optimal paths faster, SARSA prioritizes safety, making it more suitable for environments with high risk.
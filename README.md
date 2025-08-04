# RL-ASSIGNMENT-3--ON-GRIDWORLD-SARSA-VS-Q-LEARNING
This project provides an implementation and comparison of two reinforcement learning algorithms: SARSA and Q-Learning

The implementation uses a 5x5 gridworld environment where an intelligent agent must learn to navigate from a starting position to terminal goal states while avoiding penalty zones.

- ## The Problem description and environment:
  
The environment consists of a 5x5 grid with several distinct types of states that create an interesting learning challenge. The agent begins at a blue square located at position (4,0) in the bottom-left corner of the grid. The goal is to reach one of two black terminal states located at positions (0,0) and (0,4), which provide a substantial reward of +100 points upon arrival.
The environment includes red penalty states positioned at (2,0), (2,1), (2,3), and (2,4), which form a barrier across the middle of the grid. When the agent enters any of these red states, it receives a penalty of -20 points and is immediately reset to the starting position, making these states particularly challenging to navigate around. Additionally, every regular movement incurs a small penalty of -1 point, encouraging the agent to find efficient paths to the goal. This reward structure creates a natural trade-off between speed and safety, as the agent must balance avoiding penalties with reaching the goal quickly.

- ## Learning Algos and implementation:
  
SARSA (State-Action-Reward-State-Action) is an on-policy algorithm that updates its value estimates based on the actions actually taken by the current policy. This makes SARSA more conservative in its learning approach, as it considers the exploration strategy when updating values. The algorithm follows the update rule Q(s,a) ← Q(s,a) + α[r + γQ(s',a') - Q(s,a)], where the future value estimate comes from the action that will actually be taken in the next state.
Q-Learning, in contrast, is an off-policy algorithm that updates its value estimates based on the maximum possible value of the next state, regardless of which action will actually be taken. This optimistic approach often leads to faster convergence to the optimal policy, as it assumes the agent will always choose the best possible action in future states. The Q-Learning update rule is Q(s,a) ← Q(s,a) + α[r + γ max_a'Q(s',a') - Q(s,a)], where the future value estimate always uses the maximum Q-value available in the next state.
Both algorithms use an epsilon-greedy action selection strategy that balances exploration and exploitation. The exploration rate starts at 1.0 (pure exploration) and gradually decays to 0.01 (mostly exploitation) using a decay factor of 0.995. This gradual transition allows the agent to explore the environment thoroughly in early episodes while converging to optimal behavior as learning progresses.


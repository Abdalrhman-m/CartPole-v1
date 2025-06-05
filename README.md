# CartPole-v1

Project Title : Deep Q-Network (DQN) for CartPole-v1 with PyTorch and Gymnasium

Introduction

This repository presents a comprehensive project focused on the implementation of a Deep Q-Network (DQN) agent, developed from scratch, to master the classic CartPole-v1 control problem. Utilizing PyTorch for model development and Gymnasium (formerly OpenAI Gym) for the environment, this work serves as a practical guide and demonstration of applying deep reinforcement learning techniques to a well-established benchmark. The primary objective is to provide a clear, well-documented, and understandable implementation of the DQN algorithm and its core components.

The CartPole-v1 Environment

The CartPole-v1 environment is a standard benchmark in reinforcement learning. The task involves balancing a pole vertically on a cart that moves along a frictionless track. The agent can only apply a discrete left or right force to the cart. An episode ends if the pole angle exceeds a certain threshold, the cart moves off the track, or a maximum number of timesteps is reached. The simplicity of its state and action spaces, combined with its clear objective, makes CartPole an ideal environment for understanding and testing fundamental RL algorithms.

Deep Q-Network (DQN) Implementation

Our DQN agent learns a policy that maximizes cumulative rewards by approximating the optimal action-value function, Q 
∗
 (s,a), using a multi-layer perceptron implemented in PyTorch. The core components of the DQN algorithm meticulously implemented in this project include:

Q-Network: A neural network that takes the environment's state as input and outputs the estimated Q-value for each possible action.
Experience Replay: To break temporal correlations and improve sample efficiency, the agent stores its experiences (state, action, reward, next state, done flag) in a replay memory. During learning, mini-batches of these experiences are randomly sampled to update the Q-network.
Target Network: A separate neural network, which is a periodically updated copy of the main Q-network, is used to generate stable target values for the Bellman equation updates. This significantly enhances the stability of the learning process.
Epsilon-Greedy Exploration: To ensure a balance between exploring the environment to discover optimal actions and exploiting known good actions, an epsilon-greedy strategy is employed. The value of epsilon (exploration rate) anneals over time, shifting the agent from exploration to exploitation.
Training Process

The agent undergoes a training phase where it interacts with the CartPole-v1 environment over a series of episodes. In each step:

The agent observes the current state.
An action is selected using the epsilon-greedy policy based on the current Q-network's estimates.
The action is performed, leading to a new state, a reward, and a flag indicating episode termination.
This transition is stored in the replay memory.
Periodically, a mini-batch of transitions is sampled from the memory. These samples are used to compute the loss (typically Huber or MSE loss) between the predicted Q-values and the target Q-values derived from the Bellman equation using the target network.
The Q-network's weights are updated via backpropagation using an optimizer like AdamW.
The target network's weights are soft-updated with the Q-network's weights. The agent's learning progress is tracked by monitoring episode durations (or cumulative rewards), which are plotted to visualize performance improvement over time.
Key Features & Functionality

Modular Code: The implementation is structured with distinct classes for the DQN model (DQN) and the ReplayMemory, promoting clarity and reusability.
Clear Training Loop: The main script orchestrates the agent-environment interaction, learning updates, and periodic target network updates in an easy-to-follow manner.
Comprehensive Evaluation: Includes a dedicated function (evaluate_and_record_agent) to thoroughly assess the trained agent's performance over a specified number of episodes. This evaluation reports key statistics, including mean, standard deviation, median, minimum, and maximum for both episode rewards and durations.
Video Recording: Integrated capability to record videos of the agent's performance during the evaluation phase using Gymnasium's RecordVideo wrapper, providing a visual demonstration of the learned policy. Videos are organized into experiment-specific folders.
Performance Visualization: Live plotting of episode durations during training to monitor learning progress.
Project Aim

This project is designed for individuals seeking to gain a practical understanding of the Deep Q-Network algorithm and its application. It emphasizes a clear, step-by-step implementation of core deep reinforcement learning concepts, making it a valuable resource for students, researchers, and enthusiasts in the field of AI and machine learning.

![image](https://github.com/user-attachments/assets/29a9e39a-6b87-4400-98cc-a935cff8ddf6)


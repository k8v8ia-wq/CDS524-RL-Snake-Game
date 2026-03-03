# CDS524-RL-Snake-Game
# CDS524 Assignment 1 - Deep Q-Learning Snake Game 🐍🧠

[cite_start]This repository contains the source code and implementation details for a custom reinforcement learning environment, developed for **CDS524 Assignment 1: Reinforcement Learning Game Design**[cite: 1, 2]. 

[cite_start]The project applies the **Deep Q-Learning (DQN)** algorithm to train an autonomous agent to play a complex version of Snake, featuring multi-objective tasks like consuming food while avoiding walls, its own body, and randomly spawned poison traps[cite: 4, 9, 10].

## 🎥 Demo Video
Watch the agent training and navigating the environment here: 
[cite_start]**[Insert Your YouTube Video Link Here]** [cite: 31, 36]

---

## 🚀 Features
* [cite_start]**Custom Game Environment:** Built from scratch using `pygame` [cite: 17][cite_start], featuring a dynamic grid with food (positive reward) and poison traps (negative reward)[cite: 9].
* [cite_start]**Real-time Training Dashboard:** A custom UI panel that visualizes the agent's current state, action choices, total reward, and live training metrics (Epsilon, Max Q-value, Episode Score)[cite: 15, 16].
* **Live Matplotlib Metrics:** Dynamically plots the score per episode and the 50-episode moving average to evaluate convergence.

## 🧠 Markov Decision Process (MDP) Formulation
[cite_start]The game is modeled as an MDP to allow the agent to learn optimal decisions[cite: 8]:
* **State Space (15 Dimensions):** * Danger sensors (straight, right, left) for walls, body, and poison.
  * Current moving direction (4 boolean values).
  * Relative food location (4 boolean values).
  * Relative poison location (4 boolean values).
* [cite_start]**Action Space:** 3 discrete actions `[Straight, Turn Right, Turn Left]`[cite: 8].
* **Reward Function:** * `+10` for consuming food.
  * `-10` for game over (hitting walls, body, or poison).
  * [cite_start]`+1` / `-1` reward shaping based on the Manhattan distance to the food to prevent infinite loops[cite: 9].

## ⚙️ Technical Details & Hyperparameters
* [cite_start]**Algorithm:** Deep Q-Network (DQN) [cite: 10]
* **Neural Network:** PyTorch Linear Neural Network (Input: 15, Hidden: 256, Output: 3)
* **Optimization:** Adam Optimizer (Learning Rate: 0.001), Mean Squared Error (MSE) Loss
* [cite_start]**Exploration Strategy:** $\epsilon$-greedy (Starts at 1.0, decays by 0.995 to a minimum of 0.01) [cite: 13]
* [cite_start]**Discount Factor ($\gamma$):** 0.9 [cite: 13]
* **Experience Replay Memory:** `collections.deque` (Max length: 100,000, Batch size: 1000)

## 🛠️ Prerequisites
To run this project, you will need Python 3 and the following libraries installed:
```bash
pip install pygame torch torchvision torchaudio matplotlib numpy ipython

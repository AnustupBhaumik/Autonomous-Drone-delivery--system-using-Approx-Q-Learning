# SkyRoute: Autonomous Drone Delivery System

SkyRoute is an autonomous drone delivery system trained using Approximate Q-learning with linear function approximation[cite: 1]. The system models drone navigation as a finite Markov Decision Process (MDP) within a Gym-compatible simulation to balance path efficiency, obstacle avoidance, and successful task completion[cite: 1].

## Authors
* Anustup Bhaumik[cite: 1]
* Debanjan Kola[cite: 1]
* Debrup Chatterjee[cite: 1]
* Institution: Ramakrishna Mission Vivekananda Educational and Research Institute[cite: 1]

---

## Project Overview
* The environment is a discrete, grid-based navigation space featuring boundaries, obstacles, and final goal conditions[cite: 1].
* The state utilizes a feature representation of $f(s,a)\in\mathbb{R}^{4}$ to encode task-relevant properties[cite: 1].
* The action space consists of finite, discrete directional movement primitives[cite: 1].

## Reward Structure

| Reward Type | Value | Purpose |
| :--- | :--- | :--- |
| Success Reward | +100[cite: 1] | Terminal objective[cite: 1] |
| Step Penalty | -1[cite: 1] | Path efficiency[cite: 1] |
| Failure Penalty | -100 to -300[cite: 1] | Safety enforcement[cite: 1] |

---

## Methodology
* The system implements an off-policy temporal-difference control algorithm using an $\epsilon$-greedy policy[cite: 1].
* The action-value function is approximated linearly as $\tilde{Q}(s,a;w)=w^{T}f(s,a)$[cite: 1].
* Weights are updated via stochastic gradient descent based on the temporal-difference error[cite: 1].
* Training occurred over approximately 500 episodes using a decaying $\epsilon$-greedy schedule and a discount factor of $\gamma=0.99$[cite: 1].
* The four hand-engineered features encode goal progress, obstacle/boundary proximity, movement cost, and terminal success[cite: 1].

---

## Performance and Results
* The agent demonstrates reliable goal-reaching behavior under stabilized environmental conditions[cite: 1].
* The learned policy is highly risk-averse, exhibiting a strong aversion to collisions and boundary violations[cite: 1].
* The system is sensitive to high wind intensities, which can trap the drone and cause battery depletion without forward progress[cite: 1].
* The linear model lacks explicit temporal prediction, occasionally leading to collisions with dynamic obstacles like birds[cite: 1].

---

## Future Work
* Implementation of Double Q-learning to reduce overestimation bias[cite: 1].
* Integration of experience replay to improve learning stability[cite: 1].
* Utilization of Deep Q-Networks (DQN) for automatic non-linear feature learning[cite: 1].

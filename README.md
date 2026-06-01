# SkyRoute: Autonomous Drone Delivery System

SkyRoute is an autonomous drone delivery system trained using Approximate Q-learning with linear function approximation. The system models drone navigation as a finite Markov Decision Process (MDP) within a Gym-compatible simulation to balance path efficiency, obstacle avoidance, and successful task completion.

## Authors
* Anustup Bhaumik
* Debanjan Kola
* Debrup Chatterjee
* Institution: Ramakrishna Mission Vivekananda Educational and Research Institute

---

## Project Overview
* The environment is a discrete, grid-based navigation space featuring boundaries, obstacles, and final goal conditions.
* The state utilizes a feature representation of $f(s,a)\in\mathbb{R}^{4}$ to encode task-relevant properties.
* The action space consists of finite, discrete directional movement primitives.

## Reward Structure

| Reward Type | Value | Purpose |
| :--- | :--- | :--- |
| Success Reward | +100 | Terminal objective |
| Step Penalty | -1 | Path efficiency |
| Failure Penalty | -100 to -300 | Safety enforcement |

---

## Methodology
* The system implements an off-policy temporal-difference control algorithm using an $\epsilon$-greedy policy.
* The action-value function is approximated linearly as $\tilde{Q}(s,a;w)=w^{T}f(s,a)$.
* Weights are updated via stochastic gradient descent based on the temporal-difference error.
* Training occurred over approximately 500 episodes using a decaying $\epsilon$-greedy schedule and a discount factor of $\gamma=0.99$.
* The four hand-engineered features encode goal progress, obstacle/boundary proximity, movement cost, and terminal success.

---

## Performance and Results
* The agent demonstrates reliable goal-reaching behavior under stabilized environmental conditions.
* The learned policy is highly risk-averse, exhibiting a strong aversion to collisions and boundary violations.
* The system is sensitive to high wind intensities, which can trap the drone and cause battery depletion without forward progress.
* The linear model lacks explicit temporal prediction, occasionally leading to collisions with dynamic obstacles like birds.

---

## Future Work
* Implementation of Double Q-learning to reduce overestimation bias.
* Integration of experience replay to improve learning stability.
* Utilization of Deep Q-Networks (DQN) for automatic non-linear feature learning.

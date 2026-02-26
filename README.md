cat > README.md <<'EOF'
# RL Gridworld: TD(0) Policy Evaluation, SARSA, and Q-Learning (Python)

This repository contains implementation for Reinforcement Learning on a **5×5 Gridworld** with obstacles, a negative-reward water cell, and a terminal goal state. I implemented:

- **TD(0) policy evaluation** for a fixed policy (estimate state-value function)
- **On-policy control (SARSA)**
- **Off-policy control (Q-learning)**
- Experiment harness for comparing hyperparameters and plotting convergence behavior (MSE, steps vs episodes, learned policy)

> Focus: writing clean RL training loops + environment transition logic + reproducible experiments in Python.

---

## Gridworld Environment

- Grid size: **5 × 5**
- Terminal goal: **G** (positive terminal reward)
- Water cell: **negative reward** (penalty)
- Obstacles: blocked states (agent cannot enter)
- Stochastic transitions: action may “slip” (intended move with high probability, lateral moves with small probability)

The environment is small enough to debug easily, but still shows the key RL behaviors: exploration vs exploitation, convergence, and sensitivity to learning rate / stopping criteria.

---

## What’s Included

### 1) TD(0) Policy Evaluation
Given a fixed policy π, estimate **Vπ(s)** using TD(0) updates until convergence (delta threshold).

### 2) SARSA (On-policy Control)
Learn **Q(s,a)** while following an ε-greedy policy derived from Q and update using the SARSA target.

### 3) Q-Learning (Off-policy Control)
Learn **Q(s,a)** using the greedy bootstrap target, while behavior remains ε-greedy for exploration.

### 4) Evaluation / Visualizations
- **MSE vs Episodes** (value function convergence)
- **Episodes vs Steps** (how quickly episodes complete as learning improves)
- **Learned policy visualization** (arrows + terminal goal)

---

## Repository Structure

.
├── RL_HW_4_Kartikay.ipynb        # Main notebook (implementation + experiments)
├── RL_HW_4_FILE.pdf              # Assignment PDF (reference)
├── README.md
└── MEDIA/
    ├── RL_HW4_1.png
    ├── RL_HW4_2.png
    ├── RL_HW4_3.png
    ├── RL_HW4_4.png
    ├── RL_HW4_5.png
    ├── RL_HW4_6.png
    └── RL_HW4_7.png

---

## How to Run

### Option A: Run the notebook (recommended)
Install dependencies and run the notebook:

```bash
pip install numpy matplotlib tqdm
jupyter notebook
```


### code output
### RL_HW4_1: TD(0) policy-evaluation summary (error vs true values + averaged value grid).
![c](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_1.png)

### RL_HW4_2: Episodes vs steps curve (how episode count grows with total environment steps).
![d](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_2.png)

### RL_HW4_3: MSE vs episodes (value estimates converging over training).
![e](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_3.png)

### RL_HW4_4: Learned greedy policy visualization (best action per state, goal marked as G).
![f](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_4.png)

### RL_HW4_5: Episodes vs steps for another run/configuration (comparison across settings).
![g](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_5.png)

### RL_HW4_6: MSE vs episodes for another run/configuration (second convergence curve).
![h](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_6.png)

### RL_HW4_7: Final learned policy for another run/configuration (second policy arrow-grid).
![i](https://github.com/Kartikay77/RL-gridworld-sarsa-qlearning/blob/main/MEDIA/RL_HW4_7.png)

cat >> README.md <<'EOF'

---

## Notes / Tips

- The notebook is the single source of truth for implementation + experiments.
- If images don’t render, make sure they exist under `MEDIA/` and the filenames match exactly.
- To reduce notebook runtime, lower the number of runs/episodes or relax the convergence threshold.

---

## License
For educational use.

EOF

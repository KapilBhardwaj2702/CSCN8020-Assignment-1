# CSCN8020 - Reinforcement Learning Assignment 1

**Name:** Kapil Bhardwaj
**Student ID:** 9064347

## Overview

This repository contains the Jupyter Notebook for **Assignment 1**, where we model a robotic pick-and-place task using **Markov Decision Processes (MDP)** and explore various **Reinforcement Learning (RL) methods** for value estimation and policy optimization.

The assignment is divided into four main problems:

1. **Pick-and-Place Robot MDP**
2. **2x2 Gridworld – Manual Value Iteration**
3. **5x5 Gridworld – Automated Value Iteration**
4. **Off-Policy Monte Carlo with Importance Sampling**

---

## Problem 1 – Pick-and-Place Robot MDP

**Goal:** Model a robotic arm performing pick-and-place tasks as an MDP.

**Components:**

* **States:** Arm positions, velocities, gripper status
* **Actions:** Motor commands to move the arm and open/close gripper
* **Rewards:**

  * +100 for successfully picking and placing
  * -10 for collisions or error states
  * -1 per time step to encourage efficiency
  * Small smoothness penalty to encourage smooth movements
* **Transition Probabilities:** Mostly deterministic; small error probability can be introduced in real systems

**Implementation:**

* `PickPlaceEnv` class simulates the robot environment
* `_fake_forward_kinematics` maps joint angles to end-effector position
* `step()` computes the next state and reward based on actions

---

## Problem 2 – 2x2 Gridworld – Manual Value Iteration

**Goal:** Perform **two iterations of Value Iteration** manually and in code for a small 2x2 grid.

**Details:**

* **States:** s1, s2, s3, s4
* **Actions:** up, down, left, right
* **Rewards:**

  * s1 = 5, s2 = 10, s3 = 1, s4 = 2
* **Transition:** Deterministic (stay if hitting wall)
* **Discount factor (γ):** 1

**Outcome:** Value function updated for two iterations, showing step-by-step calculations.

---

## Problem 3 – 5x5 Gridworld Value Iteration

**Goal:** Implement automated value iteration on a larger 5x5 grid.

**Environment Details:**

* **Goal State:** (4,4) → +10 reward
* **Bad States:** (2,2), (3,0), (0,4) → -5 reward
* **Other States:** -1 reward per step
* **Actions:** up, down, left, right (deterministic)

**Implementation:**

* Standard **Value Iteration**
* **In-place Value Iteration** to demonstrate faster propagation
* Outputs: Optimal value function (V*) and policy (π*)

---

## Problem 4 – Off-Policy Monte Carlo with Importance Sampling

**Goal:** Estimate the value function using **off-policy Monte Carlo** with a **behavior policy** and a **target policy**.

**Details:**

* Behavior policy: Uniform random
* Target policy: Greedy (prefer right, else down)
* Discount factor: γ = 0.9
* Importance sampling used to correct for policy mismatch

**Outcome:**

* Value function estimated using off-policy MC closely matches value iteration results
* Demonstrates learning without a full model of the environment

---

## Usage

1. Clone this repository:

```bash
git clone <repo-url>
cd CSCN8020_Assignment1
```

2. Open the Jupyter Notebook:

```bash
jupyter notebook Assignment1_PickPlace_RL.ipynb
```

3. Run each cell sequentially.

**Dependencies:**

* Python 3.x
* NumPy
* Jupyter Notebook

---

## Notes

* `_fake_forward_kinematics` is a placeholder; for real robots, replace it with proper forward kinematics.
* All value iteration and Monte Carlo implementations assume deterministic movement.
* The notebook is well-commented to explain logic, formulas, and algorithms.

---

## Key Learnings

* Modeling robotic tasks as MDPs
* Manual and automated value iteration
* In-place vs standard value iteration
* Off-policy Monte Carlo with importance sampling
* Reward shaping and policy evaluation

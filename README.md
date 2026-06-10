# Optimistic vs. On-Policy Learning in the Iterated Prisoner's Dilemma

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Conference](https://img.shields.io/badge/Published-ICERAI-blue)](https://github.com/Soudk21/rl-iterated-prisoners-dilemma)
[![Topic](https://img.shields.io/badge/Topic-Reinforcement%20Learning-green)](https://github.com/Soudk21/rl-iterated-prisoners-dilemma)

## 📄 Abstract

This repository contains the implementation of our **ICERAI** paper on reinforcement learning in game theory. We investigate how two classical tabular RL algorithms — **Q-Learning** (optimistic, off-policy) and **SARSA** (realistic, on-policy) — learn to behave in the **Iterated Prisoner's Dilemma (IPD)** when facing a diverse set of opponents.

We first implement a fixed-strategy tournament involving **eight benchmark policies** (All-C, All-D, Tit-for-Tat, Tit-for-Two-Tats, Grim Trigger, Tester, Majority, and Random) to establish baseline performance. We then model the IPD as a **Markov Decision Process** with a memory-one state representation and train both agents over 3,000 episodes against each benchmark. Results show that Q-Learning's optimistic off-policy updates enable it to discover and maintain cooperative equilibria, while SARSA's on-policy updates make it risk-averse, often converging to mutual defection in harsh environments.

## 📂 Repository Structure

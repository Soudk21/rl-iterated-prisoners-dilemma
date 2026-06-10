# Optimistic vs. On-Policy Learning in the Iterated Prisoner's Dilemma

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Conference](https://img.shields.io/badge/Published-ICERAI-blue)](https://aurak.ac.ae/icerai-2026)
[![Topic](https://img.shields.io/badge/Topic-Reinforcement%20Learning-green)](https://github.com/Soudk21/rl-iterated-prisoners-dilemma)

## 📄 Abstract

This repository contains the implementation of our **ICERAI** paper on reinforcement learning in game theory. We investigate how two classical tabular RL algorithms — **Q-Learning** (optimistic, off-policy) and **SARSA** (realistic, on-policy) — learn to behave in the **Iterated Prisoner's Dilemma (IPD)** when facing a diverse set of opponents.

We first implement a fixed-strategy tournament involving **eight benchmark policies** (All-C, All-D, Tit-for-Tat, Tit-for-Two-Tats, Grim Trigger, Tester, Majority, and Random) to establish baseline performance. We then model the IPD as a **Markov Decision Process** with a memory-one state representation and train both agents over 3,000 episodes against each benchmark. Results show that Q-Learning's optimistic off-policy updates enable it to discover and maintain cooperative equilibria, while SARSA's on-policy updates make it risk-averse, often converging to mutual defection in harsh environments.

## 📂 Repository Structure

```bash
├── data/
│   └── README.md                             # Environment and payoff matrix description
├── notebooks/
│   └── rl_prisoners_dilemma.ipynb            # Full experiment notebook
├── src/
│   └── ai_in_game_theory.py                  # Core implementation
├── paper/
│   └── RL_Iterated_Prisoners_Dilemma_ICERAI.pdf  # Published conference paper
├── LICENSE
├── README.md
└── requirements.txt
```
---

This is the official code for the ICERAI paper:
**Optimistic vs. On-Policy Learning in the Iterated Prisoner's Dilemma: A Comparison of Q-Learning and SARSA**
Authors: Mohamed Malek Kaouach, Peter Yacoub, Soud Asaad Soud Alhazba, Dr. Huseyin Kusetogullari (Ajman University, UAE)
[Download Paper (PDF)](./paper/RL_Iterated_Prisoners_Dilemma_ICERAI.pdf)

---

## ⚙️ Methodology

- **Environment:** Iterated Prisoner's Dilemma modeled as an MDP with memory-one state representation
- **State Space:** 5 states — Start, (C,C), (C,D), (D,C), (D,D)
- **Action Space:** {Cooperate, Defect}
- **Payoff Matrix:** T=5, R=3, P=1, S=0 (standard IPD constraints: T > R > P > S)
- **Algorithms:** Q-Learning (off-policy) vs. SARSA (on-policy)
- **Hyperparameters:** α=0.1, γ=0.95, ε decayed from 0.1 to 0.01 over 3,000 episodes
- **Evaluation:** Average reward, cooperation rate, convergence stability

## 📊 Results

### Fixed Strategy Tournament Rankings

| Rank | Strategy | Score | Insight |
|---|---|---|---|
| 1 | Grim Trigger | 2.49 | Never exploited twice |
| 2 | Tit-for-Tat | 2.40 | Robust reciprocator |
| 3 | Tit-for-Two-Tats | 2.40 | Forgiving variant |
| 4 | Majority | 2.38 | Stable cooperator |
| 5 | Defector | 2.27 | Safe baseline |
| 6 | Random | 2.08 | No coherent strategy |
| 7 | Cooperator | 2.06 | Easily exploited |
| 8 | Tester | 1.81 | Probing backfires |

### Q-Learning vs. SARSA (Final 100 Episodes)

| Opponent | Q-L Coop% | Q-L Reward | SARSA Coop% | SARSA Reward |
|---|---|---|---|---|
| Cooperator | 0.5% | 4.99 | 10.0% | 4.80 |
| Defector | 0.5% | 1.00 | 9.8% | 0.90 |
| Tit-for-Tat | 99.4% | 2.99 | 89.9% | 2.89 |
| Grim Trigger | 80.0% | 2.61 | 18.4% | 1.14 |
| Self-Play | 96.5% | 2.94 | 11.6% | 1.35 |

> Q-Learning established trust and cooperation in self-play (96.5% cooperation rate).
> SARSA fell into mutual defection in self-play (11.6% cooperation rate).

## 🗃️ Environment

No external dataset is required. The IPD environment is fully implemented in `src/ai_in_game_theory.py`. See `data/README.md` for a description of the payoff structure and MDP formulation.

## 🚀 Installation

```bash
git clone https://github.com/Soudk21/rl-iterated-prisoners-dilemma.git
cd rl-iterated-prisoners-dilemma
pip install -r requirements.txt
```

## 📓 Usage

Run the notebook for the full experiment:

```bash
jupyter notebook notebooks/rl_prisoners_dilemma.ipynb
```

Or run the source file directly:

```bash
python src/ai_in_game_theory.py
```

## 🤝 Acknowledgments

- Affiliated with: College of Engineering and Information Technology, Ajman University, UAE
- Published at: ICERAI Conference

## 📜 Citation

If you use this code or findings in your research, please cite:

```bibtex
@inproceedings{kaouach2025ipd,
title={Optimistic vs. On-Policy Learning in the Iterated Prisoner's Dilemma: A Comparison of Q-Learning and SARSA},
author={Kaouach, Mohamed Malek and Yacoub, Peter and Alhazba, Soud Asaad Soud and Kusetogullari, Huseyin},
booktitle={Proceedings of ICERAI},
year={2025}
}
```

## License

MIT License. See [LICENSE](./LICENSE) for details.

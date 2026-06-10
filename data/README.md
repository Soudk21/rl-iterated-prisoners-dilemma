# Environment Description

This project does not use an external dataset. The Iterated Prisoner's Dilemma
environment is fully self-contained and implemented in `src/ai_in_game_theory.py`.

---

## Payoff Matrix

| | Player 2 Cooperates | Player 2 Defects |
|---|---|---|
| **Player 1 Cooperates** | R=3, R=3 (Reward) | S=0, T=5 (Sucker) |
| **Player 1 Defects** | T=5, S=0 (Temptation) | P=1, P=1 (Punishment) |

The payoff values satisfy the Prisoner's Dilemma constraints:
- **T > R > P > S** → 5 > 3 > 1 > 0
- **2R > T + S** → 6 > 5 (ensures mutual cooperation beats alternating)

---

## MDP Formulation

| Component | Definition |
|---|---|
| **State Space** | 5 states: Start, (C,C), (C,D), (D,C), (D,D) |
| **Action Space** | {Cooperate (C), Defect (D)} |
| **Reward** | Derived from payoff matrix above |
| **Discount Factor** | γ = 0.95 |

---

## Benchmark Strategies

| Strategy | Rule |
|---|---|
| Cooperator (All-C) | Always cooperates |
| Defector (All-D) | Always defects |
| Tit-for-Tat | Copies opponent's last move |
| Tit-for-Two-Tats | Defects only after two consecutive defections |
| Grim Trigger | Cooperates until betrayed, then defects forever |
| Tester | Probes with defection on first move |
| Majority | Plays opponent's most frequent historical action |
| Random | Selects C or D with equal probability |

---

## Training Setup

| Parameter | Value |
|---|---|
| Episodes | 3,000 per opponent pairing |
| Rounds per episode | 100 |
| Learning rate (α) | 0.1 |
| Discount factor (γ) | 0.95 |
| Epsilon start (ε) | 0.1 |
| Epsilon minimum | 0.01 |

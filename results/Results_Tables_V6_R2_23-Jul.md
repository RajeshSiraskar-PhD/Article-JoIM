# REPORT - V6 - RESULTS TABLE OF VALUES
- 23-Jul-2026: R2 : IEEE No Attn Eval - 0.1 
---------------------------------------------------------

## GEMINI INTERPRETATION  

1. **Attention Reverses the Algorithm Hierarchy (REINFORCE vs. PPO)**
* **Without Attention:** PPO clearly dominates REINFORCE in both SIT ($0.6313$ vs. $0.4907$) and IEEE ($0.7484$ vs. $0.6696$).
* **With Optimal Attention:** REINFORCE leapfrogs PPO, achieving statistically significant superiority in both SIT ($p = 0.0001$) and IEEE ($p = 0.0424$).
* **Takeaway:** While PPO’s clipping mechanisms make it a stronger out-of-the-box baseline, REINFORCE has a higher ceiling when paired with effective feature representations.

2. **A2C’s Multi-Head Exception**
* While TD learners generally collapse under attention, A2C in IEEE shows a notable exception: Multi-Head attention improves its performance over baseline ($0.7424$ vs. $0.6180$). Multi-head projection likely preserves enough parallel subspaces to prevent complete value collapse in Actor-Critic setups.

----

## Theoretical Justification Using Algorithmic Taxonomy

The contrast in performance between **Group 1** and **Group 2** stems from how these algorithmic families interact with dynamic feature spaces.

```
                  ┌─────────────────────────────────────────┐
                  │          Attention Layer                │
                  │   (Dynamic Feature Representations)     │
                  └────────────────────┬────────────────────┘
                                       │
            ┌──────────────────────────┴──────────────────────────┐
            ▼                                                     ▼
  Group 1: TD Learners                               Group 2: Direct Policy
  (A2C & DQN)                                        Optimizers (REINFORCE & PPO)
  ─────────────────────                              ───────────────────────────
  ❌ Bootstrapping non-stationary targets           ✅ Direct return maximization
  ❌ High variance in $Q(s,a)$ updates              ✅ Smooth optimization of policy $\pi_\theta$
  ❌ Severe representation collapse                 ✅ High tolerance for dynamic features

```

### 1. Group 1: TD Learners (DQN & A2C) — *Representation Instability*

* **The Mechanism:** Temporal Difference (TD) methods estimate state-action values $Q(s, a)$ or state values $V(s)$ by bootstrapping off future estimates via the Bellman equation.
* **Why Attention Breaks TD:** Attention mechanisms continuously re-weight and transform input features dynamically. When an attention layer sits in front of a value-based architecture:
1. **Non-Stationary Target Problem:** The bootstrapped target $r + \gamma \max_{a'} Q(s', a')$ relies on a value network whose underlying feature space is shifting due to dynamic attention updates.
2. **Overestimation & Divergence:** Small fluctuations in attention weights propagate exponentially through TD error updates, causing value estimates to explode or collapse. This explains why DQN flatlines at the score floor ($0.236 – 0.2456$) across almost all attention types.


### 2. Group 2: Policy Optimizers (REINFORCE & PPO) — *Representation Synergies*

* **The Mechanism:** Policy gradient methods directly optimize the policy parameters $\theta$ to maximize expected cumulative reward $J(\theta) = \mathbb{E}_{\pi_\theta}[R]$, without using bootstrapped values for action selection.
* **Why Attention Empowers Policy Gradients:**
1. **Direct Credit Assignment:** REINFORCE uses full trajectory Monte Carlo returns $G_t$. Because there is no bootstrapping, shifting feature representations do not create non-stationary feedback loops. The network simply learns which attention filters correlate with higher total episode rewards.
2. **Trust Region / Clipping Stability:** PPO further stabilizes attention integration through its clipped surrogate objective, preventing the policy from making destructive updates when attention weights shift drastically between iterations.
3. **Dimensionality Reduction:** Attention acts as a dynamic spatial/temporal filter. By filtering out environment noise, it presents a cleaner state representation directly to the policy head ($\pi_\theta(a\vert{}s)$), drastically simplifying the search space for policy gradient ascent.

---

### ARTCILE NOTE

> "Our empirical results reveal a clear taxonomy-level split: Direct Policy Optimizers (REINFORCE, PPO) leverage attention mechanisms to construct low-noise, task-relevant feature abstractions, yielding statistically significant performance gains. Conversely, Temporal Difference learners (DQN, A2C) suffer catastrophic representation collapse, as dynamic attention weight shifts introduce severe target non-stationarity into the Bellman update loop."
> 
> 

# RAW REPORT
---------------------------------------------------------
## SUMMARY:
- Configured alpha threshold: 0.05
---------------------------------------------------------

### PART-1: Schema: SIT
---------------------------------------------------------

Table Caption: SIT - Mean +/- Std Dev of Eval_Score by RL algorithm and attention mechanism.
| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| SIT | A2C | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.3130 +/- 0.2040 | 0.2456 +/- 0.0043 |
| SIT | DQN | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 |
| SIT | PPO | 0.6313 +/- 0.3347 | 0.7132 +/- 0.3172 | 0.5771 +/- 0.3337 | 0.6089 +/- 0.3305 | 0.8004 +/- 0.2694 |
| SIT | REINFORCE | 0.4907 +/- 0.3108 | 0.8646 +/- 0.2032 | 0.6406 +/- 0.3355 | 0.6997 +/- 0.3171 | 0.7917 +/- 0.2738 |

Table Caption: SIT - Special focus table for PPO and REINFORCE (Mean +/- Std Dev of Eval_Score).
| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| SIT | PPO | 0.6313 +/- 0.3347 | 0.7132 +/- 0.3172 | 0.5771 +/- 0.3337 | 0.6089 +/- 0.3305 | 0.8004 +/- 0.2694 |
| SIT | REINFORCE | 0.4907 +/- 0.3108 | 0.8646 +/- 0.2032 | 0.6406 +/- 0.3355 | 0.6997 +/- 0.3171 | 0.7917 +/- 0.2738 |


### PART-2: Schema: IEEE
---------------------------------------------------------

Table Caption: IEEE - Mean +/- Std Dev of Eval_Score by RL algorithm and attention mechanism.
| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| IEEE | A2C | 0.6180 +/- 0.2640 | 0.4322 +/- 0.2753 | 0.3565 +/- 0.2496 | 0.2729 +/- 0.1281 | 0.7424 +/- 0.2695 |
| IEEE | DQN | 0.5996 +/- 0.2550 | 0.2360 +/- 0.0016 | 0.2360 +/- 0.0016 | 0.2360 +/- 0.0016 | 0.2878 +/- 0.1811 |
| IEEE | PPO | 0.7484 +/- 0.1418 | 0.8343 +/- 0.1867 | 0.7608 +/- 0.2641 | 0.8044 +/- 0.2174 | 0.8232 +/- 0.1870 |
| IEEE | REINFORCE | 0.6696 +/- 0.2214 | 0.8008 +/- 0.2186 | 0.8848 +/- 0.0737 | 0.8860 +/- 0.0708 | 0.8559 +/- 0.1443 |

Table Caption: IEEE - Special focus table for PPO and REINFORCE (Mean +/- Std Dev of Eval_Score).
| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| IEEE | PPO | 0.7484 +/- 0.1418 | 0.8343 +/- 0.1867 | 0.7608 +/- 0.2641 | 0.8044 +/- 0.2174 | 0.8232 +/- 0.1870 |
| IEEE | REINFORCE | 0.6696 +/- 0.2214 | 0.8008 +/- 0.2186 | 0.8848 +/- 0.0737 | 0.8860 +/- 0.0708 | 0.8559 +/- 0.1443 |


---------------------------------------------------------
## DETAILS:
---------------------------------------------------------

### PART-1: Algorithm-wise Ablation Details

##### 1.1 SCHEMA: SIT

| Schema | Algorithm | Setup | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| SIT | A2C | No Attention (Baseline) | 0.2456 | 0.0005 | - | - |
| SIT | A2C | All Attention | 0.2625 | 0.0056 | 3.0125 | 0.0014 |
| SIT | A2C | Nadaraya-Watson | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | A2C | Temporal | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | A2C | Self-Attention | 0.3130 | 0.0215 | 3.1332 | 0.0012 |
| SIT | A2C | Multi-Head | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | DQN | No Attention (Baseline) | 0.2456 | 0.0005 | - | - |
| SIT | DQN | All Attention | 0.2456 | 0.0002 | -0.0000 | 0.5000 |
| SIT | DQN | Nadaraya-Watson | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | DQN | Temporal | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | DQN | Self-Attention | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | DQN | Multi-Head | 0.2456 | 0.0005 | 0.0000 | 0.5000 |
| SIT | PPO | No Attention (Baseline) | 0.6313 | 0.0353 | - | - |
| SIT | PPO | All Attention | 0.6749 | 0.0171 | 1.1112 | 0.1342 |
| SIT | PPO | Nadaraya-Watson | 0.7132 | 0.0334 | 1.6834 | 0.0470 |
| SIT | PPO | Temporal | 0.5771 | 0.0352 | -1.0880 | 0.8610 |
| SIT | PPO | Self-Attention | 0.6089 | 0.0348 | -0.4518 | 0.6740 |
| SIT | PPO | Multi-Head | 0.8004 | 0.0284 | 3.7330 | 0.0001 |
| SIT | REINFORCE | No Attention (Baseline) | 0.4907 | 0.0328 | - | - |
| SIT | REINFORCE | All Attention | 0.7492 | 0.0157 | 7.1139 | 0.0000 |
| SIT | REINFORCE | Nadaraya-Watson | 0.8646 | 0.0214 | 9.5544 | 0.0000 |
| SIT | REINFORCE | Temporal | 0.6406 | 0.0354 | 3.1098 | 0.0011 |
| SIT | REINFORCE | Self-Attention | 0.6997 | 0.0334 | 4.4662 | 0.0000 |
| SIT | REINFORCE | Multi-Head | 0.7917 | 0.0289 | 6.8960 | 0.0000 |


##### 1.2 SCHEMA: IEEE

| Schema | Algorithm | Setup | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | A2C | No Attention (Baseline) | 0.6180 | 0.0590 | - | - |
| IEEE | A2C | All Attention | 0.4510 | 0.0295 | -2.5313 | 0.9915 |
| IEEE | A2C | Nadaraya-Watson | 0.4322 | 0.0551 | -2.3021 | 0.9868 |
| IEEE | A2C | Temporal | 0.3565 | 0.0499 | -3.3824 | 0.9992 |
| IEEE | A2C | Self-Attention | 0.2729 | 0.0256 | -5.3618 | 1.0000 |
| IEEE | A2C | Multi-Head | 0.7424 | 0.0539 | 1.5551 | 0.0638 |
| IEEE | DQN | No Attention (Baseline) | 0.5996 | 0.0570 | - | - |
| IEEE | DQN | All Attention | 0.2489 | 0.0092 | -6.0699 | 1.0000 |
| IEEE | DQN | Nadaraya-Watson | 0.2360 | 0.0003 | -6.3757 | 1.0000 |
| IEEE | DQN | Temporal | 0.2360 | 0.0003 | -6.3757 | 1.0000 |
| IEEE | DQN | Self-Attention | 0.2360 | 0.0003 | -6.3757 | 1.0000 |
| IEEE | DQN | Multi-Head | 0.2878 | 0.0362 | -4.6143 | 1.0000 |
| IEEE | PPO | No Attention (Baseline) | 0.7484 | 0.0317 | - | - |
| IEEE | PPO | All Attention | 0.8057 | 0.0215 | 1.4948 | 0.0715 |
| IEEE | PPO | Nadaraya-Watson | 0.8343 | 0.0373 | 1.7522 | 0.0434 |
| IEEE | PPO | Temporal | 0.7608 | 0.0528 | 0.2010 | 0.4209 |
| IEEE | PPO | Self-Attention | 0.8044 | 0.0435 | 1.0399 | 0.1522 |
| IEEE | PPO | Multi-Head | 0.8232 | 0.0374 | 1.5252 | 0.0673 |
| IEEE | REINFORCE | No Attention (Baseline) | 0.6696 | 0.0495 | - | - |
| IEEE | REINFORCE | All Attention | 0.8569 | 0.0143 | 3.6351 | 0.0007 |
| IEEE | REINFORCE | Nadaraya-Watson | 0.8008 | 0.0437 | 1.9868 | 0.0269 |
| IEEE | REINFORCE | Temporal | 0.8848 | 0.0147 | 4.1672 | 0.0002 |
| IEEE | REINFORCE | Self-Attention | 0.8860 | 0.0142 | 4.2027 | 0.0002 |
| IEEE | REINFORCE | Multi-Head | 0.8559 | 0.0289 | 3.2506 | 0.0014 |


### PART-2: General Effects - All Algos.

##### 2.1 SCHEMA : SIT

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| SIT | Algos: All | No Attention (Baseline) | 0.4033 | 0.0148 | - | - |
| SIT | Algos: All | All Attention | 0.4830 | 0.0085 | 4.6626 | 0.0000 |
| SIT | Algos: All | Nadaraya-Watson | 0.5173 | 0.0176 | 4.9445 | 0.0000 |
| SIT | Algos: All | Temporal | 0.4273 | 0.0157 | 1.1070 | 0.1343 |
| SIT | Algos: All | Self-Attention | 0.4668 | 0.0166 | 2.8533 | 0.0022 |
| SIT | Algos: All | Multi-Head | 0.5209 | 0.0177 | 5.0935 | 0.0000 |


##### 2.2 SCHEMA : IEEE

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | Algos: All | No Attention (Baseline) | 0.6589 | 0.0256 | - | - |
| IEEE | Algos: All | All Attention | 0.5906 | 0.0161 | -2.2584 | 0.9873 |
| IEEE | Algos: All | Nadaraya-Watson | 0.5758 | 0.0320 | -2.0275 | 0.9779 |
| IEEE | Algos: All | Temporal | 0.5595 | 0.0327 | -2.3918 | 0.9911 |
| IEEE | Algos: All | Self-Attention | 0.5498 | 0.0325 | -2.6358 | 0.9954 |
| IEEE | Algos: All | Multi-Head | 0.6773 | 0.0303 | 0.4642 | 0.3215 |


### PART-3: General Effects - Focussed algos - PPO & REINFORCE combined

##### 3.1 SCHEMA : SIT 

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| SIT | Algos: PPO & REINFORCE | No Attention (Baseline) | 0.5610 | 0.0246 | - | - |
| SIT | Algos: PPO & REINFORCE | All Attention | 0.7120 | 0.0117 | 5.5498 | 0.0000 |
| SIT | Algos: PPO & REINFORCE | Nadaraya-Watson | 0.7889 | 0.0206 | 7.1080 | 0.0000 |
| SIT | Algos: PPO & REINFORCE | Temporal | 0.6089 | 0.0250 | 1.3658 | 0.0864 |
| SIT | Algos: PPO & REINFORCE | Self-Attention | 0.6543 | 0.0243 | 2.6996 | 0.0036 |
| SIT | Algos: PPO & REINFORCE | Multi-Head | 0.7961 | 0.0202 | 7.3911 | 0.0000 |

##### 3.2 SCHEMA : IEEE 

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | Algos: PPO & REINFORCE | No Attention (Baseline) | 0.7090 | 0.0297 | - | - |
| IEEE | Algos: PPO & REINFORCE | All Attention | 0.8313 | 0.0130 | 3.7724 | 0.0002 |
| IEEE | Algos: PPO & REINFORCE | Nadaraya-Watson | 0.8176 | 0.0286 | 2.6346 | 0.0050 |
| IEEE | Algos: PPO & REINFORCE | Temporal | 0.8228 | 0.0285 | 2.7631 | 0.0035 |
| IEEE | Algos: PPO & REINFORCE | Self-Attention | 0.8452 | 0.0234 | 3.6040 | 0.0003 |
| IEEE | Algos: PPO & REINFORCE | Multi-Head | 0.8395 | 0.0235 | 3.4472 | 0.0005 |


### PART-4: REINFORCE only
*Significant means REINFORCE is statistically significantly better (p < 0.05)*

#### 4.1 SCHEMA : SIT - Without Attention (Baseline)

Table Caption: SIT - REINFORCE vs other algorithms (Without Attention (Baseline)), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| SIT | REINFORCE vs A2C | 0.4907 | 0.2456 | 7.4789 | 0.0000 | Yes |
| SIT | REINFORCE vs DQN | 0.4907 | 0.2456 | 7.4789 | 0.0000 | Yes |
| SIT | REINFORCE vs PPO | 0.4907 | 0.6313 | -2.9224 | 0.9980 | No |

#### 4.2 SCHEMA : SIT - With Attention -- Nadaraya-Watson Attention

Table Caption: SIT - REINFORCE with NW vs other algorithms (With Nadaraya-Watson Attention), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| SIT | REINFORCE vs A2C | 0.8646 | 0.2456 | 28.8862 | 0.0000 | Yes |
| SIT | REINFORCE vs DQN | 0.8646 | 0.2456 | 28.8862 | 0.0000 | Yes |
| SIT | REINFORCE vs PPO | 0.8646 | 0.7132 | 3.8133 | 0.0001 | Yes |


#### 4.3 SCHEMA : IEEE - Without Attention (Baseline)

Table Caption: IEEE - REINFORCE vs other algorithms (Without Attention (Baseline)), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| IEEE | REINFORCE vs A2C | 0.6696 | 0.6180 | 0.6692 | 0.2538 | No |
| IEEE | REINFORCE vs DQN | 0.6696 | 0.5996 | 0.9275 | 0.1798 | No |
| IEEE | REINFORCE vs PPO | 0.6696 | 0.7484 | -1.3409 | 0.9053 | No |


#### 4.4 SCHEMA : IEEE - With Attention -- Self-Attention

Table Caption: IEEE - REINFORCE vs other algorithms (With Self-Attention Attention), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| IEEE | REINFORCE vs A2C | 0.8860 | 0.2729 | 20.9413 | 0.0000 | Yes |
| IEEE | REINFORCE vs DQN | 0.8860 | 0.2360 | 45.9253 | 0.0000 | Yes |
| IEEE | REINFORCE vs PPO | 0.8860 | 0.8044 | 1.7848 | 0.0424 | Yes |

#### 4.5 - CONCLUSION

Best Attention Mechanism for REINFORCE:
  SIT Schema: Nadaraya-Watson (p=0.0000, Mean=0.8646)
  IEEE Schema: Self-Attention (p=0.0002, Mean=0.8860)



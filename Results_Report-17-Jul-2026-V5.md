# FINAL SUMMARY:
------------------------------------
Analysis Report -- Date: 17-Jul-2026
------------------------------------
Configured alpha threshold: 0.05

Schema: SIT
------------------------------------------------------------------------------------------
Table 1: SIT - Mean +/- Std Dev of Eval_Score by RL algorithm and attention mechanism.

| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| SIT | A2C | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.3130 +/- 0.2040 | 0.2456 +/- 0.0043 |
| SIT | DQN | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 | 0.2456 +/- 0.0043 |
| SIT | PPO | 0.6313 +/- 0.3347 | 0.7132 +/- 0.3172 | 0.5771 +/- 0.3337 | 0.6089 +/- 0.3305 | 0.8004 +/- 0.2694 |
| SIT | REINFORCE | 0.4907 +/- 0.3108 | 0.8646 +/- 0.2032 | 0.6406 +/- 0.3355 | 0.6997 +/- 0.3171 | 0.7917 +/- 0.2738 |


FIGURE : Ablation_Study_SIT_All_Algos.jpg
FIGURE : Ablation_Study_Algo_SIT.jpg

Table 2: SIT - Special focus table for PPO and REINFORCE (Mean +/- Std Dev of Eval_Score).

| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| SIT | PPO | 0.6313 +/- 0.3347 | 0.7132 +/- 0.3172 | 0.5771 +/- 0.3337 | 0.6089 +/- 0.3305 | 0.8004 +/- 0.2694 |
| SIT | REINFORCE | 0.4907 +/- 0.3108 | 0.8646 +/- 0.2032 | 0.6406 +/- 0.3355 | 0.6997 +/- 0.3171 | 0.7917 +/- 0.2738 |

Best overall WITHOUT attention: PPO (mean=0.6313)
Best overall WITH attention: REINFORCE (mean=0.7492)

Statistical tests and inferences (one-tailed Welch t-test, REINFORCE > PPO):
- Baseline: t=-2.9224, p=0.9980, n(REINFORCE)=90, n(PPO)=90 -> claim 'REINFORCE performs better than PPO' is not supported at alpha=0.05.
- With attention: t=3.1941, p=0.0007, n(REINFORCE)=360, n(PPO)=360 -> claim 'REINFORCE performs better than PPO' is supported at alpha=0.05.


-- SIT: PPO & REINFORCE Spotlight details  ---

🔍 Analyzing PPO:
  • Baseline Mean Score: 0.6313
  ❌ Attention (in general) did NOT significantly outperform baseline on average.
  ✅ AT LEAST ONE specific mechanism worked! Significant winners:
      - Nadaraya-Watson (Mean: 0.7132, p=0.0470)
      - Multi-Head (Mean: 0.8004, p=0.0001)

🔍 Analyzing REINFORCE:
  • Baseline Mean Score: 0.4907
  ✅ Attention in general significantly OUTPERFORMED baseline overall. (p=0.0000)
  ✅ AT LEAST ONE specific mechanism worked! Significant winners:
      - Nadaraya-Watson (Mean: 0.8646, p=0.0000)
      - Temporal (Mean: 0.6406, p=0.0011)
      - Self-Attention (Mean: 0.6997, p=0.0000)
      - Multi-Head (Mean: 0.7917, p=0.0000)

Figure: Ablation_Study_SIT_PPO_REINFORCE.jpg

Schema: IEEE
------------------------------------------------------------------------------------------
Table 3: IEEE - Mean +/- Std Dev of Eval_Score by RL algorithm and attention mechanism.

| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| IEEE | A2C | 0.6880 +/- 0.3098 | 0.4322 +/- 0.2753 | 0.3565 +/- 0.2496 | 0.2729 +/- 0.1281 | 0.7424 +/- 0.2695 |
| IEEE | DQN | 0.6696 +/- 0.3002 | 0.2360 +/- 0.0016 | 0.2360 +/- 0.0016 | 0.2360 +/- 0.0016 | 0.2878 +/- 0.1811 |
| IEEE | PPO | 0.8434 +/- 0.1604 | 0.8343 +/- 0.1867 | 0.7608 +/- 0.2641 | 0.8044 +/- 0.2174 | 0.8232 +/- 0.1870 |
| IEEE | REINFORCE | 0.7496 +/- 0.2606 | 0.8008 +/- 0.2186 | 0.8848 +/- 0.0737 | 0.8860 +/- 0.0708 | 0.8559 +/- 0.1443 |


FIGURE : Ablation_Study_IEEE_All_Algos.jpg
FIGURE : Ablation_Study_Algo_IEEE.jpg

Table 4: IEEE - Special focus table for PPO and REINFORCE (Mean +/- Std Dev of Eval_Score).

| Schema | RL Algo | Baseline | NW | TP | SA | MH |
|---|---|---|---|---|---|---|
| IEEE | PPO | 0.8434 +/- 0.1604 | 0.8343 +/- 0.1867 | 0.7608 +/- 0.2641 | 0.8044 +/- 0.2174 | 0.8232 +/- 0.1870 |
| IEEE | REINFORCE | 0.7496 +/- 0.2606 | 0.8008 +/- 0.2186 | 0.8848 +/- 0.0737 | 0.8860 +/- 0.0708 | 0.8559 +/- 0.1443 |

Best overall WITHOUT attention: PPO (mean=0.8434)
Best overall WITH attention: REINFORCE (mean=0.8569)

Statistical tests and inferences (one-tailed Welch t-test, REINFORCE > PPO):
- Baseline: t=-1.3711, p=0.9100, n(REINFORCE)=20, n(PPO)=20 -> claim 'REINFORCE performs better than PPO' is not supported at alpha=0.05.
- With attention: t=1.9865, p=0.0243, n(REINFORCE)=100, n(PPO)=100 -> claim 'REINFORCE performs better than PPO' is supported at alpha=0.05.


--- IEEE -- PPO & REINFORCE Spotlight details  ---
🔍 Analyzing PPO:
  • Baseline Mean Score: 0.8434
  ❌ Attention (in general) did NOT significantly outperform baseline on average.
  ❌ No individual attention mechanism significantly outperformed the baseline.

🔍 Analyzing REINFORCE:
  • Baseline Mean Score: 0.7496
  ✅ Attention in general significantly OUTPERFORMED baseline overall. (p=0.0440)
  ✅ AT LEAST ONE specific mechanism worked! Significant winners:
      - Temporal (Mean: 0.8848, p=0.0175)
      - Self-Attention (Mean: 0.8860, p=0.0167)

Figure: Ablation_Study_IEEE_PPO_REINFORCE.jpg

------------------------------------
------------------------------------

# DETAILS:
------------------------------------

## General Effects Details

### SIT

SIT - Ablation Study Results Algos: All

Table Caption: SIT | Algos: All | Aggregated attention-effect summary (Category, Mean, SEM, t-statistic, p-value).

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| SIT | Algos: All | No Attention (Baseline) | 0.4033 | 0.0148 | - | - |
| SIT | Algos: All | All Attention | 0.4830 | 0.0085 | 4.6626 | 0.0000 |
| SIT | Algos: All | Nadaraya-Watson | 0.5173 | 0.0176 | 4.9445 | 0.0000 |
| SIT | Algos: All | Temporal | 0.4273 | 0.0157 | 1.1070 | 0.1343 |
| SIT | Algos: All | Self-Attention | 0.4668 | 0.0166 | 2.8533 | 0.0022 |
| SIT | Algos: All | Multi-Head | 0.5209 | 0.0177 | 5.0935 | 0.0000 |

--- Descriptive Summary ---
The baseline (No Attention) achieved an average Eval_Score of 0.4033.
✅ All Attention: Significantly OUTPERFORMED the baseline. (Mean Score: 0.4830, p-value: 0.0000)
✅ Nadaraya-Watson: Significantly OUTPERFORMED the baseline. (Mean Score: 0.5173, p-value: 0.0000)
❌ Temporal: Did NOT significantly outperform the baseline. (Mean Score: 0.4273, p-value: 0.1343)
✅ Self-Attention: Significantly OUTPERFORMED the baseline. (Mean Score: 0.4668, p-value: 0.0022)
✅ Multi-Head: Significantly OUTPERFORMED the baseline. (Mean Score: 0.5209, p-value: 0.0000)


SIT - ALGOS: PPO & REINFORCE

Table Caption: SIT | Algos: PPO & REINFORCE | Aggregated attention-effect summary (Category, Mean, SEM, t-statistic, p-value).

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| SIT | Algos: PPO & REINFORCE | No Attention (Baseline) | 0.5610 | 0.0246 | - | - |
| SIT | Algos: PPO & REINFORCE | All Attention | 0.7120 | 0.0117 | 5.5498 | 0.0000 |
| SIT | Algos: PPO & REINFORCE | Nadaraya-Watson | 0.7889 | 0.0206 | 7.1080 | 0.0000 |
| SIT | Algos: PPO & REINFORCE | Temporal | 0.6089 | 0.0250 | 1.3658 | 0.0864 |
| SIT | Algos: PPO & REINFORCE | Self-Attention | 0.6543 | 0.0243 | 2.6996 | 0.0036 |
| SIT | Algos: PPO & REINFORCE | Multi-Head | 0.7961 | 0.0202 | 7.3911 | 0.0000 |

--- Descriptive Summary ---
The baseline (No Attention) achieved an average Eval_Score of 0.5610.
✅ All Attention: Significantly OUTPERFORMED the baseline. (Mean Score: 0.7120, p-value: 0.0000)
✅ Nadaraya-Watson: Significantly OUTPERFORMED the baseline. (Mean Score: 0.7889, p-value: 0.0000)
❌ Temporal: Did NOT significantly outperform the baseline. (Mean Score: 0.6089, p-value: 0.0864)
✅ Self-Attention: Significantly OUTPERFORMED the baseline. (Mean Score: 0.6543, p-value: 0.0036)
✅ Multi-Head: Significantly OUTPERFORMED the baseline. (Mean Score: 0.7961, p-value: 0.0000)


### IEEE

IEEE - Ablation Study Results Algos: All

Table Caption: IEEE | Algos: All | Aggregated attention-effect summary (Category, Mean, SEM, t-statistic, p-value).

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | Algos: All | No Attention (Baseline) | 0.7377 | 0.0300 | - | - |
| IEEE | Algos: All | All Attention | 0.5906 | 0.0161 | -4.3197 | 1.0000 |
| IEEE | Algos: All | Nadaraya-Watson | 0.5758 | 0.0320 | -3.6897 | 0.9999 |
| IEEE | Algos: All | Temporal | 0.5595 | 0.0327 | -4.0124 | 1.0000 |
| IEEE | Algos: All | Self-Attention | 0.5498 | 0.0325 | -4.2457 | 1.0000 |
| IEEE | Algos: All | Multi-Head | 0.6773 | 0.0303 | -1.4149 | 0.9206 |

--- Descriptive Summary ---
The baseline (No Attention) achieved an average Eval_Score of 0.7377.
❌ All Attention: Did NOT significantly outperform the baseline. (Mean Score: 0.5906, p-value: 1.0000)
❌ Nadaraya-Watson: Did NOT significantly outperform the baseline. (Mean Score: 0.5758, p-value: 0.9999)
❌ Temporal: Did NOT significantly outperform the baseline. (Mean Score: 0.5595, p-value: 1.0000)
❌ Self-Attention: Did NOT significantly outperform the baseline. (Mean Score: 0.5498, p-value: 1.0000)
❌ Multi-Head: Did NOT significantly outperform the baseline. (Mean Score: 0.6773, p-value: 0.9206)
--------------------------------------------------

Visualization saved successfully as Ablation_Study_IEEE_All_Algos.jpg

IEEE - ALGOS: PPO & REINFORCE

Table Caption: IEEE | Algos: PPO & REINFORCE | Aggregated attention-effect summary (Category, Mean, SEM, t-statistic, p-value).

| Schema | Table Scope | Category | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | Algos: PPO & REINFORCE | No Attention (Baseline) | 0.7965 | 0.0346 | - | - |
| IEEE | Algos: PPO & REINFORCE | All Attention | 0.8313 | 0.0130 | 0.9406 | 0.1757 |
| IEEE | Algos: PPO & REINFORCE | Nadaraya-Watson | 0.8176 | 0.0286 | 0.4690 | 0.3202 |
| IEEE | Algos: PPO & REINFORCE | Temporal | 0.8228 | 0.0285 | 0.5866 | 0.2796 |
| IEEE | Algos: PPO & REINFORCE | Self-Attention | 0.8452 | 0.0234 | 1.1658 | 0.1238 |
| IEEE | Algos: PPO & REINFORCE | Multi-Head | 0.8395 | 0.0235 | 1.0289 | 0.1535 |

--- Descriptive Summary ---
The baseline (No Attention) achieved an average Eval_Score of 0.7965.
❌ All Attention: Did NOT significantly outperform the baseline. (Mean Score: 0.8313, p-value: 0.1757)
❌ Nadaraya-Watson: Did NOT significantly outperform the baseline. (Mean Score: 0.8176, p-value: 0.3202)
❌ Temporal: Did NOT significantly outperform the baseline. (Mean Score: 0.8228, p-value: 0.2796)
❌ Self-Attention: Did NOT significantly outperform the baseline. (Mean Score: 0.8452, p-value: 0.1238)
❌ Multi-Head: Did NOT significantly outperform the baseline. (Mean Score: 0.8395, p-value: 0.1535)
--------------------------------------------------

Visualization saved successfully as Ablation_Study_IEEE_PPO_REINFORCE.jpg


*Note For all tables below -- Significant means REINFORCE is statistically significantly better (p < 0.05)*

REINFORCE Comparison Details (Part-1)
----------------------------------------------------------
PART-1: REINFORCE vs Other Algorithms WITHOUT Attention
----------------------------------------------------------

----------------------------------------------------------
REINFORCE vs Other Algorithms - SIT Schema - Without Attention (Baseline)
----------------------------------------------------------

#### SIT Schema - Without Attention (Baseline)
Table Caption: SIT - REINFORCE vs other algorithms (Without Attention (Baseline)), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| SIT | REINFORCE vs A2C | 0.4907 | 0.2456 | 7.4789 | 0.0000 | Yes |
| SIT | REINFORCE vs DQN | 0.4907 | 0.2456 | 7.4789 | 0.0000 | Yes |
| SIT | REINFORCE vs PPO | 0.4907 | 0.6313 | -2.9224 | 0.9980 | No |


----------------------------------------------------------
REINFORCE vs Other Algorithms - IEEE Schema - Without Attention (Baseline)
----------------------------------------------------------

#### IEEE Schema - Without Attention (Baseline)
Table Caption: IEEE - REINFORCE vs other algorithms (Without Attention (Baseline)), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| IEEE | REINFORCE vs A2C | 0.7496 | 0.6880 | 0.6800 | 0.2504 | No |
| IEEE | REINFORCE vs DQN | 0.7496 | 0.6696 | 0.9003 | 0.1869 | No |
| IEEE | REINFORCE vs PPO | 0.7496 | 0.8434 | -1.3711 | 0.9100 | No |


REINFORCE Comparison Details (Part-2)
----------------------------------------------------------
PART-2: REINFORCE vs Other Algorithms WITH Best Attention Mechanism for REINFORCE
----------------------------------------------------------

Best Attention Mechanism for REINFORCE:
  SIT Schema: Nadaraya-Watson (p=0.0000, Mean=0.8646)
  IEEE Schema: Self-Attention (p=0.0167, Mean=0.8860)

----------------------------------------------------------
REINFORCE vs Other Algorithms - SIT Schema - With Nadaraya-Watson Attention
----------------------------------------------------------

#### SIT Schema - With Nadaraya-Watson Attention
Table Caption: SIT - REINFORCE vs other algorithms (With Nadaraya-Watson Attention), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| SIT | REINFORCE vs A2C | 0.8646 | 0.2456 | 28.8862 | 0.0000 | Yes |
| SIT | REINFORCE vs DQN | 0.8646 | 0.2456 | 28.8862 | 0.0000 | Yes |
| SIT | REINFORCE vs PPO | 0.8646 | 0.7132 | 3.8133 | 0.0001 | Yes |


----------------------------------------------------------
REINFORCE vs Other Algorithms - IEEE Schema - With Self-Attention Attention
----------------------------------------------------------

#### IEEE Schema - With Self-Attention Attention
Table Caption: IEEE - REINFORCE vs other algorithms (With Self-Attention Attention), with one-tailed Welch t-test outputs.

| Schema | Comparison | REINFORCE Mean | Other Algo Mean | t-statistic | p-value | Significant |
|---|---|---|---|---|---|---|
| IEEE | REINFORCE vs A2C | 0.8860 | 0.2729 | 20.9413 | 0.0000 | Yes |
| IEEE | REINFORCE vs DQN | 0.8860 | 0.2360 | 45.9253 | 0.0000 | Yes |
| IEEE | REINFORCE vs PPO | 0.8860 | 0.8044 | 1.7848 | 0.0424 | Yes |



# DETAILED ALGO WISE TABLES - RAW DATA


### SIT

Table : SIT - Algorithm-wise ablation summary with mean, SEM, t-statistic, and p-value.

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


### IEEE

Table Caption: IEEE - Algorithm-wise ablation summary with mean, SEM, t-statistic, and p-value.

| Schema | Algorithm | Setup | Mean | SEM | t_stat | p_value |
| --- | --- | --- | --- | --- | --- | --- |
| IEEE | A2C | No Attention (Baseline) | 0.6880 | 0.0693 | - | - |
| IEEE | A2C | All Attention | 0.4510 | 0.0295 | -3.1484 | 0.9980 |
| IEEE | A2C | Nadaraya-Watson | 0.4322 | 0.0551 | -2.8911 | 0.9969 |
| IEEE | A2C | Temporal | 0.3565 | 0.0499 | -3.8823 | 0.9998 |
| IEEE | A2C | Self-Attention | 0.2729 | 0.0256 | -5.6194 | 1.0000 |
| IEEE | A2C | Multi-Head | 0.7424 | 0.0539 | 0.6188 | 0.2699 |
| IEEE | DQN | No Attention (Baseline) | 0.6696 | 0.0671 | - | - |
| IEEE | DQN | All Attention | 0.2489 | 0.0092 | -6.2073 | 1.0000 |
| IEEE | DQN | Nadaraya-Watson | 0.2360 | 0.0003 | -6.4584 | 1.0000 |
| IEEE | DQN | Temporal | 0.2360 | 0.0003 | -6.4584 | 1.0000 |
| IEEE | DQN | Self-Attention | 0.2360 | 0.0003 | -6.4584 | 1.0000 |
| IEEE | DQN | Multi-Head | 0.2878 | 0.0362 | -5.0041 | 1.0000 |
| IEEE | PPO | No Attention (Baseline) | 0.8434 | 0.0359 | - | - |
| IEEE | PPO | All Attention | 0.8057 | 0.0215 | -0.9031 | 0.8136 |
| IEEE | PPO | Nadaraya-Watson | 0.8343 | 0.0373 | -0.1766 | 0.5697 |
| IEEE | PPO | Temporal | 0.7608 | 0.0528 | -1.2940 | 0.8985 |
| IEEE | PPO | Self-Attention | 0.8044 | 0.0435 | -0.6927 | 0.7539 |
| IEEE | PPO | Multi-Head | 0.8232 | 0.0374 | -0.3901 | 0.6508 |
| IEEE | REINFORCE | No Attention (Baseline) | 0.7496 | 0.0583 | - | - |
| IEEE | REINFORCE | All Attention | 0.8569 | 0.0143 | 1.7881 | 0.0440 |
| IEEE | REINFORCE | Nadaraya-Watson | 0.8008 | 0.0437 | 0.7032 | 0.2432 |
| IEEE | REINFORCE | Temporal | 0.8848 | 0.0147 | 2.2498 | 0.0175 |
| IEEE | REINFORCE | Self-Attention | 0.8860 | 0.0142 | 2.2742 | 0.0167 |
| IEEE | REINFORCE | Multi-Head | 0.8559 | 0.0289 | 1.6342 | 0.0567 |
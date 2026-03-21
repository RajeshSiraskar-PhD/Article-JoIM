# AutoRL Literature Review

##### [**Undermind**](https://undermind.ai)

---


## Table of Contents

- [AutoRL Literature Review](#autorl-literature-review)
- [Funnel outcome](#funnel-outcome)
- [LaTeX section](#latex-section)
- [Evidence mix graphic](#evidence-mix-graphic)
- [Industrial maintenance papers closest to the AutoRL question](#industrial-maintenance-papers-closest-to-the-autorl-question)
- [AutoRL method base that has not yet been translated well into maintenance](#autorl-method-base-that-has-not-yet-been-translated-well-into-maintenance)
- [Takeaways](#takeaways)
- [References](#references)

## AutoRL Literature Review

The journal literature from 2020 to 2026 does not yet show a mature stream of papers that explicitly apply AutoRL to predictive maintenance in manufacturing. The strongest evidence base instead falls into three layers. First, generic AutoRL papers define the automation toolkit through algorithm selection, hyperparameter optimization, reward tuning, and population based training (Bai & Cheng, 2024; Dierkes et al., 2024; Mussi et al., 2022; Parker-Holder et al., 2022; Wan et al., 2022). Second, RL maintenance reviews and tutorials show that predictive and prescriptive maintenance have become active RL application areas, but they do not point to a corresponding industrial AutoRL stream (Ghobadi et al., 2021; Giacotto et al., 2025; Orošnjak et al., 2025; Siraskar et al., 2023; Zhang et al., 2024). Third, manufacturing papers demonstrate that RL can improve maintenance decisions in IIoT, production lines, and machine quality control, yet these studies still rely on manually designed RL pipelines rather than end to end automation (Feng & Li, 2022; Hu et al., 2024; Jiménez et al., 2023; Ong, Wenbo, et al., 2022; Ong, Wang, et al., 2022; Zhao et al., 2023).

This widening path is itself the main finding. A strict search for explicit AutoRL in manufacturing predictive maintenance was too sparse for a stand alone practitioner survey. The evidence therefore had to widen to adjacent papers that automate parts of the RL workflow, and then to journal papers on industrial predictive or prescriptive maintenance via RL. That scarcity strengthens the case that AutoRL for industrial maintenance remains an open research space rather than a settled application niche (Giacotto et al., 2025; Orošnjak et al., 2025; Parker-Holder et al., 2022; Siraskar et al., 2023; Zhang et al., 2024).

## Funnel outcome

| Funnel step | Scope | Outcome |
|:---|:---|:---|
| 1 | Explicit AutoRL for manufacturing predictive maintenance in journals from 2020 to 2026 | No clear journal stream was found in the retrieved set |
| 2 | Maintenance papers that automate part of the RL workflow | Only partial proxies were found, such as transfer learning, hierarchical specialization, and meta reinforcement learning (Abbas et al., 2023; Cheng et al., 2024; Ong, Wang, et al., 2022) |
| 3 | Industrial predictive and prescriptive maintenance via RL | A usable journal comparison set was found across IIoT manufacturing, production lines, steel, machine robot systems, and quality aware maintenance (Feng & Li, 2022; Hu et al., 2024; Jiménez et al., 2023; Ong, Wenbo, et al., 2022; Zhao et al., 2023) |
| 4 | Generic AutoRL method papers for technical grounding | A solid method base exists, but it is not maintenance specific (Bai & Cheng, 2024; Dierkes et al., 2024; Mussi et al., 2022; Parker-Holder et al., 2022; Wan et al., 2022) |

## LaTeX section

``` latex
\section{AutoRL-Literature Review}

The present journal literature offers a clear but asymmetric picture. On one side, AutoRL is now a recognizable technical field concerned with reducing the manual burden of reinforcement learning through algorithm selection, hyperparameter optimization, reward shaping, and dynamic population based search [@Par22; @Mus22; @Die24; @Bai24; @Wan22c]. On the other side, predictive and prescriptive maintenance have become active application domains for reinforcement learning, especially in manufacturing and industrial IoT, where RL is used to learn maintenance and scheduling policies from stochastic system states [@Sir23; @Zha24b; @Gho21]. What is largely missing is the overlap between these two streams. The retrieved journal evidence does not show a mature line of work in which AutoRL is explicitly developed and deployed for manufacturing predictive maintenance.

This gap is important for both research and practice. Industrial maintenance papers increasingly show that RL can outperform heuristic, time based, greedy, or human benchmark policies when the decision problem is formulated well. In an IIoT maintenance resource management setting, a PPO LSTM approach outperformed comparable DRL baselines and human participants by 53\% and 65\%, respectively [@Ong22]. In IIoT manufacturing, transfer learning with demonstrations reduced training wall time by 58\%, showing that learning efficiency is already a practical concern in deployment minded maintenance research [@Ong22b]. In multistage production systems, RL based maintenance decisions reduced system cost by 9.68\% to 39.56\% relative to baseline policies and improved throughput by more than 9\% [@Fen22]. In vacuum packaging machines, deep RL reduced maintenance costs and defect propagation while improving reliability [@Jim23]. These studies show that industrial value exists when RL models are tuned and embedded properly.

Yet the same papers also reveal why AutoRL remains an open problem in maintenance. Most industrial studies still depend on handcrafted choices for state representation, reward structure, model architecture, and training configuration. Even where the workflow is more advanced, such as Transformer driven prognostics linked to DRL maintenance actions [@Zha23d], tailored PPO for machine robot environments [@Hu24], or hierarchical and interpretable maintenance agents [@Abb23], the automation usually applies to one part of the pipeline rather than to the entire RL design stack. In other words, the maintenance literature largely assumes that expert researchers will still choose the algorithm family, configure the search process, and decide what constitutes good reward engineering.

For technical researchers serving practitioners, this is the strongest argument for new work. Manufacturing maintenance is a high value, noisy, partially observed, and deployment constrained domain in which manual RL tuning is expensive and fragile. Generic AutoRL research already offers ingredients that map well onto this need, including population based hyperparameter adaptation, joint reward and hyperparameter optimization, and automated pipeline construction [@Par22; @Mus22; @Die24; @Bai24; @Wan22c]. What the literature still lacks is a maintenance centered synthesis that turns these ingredients into robust industrial decision systems. The gap is therefore not whether RL can help predictive maintenance. The gap is whether RL for predictive maintenance can be made easier to configure, safer to transfer, and more reliable to deploy without depending on repeated expert retuning.
```

## Evidence mix graphic

The chart below summarizes the papers emphasized in this note, not the full 84 paper retrieval.

``` mermaid
pie showData
    title Selected evidence mix in this review
    "Generic AutoRL methods" : 5
    "RL maintenance reviews and tutorials" : 5
    "Manufacturing predictive maintenance via RL" : 6
    "Automation adjacent maintenance proxies" : 3
```

## Industrial maintenance papers closest to the AutoRL question

| Paper | Authors and year | Application domain | RL technique | Hyperparameters and search space |
|:---|:---|:---|:---|:---|
| DRL based PdM resource management (Ong, Wenbo, et al., 2022) | Ong et al. 2022 | IIoT manufacturing with machine and manpower allocation | PPO with LSTM | Training choices are present, but explicit automated search space is not reported in accessible metadata |
| Transferable DRL for IIoT manufacturing (Ong, Wang, et al., 2022) | Ong et al. 2022 | IIoT manufacturing PdM with expert demonstrations | Transfer learning with model free DRL | Transfer reduces tuning burden, but explicit HPO space is not reported in accessible metadata |
| TranDRL prescriptive maintenance (Zhao et al., 2023) | Zhao et al. 2023 | IoT sensor driven maintenance with RUL forecasting | Transformer plus DRL | Model and reward settings are application designed, not framed as AutoRL |
| RL for multistage production systems (Feng & Li, 2022) | Feng and Li 2022 | Multistage manufacturing production and maintenance | RL with approximate dynamic programming | Hyperparameter search space is not emphasized in accessible metadata |
| System level machine robot maintenance (Hu et al., 2024) | Hu et al. 2024 | No wait hot rolling machine robot environment | Tailored PPO | PPO is tailored to the case, but automated tuning space is not reported in accessible metadata |
| Quality aware maintenance for vacuum packaging (Jiménez et al., 2023) | Jiménez et al. 2023 | Vacuum packaging machines in food processing | Deep RL for condition based maintenance | Search space is not reported in accessible metadata |
| Interpretable hierarchical PdM (Abbas et al., 2023) | Abbas et al. 2023 | Predictive maintenance with interpretability emphasis | Hierarchical specialized DRL | Focus is structure and interpretability rather than automated tuning |
| Combinatorial action prescriptive maintenance (Goby et al., 2023) | Goby et al. 2023 | Prescriptive maintenance with large action spaces | DRL for combinatorial actions | Focus is action space design, not automated search over RL configurations |
| Meta RL transfer across fleets (Cheng et al., 2024) | Cheng et al. 2024 | Engineering fleets, adjacent to plant maintenance | Meta reinforcement learning with knowledge transfer | Adaptation is automated across tasks, but this is still not end to end AutoRL for manufacturing PdM |

| Paper | Benefits | Research gaps | Funnel level |
|:---|:---|:---|:---|
| (Ong, Wenbo, et al., 2022) | Better maintenance resource decisions. Reported gains over comparable DRL baselines and human participants | Policy design remains researcher specified. Validation is simulator based | 3 |
| (Ong, Wang, et al., 2022) | 58 percent reduction in training wall time. Strong relevance to practical learning efficiency | Transfer learning is only one slice of AutoRL. Full pipeline automation is absent | 2 |
| (Zhao et al., 2023) | Better late cycle RUL accuracy and effective maintenance prescriptions | Prognostics plus control is integrated, but algorithm selection and HPO remain manual | 3 |
| (Feng & Li, 2022) | Cost reduction of 9.68 percent to 39.56 percent and throughput gain above 9 percent | Strong factory relevance, but not an AutoRL pipeline | 3 |
| (Hu et al., 2024) | Stable performance and lower total maintenance cost in machine robot collaboration | Tailored solution may be hard to port across plants without retuning | 3 |
| (Jiménez et al., 2023) | Reliability gain and large reductions in maintenance cost and defects | Narrow domain. No automated policy configuration layer | 3 |
| (Abbas et al., 2023) | Moves toward interpretable and specialized maintenance agents | Hierarchy is still handcrafted rather than automatically designed | 2 |
| (Goby et al., 2023) | Addresses a hard maintenance decision space with many action combinations | Solves action complexity more than tuning complexity | 2 |
| (Cheng et al., 2024) | Shows transfer and adaptation across related maintenance tasks | Close to AutoRL ideas, but not centered on manufacturing predictive maintenance | 2 |

## AutoRL method base that has not yet been translated well into maintenance

| Paper | Main automation target | Why it matters for maintenance |
|:---|:---|:---|
| (Parker-Holder et al., 2022) | Taxonomy of AutoRL including HPO, meta learning, reward design, and architecture search | Gives the clearest map of what an industrial AutoRL maintenance pipeline would need to automate |
| (Mussi et al., 2022) | End to end AutoRL pipelines for online and offline RL | Useful blueprint for maintenance pipelines that must support different data regimes |
| (Dierkes et al., 2024) | Joint optimization of hyperparameters and reward shape | Highly relevant because maintenance rewards often mix downtime, cost, risk, and quality |
| (Bai & Cheng, 2024) | Population based hyperparameter adaptation | Relevant for nonstationary plant conditions and long training cycles |
| (Wan et al., 2022) | Bayesian generational population based training | Useful for joint architecture and hyperparameter search in large maintenance state spaces |

## Takeaways

- The scarcity result is real. The retrieved journal literature does not reveal a mature stream of explicit AutoRL for manufacturing predictive maintenance (Parker-Holder et al., 2022; Siraskar et al., 2023; Zhang et al., 2024).
- The broader industrial RL maintenance literature is already strong enough to show value. RL improves scheduling, resource allocation, and maintenance timing in IIoT manufacturing and production systems when the pipeline is well designed (Feng & Li, 2022; Hu et al., 2024; Jiménez et al., 2023; Ong, Wenbo, et al., 2022; Ong, Wang, et al., 2022).
- The gap is not the lack of maintenance use cases. The gap is the lack of automation around RL design choices such as algorithm selection, reward engineering, hyperparameter search, and cross site transfer (Bai & Cheng, 2024; Dierkes et al., 2024; Parker-Holder et al., 2022; Wan et al., 2022).
- Partial bridges already exist through transfer learning, meta reinforcement learning, interpretability, and specialized maintenance agents, but these do not yet amount to a full AutoRL maintenance stack (Abbas et al., 2023; Cheng et al., 2024; Ong, Wang, et al., 2022).
- For a research case, the strongest claim is that industry facing predictive maintenance needs not only better RL policies, but also more reliable ways to configure and adapt those policies with less expert retuning across plants, assets, and operating regimes (Giacotto et al., 2025; Mussi et al., 2022; Orošnjak et al., 2025; Parker-Holder et al., 2022; Zhang et al., 2024).

---

## References

Abbas, A. N., Chasparis, G. C., & Kelleher, J. D. (2023). Hierarchical framework for interpretable and specialized deep reinforcement learning-based predictive maintenance. *Data Knowl. Eng.*, *149*, 102240. <https://doi.org/10.1016/j.datak.2023.102240>

Bai, H., & Cheng, R. (2024). Generalized Population-Based Training for Hyperparameter Optimization in Reinforcement Learning. *IEEE Transactions on Emerging Topics in Computational Intelligence*, *8*, 3450–3462. <https://doi.org/10.1109/TETCI.2024.3389777>

Cheng, J., Cheng, M., Liu, Y., Wu, J., Li, W., & Frangopol, D. (2024). Knowledge transfer for adaptive maintenance policy optimization in engineering fleets based on meta-reinforcement learning. *Reliab. Eng. Syst. Saf.*, *247*, 110127. <https://doi.org/10.1016/j.ress.2024.110127>

Dierkes, J., Cramer, E., Hoos, H., & Trimpe, S. (2024). Combining Automated Optimisation of Hyperparameters and Reward Shape. *RLJ*, *3*, 1441–1466. <https://doi.org/10.48550/arXiv.2406.18293>

Feng, M., & Li, Y. (2022). Predictive Maintenance Decision Making Based on Reinforcement Learning in Multistage Production Systems. *IEEE Access*, *10*, 18910–18921. <https://doi.org/10.1109/ACCESS.2022.3151170>

Ghobadi, Z. D., Haghighi, F., & Safari, A. (2021). An overview of reinforcement learning and deep reinforcement learning for condition-based maintenance. *International Journal of Reliability, Risk and Safety: Theory and Application*. <https://doi.org/10.30699/ijrrs.4.2.9>

Giacotto, A., Marques, H., & Martinetti, A. (2025). Prescriptive maintenance: a comprehensive review of current research and future directions. *Journal of Quality in Maintenance Engineering*. <https://doi.org/10.1108/jqme-07-2023-0064>

Goby, N., Brandt, T., & Neumann, D. (2023). Deep reinforcement learning with combinatorial actions spaces: An application to prescriptive maintenance. *Comput. Ind. Eng.*, *179*, 109165. <https://doi.org/10.1016/j.cie.2023.109165>

Hu, B., Chen, Z., Zhen, M., Chen, Z., & Pan, E. (2024). System-Level Predictive Maintenance Optimization for No-Wait Production Machine–Robot Collaborative Environment under Economic Dependency and Hybrid Fault Mode. *Processes*. <https://doi.org/10.3390/pr12081690>

Jiménez, H., Aribisala, A., Cavalcante, C., Do, P., & Lee, C.-G. (2023). A deep reinforcement learning‐based maintenance optimization for vacuum packaging machines considering product quality degradation. *Journal of Food Process Engineering*. <https://doi.org/10.1111/jfpe.14429>

Mussi, M., Lombarda, D., Metelli, A., Trovò, F., & Restelli, M. (2022). ARLO: A Framework for Automated Reinforcement Learning. *Expert Syst. Appl.*, *224*, 119883. <https://doi.org/10.48550/arXiv.2205.10416>

Ong, K. S.-H., Wang, W., Hieu, N. Q., Niyato, D., & Friedrichs, T. (2022). Predictive Maintenance Model for IIoT-Based Manufacturing: A Transferable Deep Reinforcement Learning Approach. *IEEE Internet of Things Journal*, *9*, 15725–15741. <https://doi.org/10.1109/JIOT.2022.3151862>

Ong, K. S.-H., Wenbo, W., Niyato, D., & Friedrichs, T. (2022). Deep-Reinforcement-Learning-Based Predictive Maintenance Model for Effective Resource Management in Industrial IoT. *IEEE Internet of Things Journal*, *9*, 5173–5188. <https://doi.org/10.1109/jiot.2021.3109955>

Orošnjak, M., Saretzky, F., & Kędziora, S. (2025). Prescriptive Maintenance: A Systematic Literature Review and Exploratory Meta-Synthesis. *Applied Sciences*. <https://doi.org/10.3390/app15158507>

Parker-Holder, J., Rajan, R., Song, X., Biedenkapp, A., Miao, Y., Eimer, T., Zhang, B., Nguyen, V., Calandra, R., Faust, A., Hutter, F., & Lindauer, M. (2022). Automated Reinforcement Learning (AutoRL): A Survey and Open Problems. *J. Artif. Intell. Res.*, *74*, 517–568. <https://doi.org/10.1613/jair.1.13596>

Siraskar, R., Kumar, S., Patil, S., Bongale, A., & Kotecha, K. (2023). Reinforcement learning for predictive maintenance: a systematic technical review. *Artificial Intelligence Review*, 1–63. <https://doi.org/10.1007/s10462-023-10468-6>

Wan, X., Lu, C., Parker-Holder, J., Ball, P. J., Nguyen, V., Ru, B., & Osborne, M. A. (2022). Bayesian Generational Population-Based Training. *AutoML*, 14/1–27. <https://doi.org/10.48550/arXiv.2207.09405>

Zhang, Q., Liu, Y., Xiang, Y., & Xiahou, T. (2024). Reinforcement learning in reliability and maintenance optimization: A tutorial. *Reliab. Eng. Syst. Saf.*, *251*, 110401. <https://doi.org/10.1016/j.ress.2024.110401>

Zhao, Y., Yang, J., Wang, W., Yang, H., & Niyato, D. (2023). TranDRL: A Transformer-Driven Deep Reinforcement Learning Enabled Prescriptive Maintenance Framework. *IEEE Internet of Things Journal*, *11*, 35432–35444. <https://doi.org/10.1109/JIOT.2024.3436110>

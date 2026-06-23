---
title: "Rethinking LLM Uncertainty: A Multi-Agent Approach to Estimating Black-Box Model Uncertainty"
title_zh: 重新思考LLM不确定性：一种估计黑盒模型不确定性的多智能体方法
authors: "Yu Feng, Phu Mon Htut, Zheng Qi, Wei Xiao, Manuel Mager, Nikolaos Pappas, Kishaloy Halder, Yang Li, Yassine Benajiba, Dan Roth"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.findings-emnlp.660.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 通过多样化扰动的多智能体黑盒LLM不确定性估计
tldr: 论文指出现有基于自一致性的黑盒LLM不确定性方法可能被误导，因为模型在不同扰动下表现不一。提出DiverseAgentEntropy，利用多个智能体采用知识保持的查询扰动，综合评估不确定性。理论上基于互信息，实验表明该方法显著提升了不确定性估计的准确性和可靠性。
source: EMNLP-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1619, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1609, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1394, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1592, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 746, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 749, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 754, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 735, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 739, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 738, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 740, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1616, \"height\": 2268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 715, \"height\": 2253, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 704, \"height\": 2228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1612, \"height\": 2267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 712, \"height\": 2252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 708, \"height\": 2252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 716, \"height\": 2264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-findings/anthology-2025.findings-emnlp.660/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 706, \"height\": 2236, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 798, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 819, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 794, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 716, \"height\": 805, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1227, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 728, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1614, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1620, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-findings/anthology-2025.findings-emnlp.660/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1558, \"height\": 1579, \"label\": \"Table\"}]"
motivation: 现有黑盒LLM不确定性方法中，模型可能对相同查询的不同重构给出矛盾结果，导致估计偏差。
method: 提出DiverseAgentEntropy，使用多智能体对知识保持的扰动查询进行一致性分析，基于互信息聚合不确定性。
result: 在多个基准上，该方法显著提升黑盒不确定性估计的准确性和校准度。
conclusion: 为黑盒LLM提供了一种更鲁棒的不确定性量化方法，有助于可靠决策。
---

## Abstract
Quantifying uncertainty in black-box LLMs is vital for reliable responses and scalable oversight. Existing methods, which gauge a model’s uncertainty through evaluating self-consistency in responses to the target query, can be misleading: an LLM may confidently provide an incorrect answer to a target query, yet give a confident and accurate answer to that same target query when answering a knowledge-preserving perturbation of the query. We systematically analyze the model behaviors and demonstrate that this discrepancy stems from suboptimal retrieval of parametric knowledge, often due to contextual biases that prevent consistent access to stored knowledge. We then introduce DiverseAgentEntropy, a novel, theoretically-grounded method employing multi-agent interaction across diverse query variations for uncertainty estimation of black-box LLMs. This approach more accurately assesses an LLM’s true uncertainty and improves hallucination detection, outperforming existing self-consistency based techniques.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：现有黑盒大语言模型（LLM）的不确定性估计方法主要基于对同一目标查询进行多次采样、衡量响应的自一致性（self-consistency）来计算熵。但这种做法可能产生误导：模型可能对目标查询给出自信的错误答案，却能在**知识保持的扰动版本**（知识保持扰动，knowledge-preserving perturbation）上给出自信且正确的答案。
- **根源**：论文通过系统分析发现，这种不一致源于模型对**参数化知识的检索不佳**，尤其是**上下文偏差**（contextual biases）导致模型无法稳定地访问存储的知识。
- **重要性**：在高风险领域（医疗、金融、法律），准确估计不确定性至关重要，尤其对于黑盒 API 模型，需要无需内部访问的鲁棒方法。现有方法未能捕捉模型的真实不确定性。

---

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：采用**同一模型的多智能体交互**，将目标查询的多个**知识保持扰动版本**视为不同智能体，通过受控交互使智能体收敛至真实答案，然后基于加权熵计算不确定性。
- **关键技术细节**：
  1. **多样化查询生成**：对目标查询 \(q\)，生成一组 \(Q = \{q_1, q_2, \ldots, q_n\}\)，其中 \(q_1 = q\)，其余为语义等价或基于不同角度的问题（通过提示词自动生成）。
  2. **多智能体交互**：每个智能体 \(A_j\) 用同一模型独立回答对应查询 \(q_j\)。进行多轮一对一交互：智能体选择与自己当前答案最不同的对等体，查看对方的查询和答案后决定是否更新自己的答案。交互终止条件：所有智能体一致、每个智能体连续两轮不变、或达到最大轮数 \(R^*\)。
  3. **不确定性计算**：为每个智能体分配权重 \(w_j = (R - r_j + 1) / \sum_{k=1}^n (R - r_k + 1)\)，其中 \(r_j\) 为该智能体改变答案的次数。最终答案分布为加权概率：\(\tilde{p}_\theta(z_i | q^*) = \sum_{j=1}^n w_j \cdot 1\{A_j = z_i\}\)。然后使用熵公式计算不确定性：
     \[
     U(q) = - \sum_{i} \tilde{p}_\theta(z_i | q^*) \log \tilde{p}_\theta(z_i | q^*)
     \]
  4. **弃权策略**：若不确定性超过阈值（如对应概率(0.6,0.2,0.2)或(0.6,0.4)的熵）或模式答案为“I don't know”，则模型弃权。
- **理论保证**：在模型知道答案的假设下，通过收缩性更新和连通图，加权分布可收敛到真实分布（定理4.9）。

---

### 3. 实验设计
- **数据集**：
  - **实体中心 QA**：PopQA（热门实体+冷门实体）
  - **虚假假设 QA**：FalseQA
  - **通用 QA**：TruthfulQA、FreshQA
- **评估模型**：Llama-3-70b-Instruct、Claude-3-Sonnet（均通过 API 调用）。
- **基准方法**：
  - 不确定性估计基线：P(True)、语义熵（SemanticEntropy, SC SE）、基于亲和图的 Eccentricity/Degree/Eigenvalues、Kernel Language Entropy (KLE) 等。
  - 幻觉检测基线：Greedy、Self-Refine、Self-Evaluation、Multiple-Recite、Self-Consistency (SC)、语义等价问题一致性（SeQ）、多样化问题一致性（DiverseQ）等。
  - 提出两个变体：Agent_L（宽松弃权）、Agent（严格弃权）。
- **主要指标**：AUROC（区分正确/错误响应）、Accuracy、Abstention Rate、Correctness Score、Truthfulness Score，以及 Accuracy-Recall (AR) 曲线。

---

### 4. 资源与算力
- 论文未明确说明使用的 GPU 型号、数量或训练时长（所有实验基于 API 调用）。
- **成本分析**：在附录 A.6 中，自一致性方法约需 5 次 API 调用，而 DiverseAgentEntropy 平均约需 25 次（包括问题生成和交互）。作者指出在优先正确性的高可用场景下，此成本可接受。

---

### 5. 实验数量与充分性
- **数量**：实验覆盖 5 个数据集、2 个模型，对比了 7-8 个基线方法；消融实验包括智能体数量（图5）、交互轮数（图6）、交互格式（一对一群组交互，图7）、鲁棒性分析（图8）；还分析了知识检索错误类型（表1、表9）、响应变化比例（表6）、AR 曲线（图3、图9）等。
- **充分性与公平性**：实验设计全面，涵盖了不同难度（热门/冷门）、不同领域的数据集，并与多种现有方法公平比较。消融实验验证了各组件贡献。但仅使用两个模型（虽具代表性），且数据以短文本 QA 为主。

---

### 6. 论文的主要结论与发现
- **核心结论**：提出的 DiverseAgentEntropy 在不确定性校准（AUROC）和幻觉检测上显著优于所有自一致性基线。在冷门实体数据集（PopQA 冷门）和现实场景（FreshQA、TruthfulQA）上提升最大（+3.8%、+7.5%、+5.2%）。
- **幻觉检测**：基于弃权策略的方法在保持较高准确率的同时，提升了正确率和诚实度（Truthfulness）。
- **来源分析**：验证了模型参数知识检索受上下文偏差影响（表1），多智能体交互能有效缓解此问题。
- **消融结果**：多样化查询生成和智能体交互两者对性能提升均至关重要；一对一组交互优于群组交互；智能体数量超过 4 后收益递减。

---

### 7. 优点
- **方法论创新**：针对自一致性局限，提出通过知识保持扰动和多智能体交互来恢复模型真实不确定性，理论上有收敛保证。
- **实验扎实**：在多个数据集、两个代表性模型上全面评估，并进行了充分的消融和鲁棒性分析。
- **实用性**：适用于黑盒 API 模型，无需内部访问；弃权策略可帮助用户在不确定时避免幻觉输出。
- **分析深入**：不仅报结果，还通过定量（表1）和定性（表9）分析揭示了模型检索失败的三种模式，增强了方法动机。

---

### 8. 不足与局限
- **计算成本**：相比自一致性方法，约需 5 倍 API 调用，在成本敏感场景可能受限。
- **理论假设较强**：收敛证明依赖收缩性和连通性假设，实践中未必完全满足。
- **模型与数据覆盖**：仅评估了两个模型（虽具代表性），且数据集限于短文本事实型 QA，未涉及长文本生成或更复杂的推理任务。
- **响应级不确定性**：论文聚焦于查询级不确定性，未探索响应级不确定性（如模型对自身输出的置信度），后者在开放生成中更重要。
- **交互鲁棒性**：在对有偏信号（如多数错误答案）时性能略有下降，尤其对较弱模型（Llama）影响更大。

（完）

---
title: Uncertainty Propagation on LLM Agent
title_zh: 大语言模型代理的不确定性传播
authors: "Qiwei Zhao, Dong Li, Yanchi Liu, Wei Cheng, Yiyou Sun, Mika Oishi, Takao Osaki, Katsushi Matsuda, Huaxiu Yao, Chen Zhao, Haifeng Chen, Xujiang Zhao"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.acl-long.302.pdf"
tags: ["query:luq"]
score: 7.0
evidence: 大语言模型代理中的不确定性传播
tldr: 针对现有方法仅关注最终步不确定性而忽略多步累积的问题，提出SAUP框架，通过情景感知权重在每一步传播不确定性，提升代理决策的可靠性。
source: ACL-2025-Long
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.302/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.302/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1171, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.302/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1655, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.302/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 750, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-long/anthology-2025.acl-long.302/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1635, \"height\": 373, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.302/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 1322, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.302/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1603, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.302/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1602, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-long/anthology-2025.acl-long.302/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1607, \"height\": 257, \"label\": \"Table\"}]"
motivation: 现有不确定性估计方法主要关注最终步输出，未能捕捉多步决策过程中的累积不确定性和动态环境交互。
method: 提出SAUP框架，在LLM代理的每一步推理中传播不确定性，并引入情景感知权重调整每一步的不确定性贡献。
result: 实验表明SAUP有效量化了多步决策中的不确定性，提高了代理决策的可信度。
conclusion: SAUP通过逐步不确定性传播和情景感知，增强了LLM代理在复杂任务中的可靠性。
---

## Abstract
Large language models (LLMs) integrated into multi-step agent systems enable complex decision-making processes across various applications. However, their outputs often lack reliability, making uncertainty estimation crucial. Existing uncertainty estimation methods primarily focus on final-step outputs, which fail to account for cumulative uncertainty over the multi-step decision-making process and the dynamic interactions between agents and their environments. To address these limitations, we propose SAUP (Situation Awareness Uncertainty Propagation), a novel framework that propagates uncertainty through each step of an LLM-based agent’s reasoning process. SAUP incorporates situational awareness by assigning situational weights to each step’s uncertainty during the propagation. Our method, compatible with various one-step uncertainty estimation techniques, provides a comprehensive and accurate uncertainty measure. Extensive experiments on benchmark datasets demonstrate that SAUP significantly outperforms existing state-of-the-art methods, achieving up to 20% improvement in AUROC.

---

## 论文详细总结（自动生成）

# 论文总结：Uncertainty Propagation on LLM Agent (SAUP)

## 1. 核心问题与整体含义

- **研究动机**：大语言模型（LLM）集成的多步智能体系统在复杂决策中广泛应用，但输出可靠性不足。现有不确定性估计方法仅关注最终步输出，忽略了多步过程中的不确定性累积以及智能体与环境的动态交互，导致决策风险增高（例如图1中的法律案例）。
- **核心问题**：如何全面、准确地估计LLM智能体在多步推理中的整体不确定性。
- **整体意义**：提出SAUP框架，通过情景感知的不确定性传播，提升智能体决策的可信度和可靠性，为高安全场景（如医疗、自动驾驶）提供保障。

## 2. 方法论：核心思想与关键技术

- **核心思想**：将每一步的不确定性传播到最终，并依据智能体所处的情景（如推理偏离程度）赋予不同权重，从而得到整体不确定性。
- **关键公式**：
  \[
  U_{\text{agent}} = \sqrt{\frac{1}{N} \sum_{i=1}^N (W_i \cdot U_i)^2}
  \]
  其中，\(U_i\)为第\(i\)步的单步不确定性（使用归一化熵计算），\(W_i\)为情景权重。
- **单步不确定性**：采用归一化预测熵（Normalized Entropy），对Thinking和Action分别计算并求和。
- **情景权重估计**：
  - 引入两个距离指标：
    - **Inquiry Drift** \(D_a\)：全局语义偏移（当前轨迹与原始问题间的差异）。
    - **Inference Gap** \(D_o\)：局部推理断层（同一步内思考与观测的差异）。
  - 使用连续隐马尔可夫模型（CHMM）将 \((D_a, D_o)\) 作为观测变量，学习三个隐藏状态（正确轨迹、中度偏离、高度偏离），输出权重 \(W_i\)。
- **算法流程**（Algorithm 1）：
  1. 对每一步\(n\)，计算不确定性\(U_n\)和距离\((D_{an}, D_{on})\)。
  2. 若使用CHMM，将距离序列输入模型得到权重序列；否则直接使用距离和作为权重。
  3. 最终根据公式计算整体不确定性。

## 3. 实验设计

- **数据集与任务**：
  - HotpotQA（多跳问答，2000样本）
  - MMLU（多领域选择题，10题/子任务）
  - StrategyQA（隐式推理判断题，229题）
- **基准Agent框架**：ReAct (Yao et al., 2022)
- **骨干LLM**：
  - LLaMA3 8B / 70B（开源，可获取logits）
  - GPT-4o（API访问，仅黑盒）
- **对比方法**：
  - 单步不确定性方法：Predictive Entropy, Likelihood, Normalized Entropy, P(True), Semantic Entropy
  - 简单传播方法：算术平均、几何平均、均方根（RMS）
  - SAUP变体：SAUP-P（位置权重）、SAUP-D（距离权重）、SAUP-PD（混合）、SAUP-HMMD（学习型）
- **评估指标**：AUROC（区分正确/错误回答的能力）

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。
- 仅提及HMM训练使用Baum-Welch算法，数据需求小，计算高效。
- 未提供LSTM/Transformer对比实验的具体算力细节。

## 5. 实验数量与充分性

- **多组主要实验**：在3个数据集 × 3种LLM × 多种baseline下，共报告了约9组对比表（表1-3），以及多组消融实验（图4、图5）。
- **消融实验丰富**：
  - 不同传播方式（算术、几何、RMS）
  - 不同情境权重替代方案（位置、距离、混合、HMM）
  - 不同序列模型（HMM vs LSTM vs Transformer）随数据量的变化
- **可视化分析**（图5）展示了不同方法下正确/错误样本的分离效果。
- **充分性评价**：实验设计较为全面，覆盖了多种场景、多种模型和多种不确定性估计方法，验证了SAUP在不同条件下的优势。但未在所有任务上使用相同规模的完整测试集（如HotpotQA仅随机采样2000题，MMLU每子任务仅10题），可能存在统计偏差风险。

## 6. 主要结论与发现

1. SAUP在所有数据集和LLM上显著优于现有单步不确定性方法，AUROC最高提升20%（如StrategyQA上达0.809 vs 0.71）。
2. 内部步骤的不确定性对整体估计有益，简单传播（RMS）已优于单步方法。
3. 学习型情境权重（CHMM）优于固定权重方案（位置、距离），在小数据集上表现稳健。
4. HMM在数据受限时优于LSTM/Transformer，后者需要更多数据才能达到同等效果。
5. SAUP在复杂任务（如StrategyQA）上的优势更为明显，表明情景感知对长链推理场景尤为关键。

## 7. 优点

- **创新性**：首次提出在多步智能体中传播不确定性并引入情景权重，填补了现有研究空白。
- **兼容性**：SAUP可嵌入任意单步不确定性估计方法，具有通用性。
- **可解释性**：通过Inquiry Drift和Inference Gap量化推理偏离，直观易懂。
- **实验充分**：涵盖多种数据集、模型和消融场景，验证了方法的鲁棒性和有效性。
- **实践友好**：HMM作为默认权重学习器，计算高效，适合数据稀缺场景。

## 8. 不足与局限

- **依赖人工标注**：学习型情境权重需要人工标注正确/错误轨迹，耗时且易出错，可能限制泛化性。
- **单步误差传导**：若单步不确定性估计本身不准（例如LLM输出概率不校准），则传播效果会打折扣。
- **数据集规模偏小**：HotpotQA仅采样2000题，MMLU每子任务仅10题，统计显著性可能不足。
- **未考虑噪声环境**：假设外部观测可被准确获取，实际动态环境中可能存在噪声或缺失。
- **未公开代码与细节**：无法完全复现实验结果（仅提供算法伪代码）。

（完）

---
title: "The Hidden Dimensions of LLM Alignment: A Multi-Dimensional Analysis of Orthogonal Safety Directions"
title_zh: LLM对齐的隐藏维度：正交安全方向的多维分析
authors: "Wenbo Pan, Zhichao Liu, Qiguang Chen, Xiangyang Zhou, Yu Haining, Xiaohua Jia"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=wGFEzfhFae"
tags: ["query:smd"]
score: 6.0
evidence: 分析多维安全方向以理解并保持对齐
tldr: 该论文发现LLM安全对齐行为由表示空间中的多维方向共同控制，而非单一方向。通过分析Llama3 8B安全微调时的表示变化，识别出一个主拒绝方向和多个可解释的细小方向。这一发现为安全数据的选择和策展提供了机制性指导，有助于在微调过程中更有针对性地保护对齐。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 807, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 821, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 845, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 805, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1764, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1771, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 845, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 845, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 844, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1664, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 882, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wgfezfhfae/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1668, \"height\": 1043, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1720, \"height\": 1115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1317, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 835, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 833, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 843, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 979, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wgfezfhfae/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1277, \"height\": 188, \"label\": \"Table\"}]"
motivation: 先前将安全行为建模为单一方向，限制了对其机制的理解，需探索多维安全方向。
method: 在Llama 3 8B的安全微调过程中，研究表示空间中的正交方向，分析各方向与拒绝行为的关系。
result: 发现一个主导拒绝方向及多个代表不同语义的细小方向，揭示了安全对齐的多维本质。
conclusion: 多维安全方向的识别为微调中的对齐保持提供了更精细的指导，有助于设计数据混合策略。
---

## Abstract
Large Language Models' safety-aligned behaviors, such as refusing harmful queries, can be represented by linear directions in activation space. Previous research modeled safety behavior with a single direction, limiting mechanistic understanding to an isolated safety feature. In this work, we discover that safety-aligned behavior is jointly controlled by multi-dimensional directions. Namely, we study the vector space of representation shifts during safety fine-tuning on Llama 3 8B for refusing jailbreaks. By studying orthogonal directions in the space, we first find that a dominant direction governs the model's refusal behavior, while multiple smaller directions represent distinct and interpretable features like hypothetical narrative and role-playing. We then measure how different directions promote or suppress the dominant direction, showing the important role of secondary directions in shaping the model's refusal representation. Finally, we demonstrate that removing certain trigger tokens in harmful queries can mitigate these directions to bypass the learned safety capability, providing new insights on understanding safety alignment vulnerability from a multi-dimensional perspective.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：现有研究将大语言模型的安全对齐行为（如拒绝有害查询）建模为激活空间中的单一线性方向，但这种“单方向”视角忽略了安全行为背后可能存在的多维特征。作者质疑这种简化是否遗漏了更丰富的机制。
- **整体含义**：该论文旨在揭示安全对齐行为实际上由多个正交方向共同控制——一个主导方向负责主要的拒绝行为，而多个“非主导”方向编码了诸如“假设性叙事”“角色扮演”等间接但关键的安全相关特征。理解这一多维空间有助于解释安全对齐的脆弱性，并为更鲁棒的安全训练提供指导。

## 2. 方法论

### 核心思想
- 定义**安全残差空间**（Safety Residual Space）为安全微调前后表示偏移的线性张成空间。通过奇异值分解（SVD）提取该空间的正交主成分。
- 假设：微调残差中的主成分包含安全相关的特征方向；正交方向可能代表不同且可解释的安全特征。

### 关键技术细节
- **安全残差空间构建**：学习一个仿射变换 $S(x) = Wx + b$ 来逼近微调后的真实变换 $T(x)$，最小化均方误差。$W - I$ 的SVD右奇异向量即为特征方向。
- **方向解释**：采用**部分层相关性传播（PLRP）**——将表示投影到选定方向张成的空间，将投影的范数作为相关性分数，反向传播到输入token或早期层的方向，从而识别每个方向最相关的token。
- **干预实验**：通过从激活中减去特定方向（$x := x - \alpha v$）来消融该方向，观察对拒绝行为的影响。

### 算法流程（文字说明）
1. 对安全微调前后的模型，收集训练数据上的激活，学习残差映射 $S(x)$。
2. 对 $W - I$ 做SVD，取前k个右奇异向量作为正交特征方向。
3. 对每个方向应用PLRP，计算每个输入token对方向的贡献，归纳语义。
4. 进行干预：移除某方向（如 $L14\text{-}C6$）后生成，测量攻击通过率变化。
5. 设计**触发器移除攻击**：利用PLRP识别触发token，迭代地重写有害提示以避开这些token，测试绕过安全对齐的效果。

## 3. 实验设计

### 数据集
- **安全微调数据集**：2600个样本，包含来自STRONG REJECT的毒性样本，应用8种越狱方法（PAIR、ReNellm、GPTFuzz、GCG、CodeChameleon、Flip、Simple、Trigger Removal）生成有害示例；另加入50%来自OR-Bench的无害样本。
- **测试集**：60个与训练集不重叠的STRONG REJECT样本，施加所有越狱方法；480个OR-Bench无害样本。

### Benchmark与评估指标
- **STRONG REJECT分数**：衡量响应有害性（分数越高越有害）。
- **拒绝准确率**：模型在有害/无害样本上拒绝的正确率。
- **攻击通过率**（Attack Pass Rate）：有害提示成功绕过安全机制的比率。

### 对比方法
- 基线越狱方法：PAIR、ReNellm、GPTFuzz、GCG、CodeChameleon、Flip、Simple、Trigger Removal（本文提出）。
- 方向比较：Probe Vector（从对比对学习的单一拒绝方向）、Best-of-N（从基座模型激活SVD中选择最佳方向）。

## 4. 资源与算力
- **明确说明**：文中提及所有实验使用**六块A800 GPU**。安全微调（SSFT和DPO）均训练1个epoch。未提供具体训练时长。

## 5. 实验数量与充分性
- **实验组数**：包括以下主要实验：
  1. 有效秩分析（图2，不同层和能量阈值）。
  2. 主导方向预测拒绝准确率对比（图3，Probe Vector vs. Dominant vs. Best-of-N）。
  3. PLRP解释方向语义（表1、表2，手写示例和全测试集聚合）。
  4. 方向消融攻击（图4，移除L14-C6对PAIR攻击的特异性影响）。
  5. 层间相关性传播（图5）。
  6. 非主导方向抑制与触发器移除攻击的效果（图6，投影值曲线）。
  7. N-SHOT安全训练对比（表3，不同暴露样本数下各越狱方法的攻击通过率）。
  8. 额外模型尺度实验（Llama 3.2 3B和Ministral 8B，附录C.3）。
  9. 通用能力影响评估（附录C.4，困惑度）。
- **充分性评价**：
  - **充分**：覆盖了方向发现、语义解释、因果干预、攻击绕过、训练动态、模型规模泛化、通用能力影响等多个维度。
  - **客观公平**：使用公共数据集和标准评估指标；对比方法包括现有最先进的越狱方法；实验结果量化呈现（准确率、分数、投影值）。
  - **不足之处**：仅在一个基础模型（Llama 3 8B）上进行了主要分析，虽然在附录中补充了Llama 3.2 3B和Ministral 8B，但未在其他架构（如GPT、Pythia）上验证。N-SHOT实验仅设置了0到160样本的暴露量，可能不足以模拟实际训练规模。

## 6. 主要结论与发现
1. **安全残差空间是低秩线性的**：有效秩在早期层保持为1，在中后层增加，表明存在多个特征方向。
2. **主导方向预测拒绝**：主导方向（LN-C1）在中间层后对拒绝行为具有高预测准确性，与Probe Vector性能相当。
3. **非主导方向代表不同语义**：例如L14-C2对应“假设性叙事”，L14-C5对应“ChatGPT引用”，L14-C6对应“Sure, I’m happy to help”（与PAIR攻击相关）。
4. **非主导方向因果影响拒绝**：移除L14-C6特异性消除对PAIR攻击的拒绝能力（攻击通过率从0%升至80%），而对其他攻击影响较小。
5. **层间动态**：早期层特征方向相互混合发展，后期层主导方向加强并减少不确定性。
6. **脆弱性**：通过抑制非主导方向或移除触发token，可以绕过安全对齐，且触发器移除攻击对安全微调具有鲁棒性（在80样本后仍有约30%通过率）。

## 7. 优点
- **方法论创新**：提出安全残差空间概念，无需训练探针即可自动发现多个安全特征方向，避免了探针对比对的依赖。
- **解释性强**：PLRP方法为每个方向提供了token级别的语义归因，使抽象方向变得可解释。
- **因果验证**：通过直观的方向消融实验证实了非主导方向的因果作用，而非仅仅相关性分析。
- **实用洞察**：揭示了安全训练可能学习到越狱模式的“虚假相关”，并设计了触发器移除攻击，对安全对齐的鲁棒性研究有直接应用价值。
- **实验全面**：包含多种越狱方法、不同暴露设置、不同模型规模、通用能力影响评估，论证充分。

## 8. 不足与局限
1. **模型范围有限**：主要实验基于Llama 3 8B，虽在附录中补充了两个其他模型，但样本量小，未验证更大模型（如70B）或不同训练派系（如GPT、Mistral）的普适性。
2. **线性假设约束**：假设安全残差空间是线性的，但作者指出部分方向在层间可能翻转，线性表示并非完全准确。非线性特征可能被忽略。
3. **数据复杂度不足**：训练数据集仅包含明确的有害/无害二分标签，实际安全对齐数据可能包含更细粒度的偏好（如微妙的不安全边缘案例）。数据复杂度的增加可能使方向解释更困难。
4. **触发器移除攻击的实用性限制**：攻击需要迭代重写（最多30次尝试），成本与现有越狱方法类似，但文中未评估其在黑盒场景下的可迁移性。
5. **未讨论防御**：论文侧重于分析脆弱性并展示绕过方法，但未提出基于这些分析的防御方案（如动态检测非主导方向的变化）。
6. **计算成本**：PLRP需要反向传播，对大模型可能负担较重；文中未报告推理时间成本。

（完）

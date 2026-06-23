---
title: Uncertainty-Aware Contrastive Decoding
title_zh: 不确定性感知的对比解码
authors: "Hakyung Lee, Subeen Park, Joowang Kim, Sungjun Lim, Kyungwoo Song"
date: 2025-07-01
pdf: "https://aclanthology.org/2025.findings-acl.1352.pdf"
tags: ["query:luq"]
score: 8.0
evidence: 不确定性感知的对比解码用于大语言模型
tldr: 对比解码（CD）使用静态权重，对架构和输入敏感导致次优。本文提出不确定性感知对比解码（UCD），在每个解码步根据不确定性动态调整两个模型的贡献，引入累积能量函数量化不确定性。实验显示UCD在事实正确性和一致性上优于CD。
source: ACL-2025-Findings
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1352/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 798, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1352/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 948, \"label\": \"Figure\"}, {\"url\": \"assets/figures/acl-2025-findings/anthology-2025.findings-acl.1352/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 281, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1341, \"height\": 722, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 805, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1646, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 798, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1646, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1638, \"height\": 1144, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1334, \"height\": 854, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 797, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 808, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 801, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/acl-2025-findings/anthology-2025.findings-acl.1352/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1562, \"height\": 339, \"label\": \"Table\"}]"
motivation: 对比解码的静态权重导致对模型和输入的敏感性，错误传播。
method: 提出UCD方法，基于不确定性动态调整专家模型和基础模型的贡献。
result: UCD在文本可靠性和事实一致性上优于传统对比解码。
conclusion: 不确定性感知的动态调整能有效提升解码质量。
---

## Abstract
Large language models excel in a wide range of natural language processing tasks, but generating factually accurate and consistent outputs remains a challenge. To improve text reliability, Contrastive Decoding (CD) refines token selection by leveraging differences between an expert and base model, penalizing low-quality token choices. However, CD employs static weighting between models, making it sensitive to variations in model architecture and input characteristics, often resulting in suboptimal token selection and error propagation throughout generation. We propose Uncertainty-Aware Contrastive Decoding (UCD), a method that dynamically adjusts model contributions at each decoding step based on uncertainty. We introduce a cumulative energy function, where uncertainty is quantified as the negative log-sum-exp over logits, and decomposed into entropy and expected logit components. This energy serves as a dynamic confidence signal, guiding adaptive model weighting during generation. We demonstrate through extensive experiments that UCD significantly improves factual accuracy and reliability over existing decoding methods. Finally, we provide a theoretical analysis showing that our energy function serves as a well-defined uncertainty metric capturing model confidence. Our code is available at: https://github.com/MLAI-Yonsei/UCD.

---

## 论文详细总结（自动生成）

# 不确定性感知的对比解码（UCD）——论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：大语言模型（LLM）在文本生成中常出现事实不准确、重复、幻觉等可靠性问题。现有对比解码（Contrastive Decoding, CD）通过对比专家模型与基础模型的输出差异来筛选低质量token，但采用**静态权重**（固定比例）结合两者贡献，导致：
  - 对模型架构和输入特征敏感，权重无法自适应调整。
  - 生成过程中错误累积和传播，造成次优token选择。
- **研究动机**：需要一种能**动态调整模型贡献**的机制，在每一步解码中根据模型的实时置信度自适应地平衡专家与基础模型，从而提升生成的事实准确性与一致性。
- **整体含义**：本文提出的不确定性感知对比解码（Uncertainty-Aware Contrastive Decoding, UCD）首次将**累积能量函数**作为不确定性度量引入对比解码，实现无需额外训练的自适应权重调整，显著改善文本可靠性。

## 2. 方法论

### 核心思想
- 对每个解码步，利用专家模型和基础模型输出的logit信息，定义一个**累积能量函数**，其值越高表示模型对该步的预测越有信心。
- 基于两种模型的能量值动态计算各自的权重（能量归一化），然后构建加权后的对比logit向量，选择最大logit对应的token。
- 能量函数不仅考虑当前步的logit分布，还通过**logit轨迹**（对历史选择token的logit进行折扣累加）引入时序信息，确保动态调整的稳定性。

### 关键技术细节
- **Logit轨迹（Logit Trace）**：  
  `ℓ_t^(M) = β · ℓ_{t-1}^(M) + z_t^(M)[ˆx_{t-1}]`  
  其中`β`为折扣因子（推荐设为1），`z_t^(M)[ˆx_{t-1}]`为模型M在上一步选择token上的logit值。轨迹可写成：  
  `ℓ_t^(M) = Σ_{k=1}^{t-1} β^{t-1-k} · z_k^(M)[ˆx_k]`。

- **累积能量函数（Cumulative Energy）**：  
  `Energy(z_t, ℓ_t) = T · log Σ_{v∈V} exp((z_t[v] + ℓ_t)/T)`  
  其中`T`为温度参数，控制softmax的尖锐程度。能量越高表示信心越强（文中定义能量为负的对数概率，本质是log-sum-exp值）。

- **能量分解（Theorem 1）**：  
  `Energy(z_t, ℓ_t) = T·H(p_t) + E_{p_t}[z_t] + ℓ_t`  
  即能量 = 温度×熵（不确定性部分） + 期望logit（即时信心部分） + logit轨迹（历史信心部分）。这一分解为能量作为不确定性度量提供了理论支持。

- **动态权重**：  
  `w_t^(EXP) = E_t^(EXP) / (E_t^(EXP) + E_t^(BASE))`  
  `w_t^(BASE) = E_t^(BASE) / (E_t^(EXP) + E_t^(BASE))`  
  仅当能量为正时生效，以避免使用过度不确定的模型。

- **UCD token选择**：  
  `z_t^UCD[v] = 2·w_t^(EXP)·z_t^(EXP)[v] - w_t^(BASE)·z_t^(BASE)[v]`  
  然后选择argmax得到生成token。该公式可扩展到多专家场景（如两个专家直接加权求和）。

### 算法流程（文字说明）
1. 对每步解码输入，分别由专家模型和基础模型计算logits。
2. 更新两个模型的logit轨迹（按折扣因子累加）。
3. 计算每个模型的累积能量（使用当前logits和轨迹）。
4. 根据能量值归一化得到动态权重。
5. 计算加权的UCD logit向量，并选择最大logit对应的token作为输出。
6. 重复上述步骤直到生成完整序列。

## 3. 实验设计

### 使用的数据集/场景
- **去幻觉评估**：TruthfulQA（816个样本），包括多项选择（MC1/MC2/MC3）和开放生成两种评估。
- **推理能力评估**：涵盖数学推理（GSM8K, SVAMP, MultiArith）、通用知识（MMLU）、常识推理（Arc-Challenge, CommonsenseQA, StrategyQA）、符号推理（Last Letter Concatenation, Coin Flip）、BIG bench任务（Date Understanding, Sports Understanding）等，每数据集200个样本。
- **领域特定任务**：BioASQ（生物医学问答），包含Factoid、List、Yes/No、Summary四类，复用验证集和测试集（310个测试样本）。

### Benchmark与对比方法
- **对比方法**：
  - 标准对比解码（CD）
  - DoLa（层对比）
  - SH2（自强调停顿）
  - ITI（推理时干预）
  - Nudging（推理时对齐）
  - Proxy-Tuning（PT，三模型代理调优）
  - Co-LLM（协作多LLM）
  - Greedy Decoding（贪婪解码）
- **公平性**：所有方法使用相同的prompt模板，对于TruthfulQA和推理任务，均使用推理（无微调）。BioASQ任务中，UCD使用了两个微调专家模型（Meditron-7B和LLaMA2-7B-Base fine-tuned on BioASQ），与其他方法（如Co-LLM、PT）共享相同的微调基础。

### 主要实验结果
- **TruthfulQA多项选择**：UCD在MC1、MC2、MC3上全面优于CD和单独模型（如13B-Chat+7B-Base达到MC1 39.46, MC2 65.24, MC3 36.13），较贪婪解码显著提升。
- **LLaMA 3.2验证**：UCD（3B+1B）在MC1/2/3上分别达50.12/74.15/46.94，远超CD和贪婪解码，表明跨架构泛化性。
- **推理基准**：UCD扩展Proxy-Tuning（三模型），平均得分48.8，在所有方法中最高，几乎在全部11个任务上超越对比方法。
- **领域特定（BioASQ）**：UCD（FT 7B-Base + Meditron-7B）在Factoid上达30.3，平均36.2，优于多数大规模模型（如Meditron-70B的33.7）和对比方法。
- **消融实验**：变化折扣因子β（0~1），UCD始终优于基于熵的不确定性变体；温度参数T=1时性能最优，验证了理论分析。
- **定性分析**：UCD正确回答“Darth Vader对Luke说的话”等事实性问题，而CD和其他模型回答错误或回避。

## 4. 资源与算力

- 论文在微调部分明确说明：使用**4张A100 80G GPU**，结合FlashAttention和DeepSpeed进行LLaMA 2-7B的微调（BioASQ数据集）。
- 对于推理和对比实验，未明确给出具体的GPU数量或时长，但提到UCD在单GPU上平均每token解码时间为0.0751秒（13B-Chat+7B-Chat），优于CD（0.0910秒/token）和70B单模型（0.1137秒/token），表明计算效率较高。
- 总体来看，实验所需的计算资源较为合理，但大规模模型（70B）的实验可能受限于资源而部分展开。

## 5. 实验数量与充分性

- **实验数量**：共进行了三组主要实验（去幻觉、通用推理、领域任务），还包括消融实验（β、T、能量vs熵）和定性分析，总计超过10组对比结果。
- **充分性与公平性**：
  - 数据集覆盖广泛：从基准建模（TruthfulQA）、多类推理到生物医学专用，场景多样。
  - 对比方法包括当前主流方法（DoLa、ITI、SH2、CD、PT、Co-LLM等），且结果多取自原始论文或统一复现，确保可比性。
  - 消融实验验证了各组件的贡献（累积能量、logit轨迹、温度等）。
  - 在LLaMA 3.2上的额外实验证明了跨架构的稳健性。
- **不足之处**：部分推理任务仅取200个样本，可能无法完全反映模型在所有样本上的能力；领域任务仅在BioASQ上评估，未拓展至其他专业领域。整体而言实验设计合理，结论可信。

## 6. 主要结论与发现

- UCD通过**动态权重**（基于累积能量）替代CD的静态权重，在每一步解码中自适应地调整专家与基础模型的贡献，显著提升了生成文本的**事实准确性和可靠性**。
- 理论分析表明累积能量函数可分解为熵、期望logit和logit轨迹，分别表征不确定性、即时信心和历史信心，提供了坚实的理论依据。
- 实验证明UCD在多个基准（TruthfulQA、推理、领域问答）上均优于现有对比解码方法，且具有**高效推理**（单GPU即可运行）和**跨模型泛化**（适用于不同架构和尺寸）的优势。
- 动态不确定性感知能够有效缓解幻觉和错误传播，提升文本质量。

## 7. 优点

- **方法创新**：首次将累积能量作为不确定性度量引入对比解码，兼顾即时与历史信息，无需额外训练或搜索优化。
- **理论基础扎实**：提供了能量分解定理，清晰证明能量是如何综合熵、期望logit和logit轨迹的，具有可解释性。
- **实验全面**：覆盖幻觉缓解、多类型推理、领域专用任务，且包含充分的消融和泛化验证。
- **效率高**：单步解码无需迭代优化，计算开销与标准CD相当甚至更低（动态权重仅需一次归一化）。
- **扩展灵活**：支持双模型对比场景（专家+基础）和三模型/多专家场景（如Proxy-Tuning扩展），通用性强。
- **代码开源**：提供了GitHub代码，便于复现和后续研究。

## 8. 不足与局限

- **实验覆盖有限**：
  - 仅在LLaMA2（7B/13B/70B）和LLaMA 3.2（1B/3B）上验证，未测试其他主流模型（如GPT系列、Mistral、Gemma等）。
  - 领域任务仅局限在生物医学（BioASQ），未扩展到法律、金融等其他专业领域。
- **GPU资源限制**：论文自身承认因资源限制，未能对所有70B和更大模型进行充分实验，可能影响对极大规模模型下UCD表现的观察。
- **评估偏差风险**：
  - 部分推理任务使用GPT-4自动评分，可能存在来自GPT-4自身的偏差或判断错误。
  - TruthfulQA开放生成评估采用第三方重评估工具（基于LLaMA训练judge），其准确性未与人工评价严格对齐。
- **超参数敏感性**：温度T和折扣因子β需要根据任务调整（最优T≈1，β=1），虽然提供了理论指导，但实际使用可能需要少量调参。
- **多语言缺失**：所有实验均基于英文数据集，未测试UCD对非英语文本的适用性。
- **应用限制**：UCD需要至少两个模型（专家和基础）同时运行，增加了内存开销和部署复杂度；在最简单场景下（单模型）无法直接使用。

（完）

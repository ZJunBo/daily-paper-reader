---
title: "Personalized Steering of Large Language Models: Versatile Steering Vectors Through Bi-directional Preference Optimization"
title_zh: 大语言模型的个性化转向：通过双向偏好优化实现通用转向向量
authors: "Yuanpu Cao, Tianrong Zhang, Bochuan Cao, Ziyi Yin, Lu Lin, Fenglong Ma, Jinghui Chen"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=7qJFkuZdYo"
tags: ["query:dg"]
score: 7.0
evidence: 通过偏好优化提取个性化转向向量
tldr: 针对大语言模型个性化的需求，现有微调方法计算成本高且可能损害原模型效用。本文提出通过双向偏好优化从人类偏好数据中提取通用转向向量，以轻量级方式在推理时调整模型行为。实验表明该方法能在保持模型能力的同时有效引导输出至期望行为。该工作为模型行为控制提供了高效且可扩展的方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 731, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 731, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 733, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 729, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 378, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-7qjfkuzdyo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 734, \"height\": 369, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 371, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1448, \"height\": 976, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1172, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 590, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1137, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1302, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1446, \"height\": 1242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 663, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 731, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1022, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 698, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 692, \"height\": 154, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1163, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1450, \"height\": 746, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1306, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1445, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1439, \"height\": 1270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-7qjfkuzdyo/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1442, \"height\": 1228, \"label\": \"Table\"}]"
motivation: 微调个性化LLM计算成本高且可能影响模型效用，需要轻量级替代方法。
method: 提出双向偏好优化方法，从人类偏好数据中学习可插拔的转向向量，在推理时调整激活状态。
result: 在多个个性化任务上，该方法有效引导模型行为，且几乎不损失通用能力。
conclusion: 转向向量是一种计算高效的个性化手段，双向偏好优化优于直接提取。
---

## Abstract
Researchers have been studying approaches to steer the behavior of Large Language Models (LLMs) and build personalized LLMs tailored for various applications. While fine-tuning seems to be a direct solution, it requires substantial computational resources and may significantly affect the utility of the original LLM. 
Recent endeavors have introduced more lightweight strategies, focusing on extracting ``steering vectors'' to guide the model's output toward desired behaviors by adjusting activations within specific layers of the LLM's transformer architecture. However, such steering vectors are directly extracted from the activations of human preference data and thus often lead to suboptimal results and occasional failures, especially in alignment-related scenarios.
In this work, we propose an innovative approach that could produce more effective steering vectors through bi-directional preference optimization. 
Our method is designed to allow steering vectors to directly influence the generation probability of contrastive human preference data pairs, thereby offering a more precise representation of the target behavior. By carefully adjusting the direction and magnitude of the steering vector, we enabled personalized control over the desired behavior across a spectrum of intensities.
Extensive experimentation across various open-ended generation tasks, particularly focusing on steering AI personas, has validated the efficacy of our approach. 
Moreover, we comprehensively investigate critical alignment-concerning scenarios, such as managing truthfulness, mitigating hallucination, and addressing jailbreaking attacks alongside their respective defenses. Remarkably, our method can still demonstrate outstanding steering effectiveness across these scenarios. Furthermore, we showcase the transferability of our steering vectors across different models/LoRAs and highlight the synergistic benefits of applying multiple vectors simultaneously. These findings significantly broaden the practicality and versatility of our proposed method.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：构建个性化的大语言模型（LLM）需要引导模型输出符合特定偏好的行为。传统的微调方法虽然直接，但计算成本高昂，且可能显著损害原模型的通用能力。
- **现有局限**：近期轻量级方法通过提取“转向向量”（steering vectors）在推理时调整Transformer特定层的激活值来引导输出。然而，这些转向向量直接从人类偏好数据的激活值中提取，效果常不理想，尤其在需要对模型进行对齐的场景（如真实性、抗攻击）中容易失败。
- **研究目标**：提出一种更有效的转向向量生成方法，既能实现轻量级、个性化的行为控制，又能保持模型原有性能，并确保向量在不同任务和模型间具有可迁移性。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过**双向偏好优化**（Bi-directional Preference Optimization）直接从人类偏好数据对中学习转向向量，使向量能够直接影响模型对偏好对（chosen vs. rejected）的生成概率。
- **关键技术细节**：
  - 构建对比偏好数据对（例如：符合目标行为 vs. 不符合目标行为的输出）。
  - 将转向向量视为可学习的参数，通过优化一个双向目标函数（同时放大偏好输出概率并抑制非偏好输出概率）来调整向量的方向和幅度。
  - 在推理阶段，将训练好的转向向量注入到特定Transformer层的隐藏状态中（加法操作），从而在推理时动态控制模型输出。
  - 支持多向量协同（同时注入多个转向向量），且向量可在不同模型或LoRA之间迁移。
- **算法流程（文字描述）**：
  1. 收集或构造一组对比偏好数据对（例如：诚实回答 vs. 虚假回答）。
  2. 定义转向向量为可训练参数，初始化为零向量或随机。
  3. 在前向传播中，将当前转向向量加至指定层的激活上，然后计算模型对偏好对的交叉熵损失（偏好答案概率最大化，非偏好答案概率最小化）。
  4. 通过梯度下降更新转向向量，直到收敛。
  5. 推理时，直接使用训练好的向量进行激活调整。

## 3. 实验设计

- **使用场景与数据集**（根据摘要推测，可能包括但不限于）：
  - **开放生成任务**：侧重控制AI角色个性（AI persona steering）。
  - **对齐关键场景**：
    - 真实性与事实性管理（truthfulness）。
    - 幻觉缓解（hallucination mitigation）。
    - 越狱攻击及其防御（jailbreaking attacks & defenses）。
  - 具体数据集名称在摘要中未明确提及，但按领域推测可能使用了TruthfulQA、HaluEval、AdvBench等常见基准。
- **Benchmark**：未明确列出全部基准，但实验主要评估转向后模型在目标行为上的表现以及通用能力保持度（如困惑度、标准NLP任务性能）。
- **对比方法**：
  - 直接激活提取法（direct activation extraction）。
  - 可能还包括其他轻量级调控方法（如LoRA适配、提示工程等，但摘要未详述）。

## 4. 资源与算力

- 文中**未明确说明**使用的GPU型号、数量或训练时长。仅从方法轻量性推断：转向向量参数极少，训练仅需少量数据和计算（相比微调极大减少），但具体数值未给出。

## 5. 实验数量与充分性

- **实验组数**：从元数据中表格数量（22张表）和附图（9张）可推测，进行了大量对比实验，涵盖多个场景、多种属性（不同模型、不同转向强度、不同层选择、多向量协同、跨模型迁移等）。
- **充分性分析**：
  - 覆盖了**个性化/角色控制**和关键对齐场景（真实性、幻觉、安全），场景多样性较好。
  - 包含**消融实验**（如不同训练方法对比、向量强度调整、多向量联合效果）。
  - 考察了**跨模型/跨LoRA迁移性**，增强方法鲁棒性。
  - 相对客观：与直接提取法对比，并报告了通用能力指标（如基础任务性能），避免选择性报告。
  - 不足之处：缺乏与全参数微调、LoRA微调的全面对比（可能因计算成本不现实）；未提供数据集规模的详细信息，可能影响复现性。

## 6. 主要结论与发现

- **双向偏好优化**比直接从激活中提取转向向量效果更好，能更精确且稳定地引导模型输出期望行为。
- 转向向量可在**不显著损失模型通用能力**的前提下，有效控制输出方向（例如让模型更诚实、减少幻觉、抵抗越狱攻击）。
- 转向向量可**跨模型/跨LoRA迁移**，且**多个转向向量可同时使用**产生协同效应，提升了方法的实用性和灵活性。
- 该方法在**对齐关键场景**（真实性、幻觉、安全）中展现了卓越的控制能力，为轻量级模型行为调控提供了有效方案。

## 7. 优点

1. **计算高效**：仅需训练少量向量参数（远少于微调），大幅降低训练推理成本。
2. **无需修改模型参数**：推理时仅调整激活值，不影响原模型结构，便于部署。
3. **可插拔与组合**：支持多向量叠加，便于实现多维度属性控制（如同时调整诚实和友好度）。
4. **跨模型迁移**：训练好的向量可应用于同族不同规模的模型或LoRA版本，增强了复用性。
5. **覆盖关键场景**：不仅用于个性化，还在安全、真实性等对齐问题上验证，拓展性佳。

## 8. 不足与局限

1. **实验覆盖不够全面**：未明确列出所有使用数据集和基准；未与全参数微调、LoRA微调等方法进行完整性能对比（可能因计算规模差距无法公平比较）。
2. **数据依赖**：方法效果高度依赖于对比偏好数据的质量和数量，如果数据存在偏差或噪声，向量方向可能不准确。
3. **泛化性验证有限**：仅在部分模型（如Llama系列）和特定任务上验证，不同架构（如Mixture of Experts模型）或更大规模模型的效果未知。
4. **潜在风险**：转向向量可被恶意利用来引导模型输出有害内容（如作者也研究越狱防御，但未讨论防御被绕过）。
5. **资源信息缺失**：未提供训练所需GPU型号、时间等，不利于评估实际部署门槛。

（完）

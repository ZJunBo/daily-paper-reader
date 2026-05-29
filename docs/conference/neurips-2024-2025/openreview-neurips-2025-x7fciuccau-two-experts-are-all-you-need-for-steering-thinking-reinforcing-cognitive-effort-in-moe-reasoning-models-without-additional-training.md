---
title: "Two Experts Are All You Need for Steering Thinking: Reinforcing Cognitive Effort in MoE Reasoning Models Without Additional Training"
title_zh: 仅需两个专家即可引导思考：无需额外训练强化MoE推理模型的认知努力
authors: "Mengru Wang, Xingyu Chen, Yue Wang, Zhiwei He, Jiahao Xu, Tian Liang, Qiuzhi Liu, Yunzhi Yao, Wenxuan Wang, Ruotian Ma, Haitao Mi, Ningyu Zhang, Zhaopeng Tu, Xiaolong Li, Dong Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=x7fCiuCCAu"
tags: ["query:dg"]
score: 6.0
evidence: 无需额外训练即对MoE推理模型进行激活引导
tldr: 混合专家推理模型常存在过度思考或思考不足的认知效率问题。本文提出推理时转向方法RICE，利用归一化点互信息识别擅长特定认知过程的专家，并在生成时增强其激活，无需额外训练。在数学推理任务上，该方法显著提升了推理深度和效率。这项工作为MoE模型的行为优化提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-x7fciuccau/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1301, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x7fciuccau/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 724, \"height\": 491, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1096, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1078, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1003, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1278, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1036, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 659, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 741, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 997, \"height\": 598, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1192, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 907, \"height\": 655, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1203, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x7fciuccau/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1030, \"height\": 337, \"label\": \"Table\"}]"
motivation: 现有推理模型存在认知效率低下（过度思考/思考不足），缺乏轻量级干预手段。
method: 通过nPMI识别认知专家，在推理时选择性地增强特定专家的贡献。
result: 该方法在不训练的情况下改善了MoE模型的推理质量和效率。
conclusion: 激活特定认知专家可有效调节模型思考过程。
---

## Abstract
Mixture-of-Experts (MoE) architectures within Large Reasoning Models (LRMs) have achieved impressive reasoning capabilities by selectively activating experts to facilitate structured cognitive processes. Despite notable advances, existing reasoning models often suffer from cognitive inefficiencies like overthinking and underthinking. To address these limitations, we introduce a novel inference-time steering methodology called Reinforcing Cognitive Experts (RICE), designed to improve reasoning depth and efficiency without additional training or complex heuristics. Leveraging normalized Pointwise Mutual Information (nPMI), we systematically identify specialized experts, termed cognitive experts that orchestrate meta-level reasoning operations characterized by tokens like <think>. Empirical evaluations with leading MoE-based LRMs (DeepSeek-R1 and Qwen3-235B) on rigorous quantitative and scientific reasoning benchmarks (AIME and GPQA Diamond) demonstrate noticeable and consistent improvements in reasoning accuracy, cognitive efficiency, and cross-domain generalization. Crucially, our lightweight approach substantially outperforms prevalent reasoning-steering techniques, such as prompt design and decoding constraints, while preserving the model's general instruction-following skills. These results highlight reinforcing cognitive experts as a promising, practical, and interpretable direction to enhance cognitive efficiency within advanced reasoning models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 大型推理模型（LRMs）如 OpenAI o1 和 DeepSeek-R1 通过扩展测试时计算取得了显著进展，但普遍存在**认知效率低下**问题：过度思考（overthinking）和思考不足（underthinking）。
- 已有方法如偏好优化、解码惩罚等，但均需要额外训练或复杂的启发式规则。
- 本文从 **MoE（混合专家）架构**中的专家特化角度出发，假设存在专门负责元推理的“认知专家”（cognitive experts），并探索通过**轻量级推理时操控**这些专家来改善推理深度和效率，无需额外训练。

## 2. 方法论：核心思想、关键技术细节、公式
- **核心思想**：利用**归一化点互信息（nPMI）** 量化专家激活与思考标记（如 `<think>`、`</think>`）之间的共现关系，识别出与推理强相关的 **认知专家**。然后在推理时，通过**放大这些专家的权重**（即乘以一个增强乘数 β）来增强其贡献，从而引导模型进行更深入、更高效的推理。
- **关键步骤**：
  1. **专家识别**：对每个专家 Ei，计算其与思考标记集 Π = {`<think>`, `</think>`} 的 nPMI 综合得分：  
     nPMI_Ei = c_think·nPMI(`<think>`, Ei) + c_/think·nPMI(`</think>`, Ei)，其中 c_think=1, c_/think=-1（优先选择启动而非终止思考的专家）。
  2. **权重调整**：若专家 Ei 在 gating 函数选中的子集 S 中且属于认知专家集 P，则将其权重乘以 β（β > 1 为增强乘数），否则保持不变。
- **无需训练**：仅需一次前向传播获取专家激活统计，即可完成专家识别。

## 3. 实验设计
- **数据集**：
  - **AIME2024 / AIME2025**（数学推理，各30题）
  - **GPQA Diamond**（科学推理，198道专家级选择题，涵盖物理、化学、生物）
  - **辅助数据集**：GSM8K、MATH-500、HLE（各随机采样部分子集）
  - 通用指令跟随能力评估：**ArenaHard**（500题，随机抽取50题）
- **模型**：
  - DeepSeek-R1（671B参数，每层256专家选8）
  - Qwen3-235B（每层128专家选8）
- **对比方法**：
  - 无干预（Vanilla）
  - 提示工程（Prompt before / after `<think>`）
  - 解码约束（TIP t：惩罚 `</think>` 标记）
  - 随机专家增强（Random）
  - 不同专家数量（Top1-5）和乘数β（2-512）的消融

## 4. 资源与算力
- 论文明确说明：**DeepSeek-R1 实验在 16 张 H20 GPU 上使用 vLLM 0.7.0 进行**；Qwen3-235B 实验使用 vLLM 0.8.5+。
- 未报告具体训练时长或总计算量，因为方法本身无需训练，仅需推理时统计专家激活和简单权重调整。

## 5. 实验数量与充分性
- **充分性较高**：
  - 在 4 个主要数据集（AIME24/25, GPQA四领域）上评估，覆盖数学与科学推理。
  - 在通用能力（ArenaHard）上测试副作用。
  - 消融实验：不同专家数量（Top1-5）、不同乘数β（2-512）、随机专家对比、有无重归一化。
  - 跨领域迁移实验：将某一领域识别的专家应用于其他领域。
  - 对比多种基线方法（提示、解码约束）。
  - 提供了 Pass@k 结果（16次采样）。
- **公平性**：超参数（专家数=2，β=64）在AIME24上根据验证选择后固定用于所有测试，避免了过度调参。对比方法使用相同模型和设置。

## 6. 主要结论与发现
- **认知专家确实存在**：在DeepSeek-R1和Qwen3-235B中均识别出少量专家（如前两名）与思考标记高度相关，且跨数学、物理等共享部分专家，表明存在通用推理回路。
- **增强两个顶级认知专家即可显著提升推理准确性和效率**：在AIME24上准确率从73.3%提升至83.3%，同时平均Token数减少（9,219→8,317），思考步数也减少。
- **跨领域泛化好**：数学识别的专家在AIME25上依然有效（63.3%→73.3%），对GPQA物理和化学也有提升，生物学基本持平。
- **不损害通用指令跟随能力**：ArenaHard得分从91%升至92%–94%（不同领域专家），说明认知专家增强是安全的。
- **优于现有轻量级方法**：RICE平均准确率78.7%，优于提示（75.0%）和TIP t（76.7%）。

## 7. 优点
- **无需额外训练**：仅需一次前向传播统计，计算开销极小，可即插即用于现有MoE推理模型。
- **可解释性强**：nPMI度量直观揭示了哪些专家负责启动/终止思考。
- **有效性突出**：仅放大两个专家权重即可获得一致提升，且同时减少Token使用，实现更高效推理。
- **广泛适用性**：在两种不同MoE架构（DeepSeek-R1, Qwen3-235B）和多个领域验证，且跨领域迁移良好。
- **安全性好**：通用能力不受损，甚至小幅提升。

## 8. 不足与局限
- **专家识别仅基于nPMI**：可能未捕捉所有相关交互（如专家间的协同作用），未来可探索更复杂度量。
- **验证模型有限**：仅测试了DeepSeek-R1和Qwen3-235B，缺乏对更多MoE推理模型（如其他开源或商业模型）的验证。
- **β乘数需要手动设定**：虽然采用简单网格搜索，但不同领域可能需不同强度，当前论文仅使用固定配置（β=64, 2专家）。
- **跨领域迁移存在负迁移**：例如生物-识别的专家在化学上反而降低性能，说明领域特异性仍需进一步研究。
- **未提供统计显著性检验或置信区间**：部分结果（如AIME24的83.3%）可能受单次运行波动影响。
- **资源开销报告不完整**：未给出nPMI计算和专家识别所需的确切时间，仅说明是轻量级。

（完）

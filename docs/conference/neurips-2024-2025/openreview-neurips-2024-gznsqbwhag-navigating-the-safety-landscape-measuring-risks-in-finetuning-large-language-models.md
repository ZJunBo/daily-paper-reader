---
title: "Navigating the Safety Landscape: Measuring Risks in Finetuning Large Language Models"
title_zh: 导航安全景观：测量大语言模型微调中的风险
authors: "ShengYun Peng, Pin-Yu Chen, Matthew Daniel Hull, Duen Horng Chau"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=GZnsqBwHAG"
tags: ["query:smd"]
score: 6.0
evidence: 测量微调导致的安全退化风险，并发现安全盆地现象
tldr: 论文通过导航大语言模型的安全景观来测量微调风险，发现参数空间中普遍存在“安全盆地”现象：在局部邻域内随机扰动权重不会降低安全性，但微调会轻易跳出该盆地导致安全性完全丧失。这一发现揭示了微调导致安全退化的内在机制，为设计防御方法提供了理论基础。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1125, \"height\": 796, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 546, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 573, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1197, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 551, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 548, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1210, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1212, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1206, \"height\": 656, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-gznsqbwhag/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1211, \"height\": 752, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-gznsqbwhag/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1329, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gznsqbwhag/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1107, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-gznsqbwhag/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1542, \"height\": 1347, \"label\": \"Table\"}]"
motivation: 安全对齐的模型在微调少量对抗样本后即可被攻破，需要理解微调导致安全退化的根本原因。
method: 通过探索模型参数空间中的安全景观，分析不同参数区域的安全性，发现安全盆地结构。
result: 发现所有开源模型参数空间中都存在安全盆地，局部扰动不降低安全性，但微调会推动参数离开盆地，导致安全完全丧失。
conclusion: 安全盆地的存在为理解微调攻击提供了新视角，并提示防御应致力于将模型参数保持在安全盆地内。
---

## Abstract
Safety alignment is crucial to ensure that large language models (LLMs) behave in ways that align with human preferences and prevent harmful actions during inference. However, recent studies show that the alignment can be easily compromised through finetuning with only a few adversarially designed training examples. We aim to measure the risks in finetuning LLMs through navigating the LLM safety landscape. We discover a new phenomenon observed universally in the model parameter space of popular open-source LLMs, termed as “safety basin”: random perturbations to model weights maintain the safety level of the original aligned model within its local neighborhood. However, outside this local region, safety is fully compromised, exhibiting a sharp, step-like drop. This safety basin contrasts sharply with the LLM capability landscape, where model performance peaks at the origin and gradually declines as random perturbation increases. Our discovery inspires us to propose the new VISAGE safety metric that measures the safety in LLM finetuning by probing its safety landscape. Visualizing the safety landscape of the aligned model enables us to understand how finetuning compromises safety by dragging the model away from the safety basin. The LLM safety landscape also highlights the system prompt’s critical role in protecting a model, and that such protection transfers to its perturbed variants within the safety basin. These observations from our safety landscape research provide new
insights for future work on LLM safety community. Our code is publicly available at https://github.com/ShengYun-Peng/llm-landscape.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：大型语言模型（LLM）的安全对齐（safety alignment）通过人类反馈强化学习、指令微调等方法使模型拒绝有害指令。然而，近期研究表明，仅用少量对抗设计的训练样本进行微调（fine-tuning）就能轻易破坏安全对齐，甚至GPT-3.5 Turbo和LLaMA-2在10个有害样本下就失效。这给模型部署带来严重安全隐患，因为定制化微调是常见需求。
- **核心问题**：为什么简单的微调能轻易破坏安全对齐？不同开源LLM是否同样脆弱？安全何时开始失效？
- **整体含义**：论文通过“安全景观”（safety landscape）的概念探索LLM参数空间中的安全行为，发现了普遍存在的“安全盆地”（safety basin）现象，并据此提出VISAGE安全度量指标，用于测量微调风险。这一发现揭示了微调攻击的内在机制，为设计防御方法提供了理论基础。

## 2. 方法论：核心思想、关键技术细节、公式/算法流程
- **核心思想**：将模型参数视为空间中的点，通过沿随机方向或插值方向扰动权重，评估不同位置的安全性（攻击成功率ASR），从而绘制安全景观。发现安全盆地的存在后，提出VISAGE指标量化盆地深度。
- **关键技术细节**：
  - **1D安全景观**：`f(α) = S(θ + α·cd1)`，其中θ为初始权重，cd1为归一化后的随机方向或插值方向，α为扰动幅度，S为安全度量（ASR）。对cd1进行逐层归一化以消除尺度影响。
  - **2D安全景观**：`f(α,β) = S(θ + α·cd1 + β·cd2)`，两个方向随机或插值，使用Gram-Schmidt正交化保证方向正交。
  - **VISAGE安全度量**：定义为沿随机方向在局部邻域内所有采样点的平均安全边际：`VISAGE = E[ Smax - S(α,β,...) ]`，其中S< Smax（ASR时Smax=100）。沿多个随机方向取均值以保证稳定性（3个方向即可收敛）。
  - **微调轨迹投影**：将每个epoch的模型权重投影到从初始到最终模型权重的插值方向，可视化微调如何将模型拖出安全盆地。
- **公式/算法流程**（文字说明）：首先从高斯分布采样随机方向，经逐层归一化得到扰动方向；然后以步长20在[-a,a]（a=0.5）区间内采样α，计算每个扰动模型的ASR；最后对所有ASR低于100的样本计算平均安全边际即为VISAGE。对于微调轨迹，使用PCA难以处理7B参数，故直接使用初始与最终权重的插值方向。

## 3. 实验设计
- **使用的模型**：LLaMA2-7B/13B-chat、LLaMA3-8B-instruct、Mistral-7B-instruct-v0.1/v0.2、Vicuna-7B-v1.3/v1.5。
- **数据集/场景**：
  - **安全评估**：AdvBench Harmful Behaviors（80子集和520全量）作为主要基准；POSE benchmark（基于Meta和OpenAI的11类禁止使用策略）用于验证泛化。
  - **能力评估**：MMLU中的abstract_algebra、high_school_us_history、us_foreign_policy。
  - **流畅性**：MTBench。
  - **越狱攻击**：JailbreakBench（包含GCG和PAIR生成的对抗性提示）。
- **对比方法**：
  - **系统提示对比**：默认、空提示（Empty）、角色扮演（Roleplay）、LLaMA2系统提示、安全提示（Prompt tuning优化）。评估每种提示下的VISAGE。
  - **微调数据对比**：纯有害样本（10/50/100 shots）、有害+安全混合样本（各100 shots）。
  - **模型大小对比**：LLaMA2-7B vs 13B。
- **安全评估指标**：主要使用ASR（关键词检测），并用LLaMA Guard 2验证一致性。
- **基线**：原始对齐模型（未微调）的VISAGE作为基线。

## 4. 资源与算力
- 文中明确指出：“Finetuning is done on 4 A100 GPUs”。对于全参数微调（full parameter finetuning），未提及具体的训练时长、批次大小等细节。安全景观绘制（perturbation）需要的计算量相对较小（仅推理）。整体实验在NeurIPS 2024标准GPU集群上完成，但未详细列明总GPU耗时。

## 5. 实验数量与充分性
- **实验数量**：论文进行了多组实验：
  - 4种开源LLM的安全景观绘制（1D和2D随机方向）。
  - 微调实验：有害数据10/50/100 shots，混合数据100+100 shots，每种条件保存5个epoch的checkpoint并投影。
  - 系统提示实验：5种提示×6个模型变体（含不同版本），共约30个VISAGE测量。
  - 越狱攻击实验：2个模型×2种提示条件。
  - 能力景观对比：3个MMLU子集。
  - 模型大小对比（7B vs 13B）。
  - 附录中还包括LLaMA Guard 2指标验证、POSE数据集验证、输出流畅性（perplexity）验证。
- **充分性**：实验覆盖了主要开源模型、多种数据规模、多种提示策略，并验证了指标在不同安全度量下的稳定性。消融实验较充分（如随机方向数量对比、不同数据集）。但仅限7B-13B规模的开源模型，未涵盖更大或闭源模型。从研究深度看，实验设计客观、公平，对比了不同模型同类条件下的表现。

## 6. 主要结论与发现
- **安全盆地普遍存在**：所有测试的开源LLM在随机扰动下，局部邻域内安全水平保持稳定，但超出邻域后安全急剧下降（阶跃式跌落）。能力景观则不同，性能随扰动逐渐下降。
- **VISAGE能预测微调风险**：VISAGE越高的模型，微调后越安全。LLaMA3（90.40）> LLaMA2（85.32）> Mistral（82.04）> Vicuna（73.26），与微调后实际的ASR排序一致。
- **微调机制**：微调将模型参数拖离安全盆地（如从盆地中心向外移动），导致安全性丧失。若混合安全数据，微调方向可保持在盆地内，安全性得以保留。
- **系统提示的关键作用**：
  - 移除默认提示或使用角色扮演提示会降低安全性（空提示危害更大）。
  - LLaMA2的系统提示可以跨模型提升安全性（如提升LLaMA3的VISAGE达9.3pp）。
  - 通过提示调优优化的安全提示对特定模型有效，且对盆内扰动模型仍有效。
- **越狱攻击对权重扰动高度敏感**：轻微扰动模型权重即可显著降低越狱攻击成功率，这为简单防御提供可能，但攻击者也可针对多个扰动模型构造更强攻击。

## 7. 优点
- **新颖性**：首次发现“安全盆地”现象，直观揭示了微调破坏安全对齐的内在原因，为理解LLM微调安全性提供了全新视角。
- **度量实用性**：VISAGE指标不需要实际微调，只需沿随机方向扰动推理即可预估微调风险，是任务无关的任务前风险评估工具。
- **可视化方法**：通过1D/2D景观可视化微调轨迹、系统提示效果、越狱敏感度，直观且具有解释性。
- **实验设计全面**：覆盖多种模型、多种提示、多种数据集，验证了现象的普适性；使用了不同安全指标（关键词检测、LLaMA Guard）和不同数据集（AdvBench、POSE）进行交叉验证。
- **开源贡献**：代码公开，便于复现和后续研究。

## 8. 不足与局限
- **模型范围有限**：仅研究7B-13B的开源模型，未验证更大模型（如70B）或闭源模型（如GPT-4）是否也存在安全盆地。
- **VISAGE的稳定性和计算成本**：虽然实验表明3个方向即可收敛，但理论上随机方向的选择可能影响结果；需要较多推理（每方向20步×3方向×每个模型）才能计算，对于超大规模模型成本仍高。
- **未提出直接防御方法**：论文主要提供分析和度量工具，未设计具体的防御算法（如如何引导微调保持在盆地内），仅指出现有混合安全数据的方法有效。
- **安全-能力权衡未深入**：虽然发现能力景观与安全景观不同，但未探索如何在保持安全的同时最大化能力（如找到盆内最优性能点）。
- **越狱攻击部分较初步**：仅验证了已有攻击对扰动的敏感性，未提出防御或更系统性的攻击分析。
- **评估依赖ASR**：ASR采用关键词检测，尽管与GPT-4 Judge表现接近，但仍可能漏报或误报；LLaMA Guard 2验证仅用于泛化测试，未全面替换。

（完）

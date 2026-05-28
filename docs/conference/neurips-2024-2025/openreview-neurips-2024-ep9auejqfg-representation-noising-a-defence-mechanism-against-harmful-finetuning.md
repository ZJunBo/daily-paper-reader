---
title: "Representation Noising: A Defence Mechanism Against Harmful Finetuning"
title_zh: 表示噪声化：一种针对有害微调的防御机制
authors: "Domenic Rosati, Jan Wehner, Kai Williams, Lukasz Bartoszcze, Robie Gonzales, carsten maple, Subhabrata Majumdar, Hassan Sajjad, Frank Rudzicz"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=eP9auEJqFg"
tags: ["query:smd"]
score: 9.0
evidence: 通过移除有害表示来防御有害微调
tldr: 论文针对有害微调攻击（HFA）中恶意用户可通过微调恢复模型有害能力的问题，提出表示噪声化（RepNoise）防御机制。该方法在模型权重中移除有害表示的信息，使得即使在攻击者拥有权重访问权的情况下，微调也难以恢复有害行为。实验证明RepNoise能有效降低有害微调的成功率，且对正常性能影响较小。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1302, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1361, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1011, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1155, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1450, \"height\": 234, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-ep9auejqfg/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 313, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1276, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1035, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1318, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1408, \"height\": 376, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1189, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1052, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1438, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1349, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1376, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1443, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1218, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1184, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1086, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 652, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 413, \"height\": 141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 689, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1255, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1095, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 637, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 683, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1195, \"height\": 711, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-ep9auejqfg/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1079, \"height\": 225, \"label\": \"Table\"}]"
motivation: 开源大语言模型易被恶意用户通过微调用于有害目的，即使闭源模型也面临权重窃取和微调API攻击。
method: 提出表示噪声化（RepNoise），在模型表示层面移除有害信息，使得微调过程中难以恢复有害表征。
result: RepNoise能显著降低有害微调的成功率，同时保持模型在正常任务上的性能。
conclusion: 表示噪声化是一种有效的防御手段，能抵抗攻击者具有权重访问权的有害微调攻击。
---

## Abstract
Releasing open-source large language models (LLMs) presents a dual-use risk since bad actors can easily fine-tune these models for harmful purposes. Even without the open release of weights, weight stealing and fine-tuning APIs make closed models vulnerable to harmful fine-tuning attacks (HFAs). While safety measures like preventing jailbreaks and improving safety guardrails are important, such measures can easily be reversed through fine-tuning. In this work, we propose Representation Noising (\textsf{\small RepNoise}), a defence mechanism that operates even when attackers have access to the weights. \textsf{\small RepNoise} works by removing information about harmful representations such that it is difficult to recover them during fine-tuning. Importantly, our defence is also able to generalize across different subsets of harm that have not been seen during the defence process as long as they are drawn from the same distribution of the attack set. Our method does not degrade the general capability of LLMs and retains the ability to train the model on harmless tasks. We provide empirical evidence that the efficacy of our defence lies in its ``depth'': the degree to which information about harmful representations is removed across {\em all layers} of the LLM. We also find areas where \textsf{\small RepNoise} still remains ineffective and highlight how those limitations can inform future research.

---

## 论文详细总结（自动生成）

# 论文总结：Representation Noising: A Defence Mechanism Against Harmful Finetuning

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：开源大语言模型（LLM）存在双重使用风险——恶意用户可通过微调（Harmful Fine-tuning Attack, HFA）轻易地将模型用于有害目的。即使不开源权重，权重窃取和微调API也使闭源模型面临相同威胁。
- **现有局限**：当前安全措施（如拒绝回答、对抗性防御）在推理时有效，但极易被微调逆转。安全机制往往仅抑制而非移除有害能力，深层有害表征仍可通过微调恢复。
- **目标**：提出一种即使在攻击者拥有模型权重访问权时仍能生效的防御机制，使模型难以被微调用于有害任务，同时保持正常能力。

## 2. 方法论：核心思想、关键技术细节、公式/算法
- **核心思想**：通过减少有害文本序列的中间激活（表征）与有害输出之间的互信息，使得后续微调无法有效恢复有害能力。防御过程在模型发布前完成，之后防御者无法干预攻击者的微调。
- **关键技术细节**：
    - 基于信息瓶颈理论和过渡概率模型，推导出最小化互信息可提升从初始权重到有害目标权重的过渡难度，从而防御HFA。
    - 损失函数由三项构成：  
      \( \mathcal{L}_{\text{RepNoise}} = \ell_{\text{stability}} + \alpha \cdot \ell_{\text{noise}} - \beta \cdot \ell_{\text{ascent}} \)
        - **稳定性损失 (\(\ell_{\text{stability}}\))**：在无害数据上最小化语言建模损失，保持模型能力。
        - **对抗性损失 (\(-\beta \cdot \ell_{\text{ascent}}\))**：在有害数据上执行梯度上升，增大生成有害输出的损失。
        - **噪声损失 (\(\alpha \cdot \ell_{\text{noise}}\))**：使用多核最大均值差异（MMD）近似KL散度，将有害表征推向高斯噪声，消除有害信息。
    - 逐层实施：对每一层（post-MLP pre-residual）的激活分别计算 \(\ell_{\text{ascent}}\) 和 \(\ell_{\text{noise}}\)，并使用语言模型头进行层间损失计算。
    - 使用掩码（mask）区分有害问题与目标答案，避免对共享部分进行噪声化。
- **算法流程**（文字说明）：
    1. 输入预训练LLM、无害样本和有害样本（配对，即相同问题对应安全回答和有害回答）。
    2. 每步训练：采样批次，计算掩码；计算稳定性损失；对每个层，计算有害表征上的语言建模损失（梯度上升项）和MMD噪声损失；加权求和后反向传播更新参数。

## 3. 实验设计
- **数据集与场景**：
    - **有害问答**：BeaverTails有害QA数据集（14种危害类别，约18k配对样本）。
    - **毒性内容生成**：DecodingTrust分出的Real Toxicity Prompts（RTP）毒性子集（351个样本）。
- **基准/评价指标**：
    - 有害性分类器：基于DeBERTa-v3在BeaverTails上训练（F1=0.87），输出有害标签logits作为分数。
    - 毒性评价：Perspective API平均毒性分数。
    - 能力保持：TruthfulQA、MMLU、Hellaswag、ARC-easy、Ethics、CrowS-Pairs。
    - 可训练性：GEM benchmark（ViGGO, E2E NLG, DART, CACAPO, ConvWeather），ROUGE-1。
- **对比方法**：
    - 原始模型、随机初始化、额外安全训练、梯度上升、对抗性损失（仅\(\ell_{\text{stability}} - \beta \ell_{\text{ascent}}\)）、Security Vectors、Vaccine。
- **攻击设置**：监督微调，学习率 \(3\times10^{-5}, 6\times10^{-5}, 8\times10^{-5}\)，样本量1k/10k，1 epoch（BeaverTails）或4 epochs（RTP），Adam优化器，余弦学习率调度。

## 4. 资源与算力
- 论文附录L明确说明：
    - GPU：4×A100（80GB）或4×A40（40GB）节点；偶尔使用1×A100（40GB）Google Colab。
    - 平均防御训练时间（10k样本，4×A40）：约1小时52分钟。
    - 攻击训练时间（10k样本）：约26分钟。
    - 成本估算：约2.80加元（RunPod $0.35/hr）。
    - 峰值显存：防御约26.37 GB/设备，攻击约20.81 GB/设备。
- 未给出全部实验总耗时，但强调了超参数搜索的计算需求。

## 5. 实验数量与充分性
- **实验数量**：丰富且多维。
    - 主要抵抗实验：2个任务 × 3学习率 × 2样本量 × 多个对比方法。
    - 稳定性：7个基准测试。
    - 可训练性：5个GEM数据集，含训练前后ROUGE-1和有害性评估。
    - 泛化性：留出5个危害类别 + 半数据集随机划分实验。
    - 机制分析：权重L2距离、逐层概率、PCA可视化、线性探针实验。
    - 消融实验：噪声项/梯度上升项、掩码/逐层操作、种子敏感性、学习率/epoch/β/样本量影响。
    - 额外安全评估：偏见（ROBBIE）、夸张安全（XSTest）、对抗攻击（HarmBench, GCG等）、良性/身份转移攻击。
    - 多模型验证：llama2-7b/13b-chat、Qwen 0.5B-7B系列。
- **充分性与公平性**：实验设计较为全面，但指出超参数敏感（表19显示不同随机种子导致结果波动），需仔细调参。对比方法包括同类防御（Security Vectors, Vaccine, 梯度上升等），设置基本一致。攻击强度从弱到强覆盖全面，但未涉及强化学习类攻击（如DPO逆向）。总体客观。

## 6. 主要结论与发现
- RepNoise能显著抵抗有害微调：在BeaverTails上，经防御后有害性分数稳定在0.10–0.12，远低于原始模型的0.73–0.74；在毒性生成任务上完全抵抗（分数0.00–0.07）。
- 不降低通用能力：TruthfulQA、MMLU等基准得分与基线几乎相同；保持可训练性：在GEM无害任务上微调后ROUGE-1提升与原模型相当。
- 泛化性：可推广到未见过但同分布的有害子集；但在跨域（BeaverTails→HEX-PHI）时失效，需防御样本与攻击样本同分布。
- 机制深度是关键：早期层冻结会使防御失效；权重变化和探针精度表明RepNoise在所有层均匀移除有害信息，而对比方法（对抗性损失）仅影响最后几层。

## 7. 优点
- **防御场景强**：首个在攻击者拥有权重访问权时仍有效的防御方法，适用于开源模型和权重泄露场景。
- **理论支撑**：基于信息瓶颈和过渡概率的数学推导，连接了互信息最小化与防御目标。
- **实验覆盖面广**：多任务、多模型、多对比方法、多维度评估（能力、可训练性、泛化性、安全性），并有深入机制分析。
- **实用性强**：不降低模型正常能力，且允许无害任务继续训练，满足实际部署需求。

## 8. 不足与局限
- **可被击败**：更高学习率（≥3e-4）、更多数据或多epoch可攻破RepNoise，并非完美防御。
- **超参数敏感**：性能对学习率、β、随机种子等高度敏感，需仔细调参，限制了易用性。
- **需要配对数据**：无法直接使用仅有有害问题的数据集（如HEX-PHI），需额外生成安全回答，数据收集成本高。
- **跨域泛化有限**：仅在分布内有效，对分布偏移（如BeaverTails→HEX-PHI）失效，难以防范攻击者使用完全不同的有害数据集。
- **仅限监督微调**：未评估强化学习（如反向DPO）或激活工程等新型攻击，防御范围有限。
- **可能增强夸张安全**：在XSTest上出现小幅增加安全拒绝率，可能影响正常对话流畅性。

（完）

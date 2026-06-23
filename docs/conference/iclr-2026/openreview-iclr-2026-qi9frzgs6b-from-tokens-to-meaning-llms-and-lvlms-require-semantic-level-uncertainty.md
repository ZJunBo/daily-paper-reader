---
title: "From Tokens to Meaning: LLMs and LVLMs Require Semantic-Level Uncertainty"
title_zh: 从词元到意义：大语言模型与大型视觉语言模型需要语义级不确定性
authors: "Gianni Franchi, Andrei Bursuc, Joseph Hoche, Pavel Izmailov, Gilles Louppe, Angela Yao"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=QI9fRzGs6b"
tags: ["query:luq"]
score: 9.0
evidence: 提倡语义级不确定性以提升大语言模型可靠性
tldr: 本立场论文指出，在开放世界场景下，基于词元的不确定性不足以衡量大语言模型的可信度，并提倡转向语义级不确定性。作者认为词元级置信度在开放任务中可能具有误导性，高概率输出仍可能语义错误或产生幻觉，因此需要将不确定性度量从词元提升至语义层面，以更准确地反映模型的不确定性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-iclr-2026-qi9frzgs6b/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1387, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-iclr-2026-qi9frzgs6b/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1467, \"height\": 646, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-iclr-2026-qi9frzgs6b/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 913, \"height\": 216, \"label\": \"Table\"}]"
motivation: 现有词元级不确定性在开放世界任务中无法可靠反映语义正确性，需要更高级的不确定性度量。
method: 通过分析词元级与语义级不确定性的差异，提出应转向语义级不确定性度量。
result: 指出词元级置信度在开放任务中不可靠，语义级不确定性是更优方向。
conclusion: 提倡在大语言模型中采用语义级不确定性以提升可靠性。
---

## Abstract
This position paper argues LLM and LVLM reliability should go beyond hallucinations and integrate uncertainties.
Furthermore, the commonly used token-level uncertainty is insufficient and semantic-level uncertainty is key. 
Token-based criteria, such as next-token entropy or maximum probability, work well in closed-world tasks where the output space is predefined and bounded. However, foundation models increasingly operate in open-world settings. The space of 
answers is unbounded and queries may involve unseen entities, ambiguous phrasing, or complex reasoning. In such cases, token-level confidences may be misleading;  outputs with  high probability may  
be semantically wrong, irrelevant, or hallucinatory.  

We advocate shifting toward \textbf{semantic-level uncertainty} to capture uncertainty in the meaning of generated outputs. 
By doing so, we can better characterize phenomena such as ambiguity, reasoning failures, and hallucination. We further argue that semantic uncertainty should become the primary lens through which we assess the reliability of foundation models in high-stakes applications, enabling more faithful, trustworthy, and transparent AI systems.

---

## 论文详细总结（自动生成）

# 从词元到意义：大语言模型与大型视觉语言模型需要语义级不确定性

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有大语言模型（LLM）与大型视觉语言模型（LVLM）在开放世界场景下，使用**词元级不确定性**（如下一个词元的熵或最大概率）来评估模型置信度是不充分的。高概率输出仍可能语义错误、无关或产生幻觉，词元级度量无法有效捕捉语义层面的不确定性。
- **背景**：传统深度学习中的不确定性分为 aleatoric（数据固有噪声）和 epistemic（模型知识不足），但将其扩展到 LLM/LVLM 时，由于模型处理多模态输入、生成自由文本，且输出空间在开放世界任务中无边无际，词元级度量已不足以反映真实的不确定性。例如，模型可能以低熵生成“I am not sure but I think it is Zurich.”，但词元级度量却显示高置信度。论文主张转向**语义级不确定性**，以更准确地刻画歧义、推理失败和幻觉等现象。

## 2. 论文提出的方法论：核心思想、关键技术细节与流程

- **核心思想**：将不确定性度量从词元级提升至语义级。语义级不确定性反映生成输出的**意义**层面的不确定性，而非表面词元序列的波动。
- **关键技术细节**：
  - **语义不确定性定义**：定义为模型输出语义概念 $C$ 的不确定性，通过将多个生成结果聚类为等价语义组，然后在组上计算分布 $p(C_k \mid x, \omega)$。
  - **语义熵**：$H_{\text{SE}}(C \mid x, \omega) = - \sum_{k=1}^K p(C_k \mid x) \log p(C_k \mid x)$。该度量在封闭世界分类任务中退化为经典预测熵。
  - **主要分歧**：提出两种语义不确定性来源：
    1. **由提示措辞引起的不确定性**（语义 aleatoric）：模型对同一语义的不同表达敏感，源于随机性和提示脆弱性。
    2. **由任务和模型局限性引起的不确定性**（语义 epistemic）：模型知识不足或推理能力限制导致，如未见实体或复杂推理。
  - **链式思维（CoT）作为不确定性降低机制**：通过形式化分析，证明当添加的相关上下文满足主化（majorization）条件时，语义熵不会增加；CoT 的中间步骤可视为逐步添加上下文，从而降低不确定性。
  - **互信息视角**：还可以通过互信息 $I(C; x_{\text{txt}} \mid x_{\text{img}}, \omega)$ 分解预测不确定性：总不确定性 = 给定固定提示的内在不确定性 + 提示变化引起的不确定性。
- **语义不确定性的估算流程**（来源于附录）：
  1. 多次采样生成多个响应 $ \{y^{(1)}, \ldots, y^{(n)}\} $；
  2. 按含义聚类：使用自然语言推理（NLI）模型（如 DeBERTa）或 GPT-4o 判断双向蕴含，进行硬聚类或软聚类；
  3. 估计每个语义簇的概率：通过概率归一化或频率估计得到 $p(C_k \mid x, \omega)$；
  4. 计算语义熵。

## 3. 实验设计

- **数据集**：TriviaQA（大规模阅读理解数据集，含 650k+ 问答对，来自常识问答和维基百科证据）。实验在 TriviaQA 上进行。
- **评估设置**：每个问题用 Llama-3.1-8B-Instruct 采样 20 次。然后比较三种不确定性度量：
  - 词元级不确定性：采用**困惑度**（perplexity）。
  - 语义熵（基于 DeBERTa 聚类）。
  - 语义熵（基于 GPT-4o 聚类）。
- **评估指标**：
  - **Expected Calibration Error (ECE)**：校准误差，越低越好。
  - **AUROC**：区分正确和错误输出的能力，越高越好。
- **对比结果**（表 1）：
  - 困惑度：ECE 31.50%，AUROC 54.07% —— 校准差，区分能力弱。
  - 语义熵 (DeBERTa)：ECE 22.66%，AUROC 79.16% —— 显著提升。
  - 语义熵 (GPT-4o)：ECE 13.53%，AUROC 80.94% —— 最佳校准但标准偏差约 2%。
- **校准图**（图 2）进一步可视化不同方法的校准质量。

## 4. 资源与算力

- 文中**未明确说明**所使用的 GPU 型号、数量、训练时长或算力开销。仅提及“语义不确定性估计计算昂贵，需要运行大模型（如 GPT-4o）进行聚类”，但未给出具体数值。

## 5. 实验数量与充分性

- **实验数量**：仅在一组数据集（TriviaQA）上进行了一种设置（20 次采样），对比了三种不确定性度量方法。没有其他数据集或任务（如视觉问答、多步推理、多语言等）。无消融实验（如不同采样次数、不同聚类阈值、不同模型规模等）。
- **充分性评估**：实验设计较为简单，作为立场论文（position paper）尚可接受，但作为实证论文则明显不足。**不充分**：仅一个数据集、一种模型（Llama-3.1-8B-Instruct）、一种采样策略，缺乏跨模型、跨任务、跨领域的验证。校准和 AUROC 指标虽然常用，但结果偏向特定设置。实验公平性：对比了困惑度（词元级）和两种语义熵（不同聚类模型），但语义熵需要额外计算资源，对比基准的选择合理但不够广泛。

## 6. 论文的主要结论与发现

- **主要结论**：词元级不确定性（如困惑度）在开放世界任务中校准差、区分能力弱；语义级不确定性（语义熵）显著优于词元级，能够更可靠地反映模型是否生成正确/错误输出。
- **发现**：
  - 基于 GPT-4o 的聚类达到最佳校准（ECE 13.53%），优于 DeBERTa 聚类（ECE 22.66%），但前者具有随机性（标准差约 2%）。
  - 语义不确定性可帮助检测幻觉，而词元级度量往往掩盖幻觉。
  - 链式思维推理可形式化为上下文逐步添加，从而降低语义不确定性。
- **立场**：可靠性评估应从“幻觉”视角转向“不确定性”视角，并采用语义级不确定性作为主要度量。

## 7. 优点

- **概念贡献**：清晰区分词元级与语义级不确定性，并系统列举了 LLM/LVLM 特有的不确定性来源（提示破坏、知识缺口、提示欠指定、推理复杂性、多模态接地错误、解码随机性）。
- **形式化分析**：利用主化理论证明相关上下文的添加会使语义熵不增加，为 CoT 的合理性提供了理论支撑。
- **实验中简单有效**：语义熵方法在 TriviaQA 上显著优于困惑度，验证了核心论点。
- **实践可用性**：提供具体聚类流程（NLI / GPT-4o），易于复现。

## 8. 不足与局限

- **实验范围过窄**：仅在一个数据集（TriviaQA）上进行，且仅使用一种模型（Llama-3.1-8B-Instruct），结果泛化性存疑。未验证视觉语言任务、长文本生成、多步推理等更复杂场景。
- **未对比其他语义不确定性方法**：如 kernel language entropy (Nikitin et al., 2024)、语义密度 (Qiu & Miikkulainen, 2024) 等，未建立 SOTA 比较。
- **缺乏对自身局限性的定量分析**：仅定性列出三点局限（采样次数、聚类不确定性、仅短答案），但未通过实验量化影响。
- **计算成本**：语义熵需要多次采样并调用额外聚类模型（DeBERTa 或 GPT-4o），实际部署成本高，论文未讨论效率或近似方案。
- **校准与 AUROC 的绝对值**：即使最佳 ECE 13.5%，在安全关键应用中仍可能不够；AUROC 80.9% 也并非完美。
- **立场论文性质**：结论偏宣示性，缺乏大规模的消融实验和鲁棒性分析，作为 ICLR 论文实验深度不足。
- **未公开代码/数据**：难以复现实验。

（完）

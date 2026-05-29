---
title: "Who's asking? User personas and the mechanics of latent misalignment"
title_zh: 谁在问？用户角色与潜在对齐失效的机制
authors: "Asma Ghandeharioun, Ann Yuan, Marius Guerard, Emily Reif, Michael A. Lepori, Lucas Dixon"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=eSes1Mic9d"
tags: ["query:dg"]
score: 8.0
evidence: 比较激活引导和提示工程绕过安全过滤器的效果，揭示激活引导的有效性
tldr: 安全对齐的模型仍可能泄露有害信息，且与用户身份相关。本文发现操控用户身份比直接提示更易引发有害输出。比较了自然语言提示和激活引导两种干预方法，激活引导在绕过安全过滤器方面显著更有效。此外，即使生成内容安全，隐藏表示中仍可能残留有害信息，可从早期层解码提取。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 572, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1176, \"height\": 857, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1415, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1170, \"height\": 559, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1172, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 311, \"height\": 228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 310, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 592, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1456, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 281, \"height\": 228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1459, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1223, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 574, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1428, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 732, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1272, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1154, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1267, \"height\": 1322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1371, \"height\": 1323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1402, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-eses1mic9d/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1426, \"height\": 709, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1417, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1356, \"height\": 164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 976, \"height\": 1201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1076, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-eses1mic9d/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 782, \"height\": 571, \"label\": \"Table\"}]"
motivation: 安全对齐模型仍可能根据用户身份泄露有害信息，需理解其机制并寻找更有效的干预方法。
method: 通过自然语言提示和激活引导操控用户角色，对比两者诱导有害输出的效果，并分析隐藏表示。
result: 激活引导比提示更有效，且即使在安全生成中，隐藏表示仍含可提取的有害信息。
conclusion: 激活引导是研究对齐失效的有力工具，揭示了安全过滤的局限性。
---

## Abstract
Studies show that safety-tuned models may nevertheless divulge harmful information. In this work, we show that whether they do so depends significantly on who they are talking to, which we refer to as *user persona*. In fact, we find manipulating user persona to be more effective for eliciting harmful content than certain more direct attempts to control model refusal. We study both natural language prompting and activation steering as intervention methods and show that activation steering is significantly more effective at bypassing safety filters.
We shed light on the mechanics of this phenomenon by showing that even when model generations are safe, harmful content can persist in hidden representations and can be extracted by decoding from earlier layers.  We also show we can predict a persona’s effect on refusal given only the geometry of its steering vector. Finally, we show that certain user personas induce the model to form more charitable interpretations of otherwise dangerous queries.

---

## 论文详细总结（自动生成）

## 论文结构化总结

### 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：安全对齐（safety-tuning）的大语言模型（LLM）仍可能泄露有害信息，且这种泄露行为**显著依赖于用户身份（user persona）**。已有研究表明，模型对用户属性的判断会影响其是否拒绝有害查询，甚至比直接操控模型拒绝行为更有效。
- **整体含义**：揭示了安全对齐模型的“潜在对齐失效”现象——即使输出安全文本，有害内容仍可能存在于隐藏表示中，可通过早期层解码提取。这一发现对模型安全部署提出了警示：安全机制不能仅依赖表层输出，用户的特征（如利他、自私、政治倾向等）会无意中绕过安全过滤器。

### 2. 方法论

- **核心思想**：通过操控模型对用户的判断（用户角色）来改变模型回应有害查询的意愿，并对比自然语言提示（prompt prefix, PP）与激活引导（contrastive activation addition, CAA）两种干预方式的效果。
- **关键技术细节**：
  - **用户角色构建**：定义8种行为角色（如利他/自私、守法/非法、好奇/封闭、权力回避/权力追求）以及性别、政治、宗教等角色。每个角色生成约100条第一人称陈述，再转化为“是/否”问题形式用于CAA训练。
  - **CAA（对比激活加法）**：为每个角色计算“对照差异向量”，即对一组对比输入对（体现该角色行为 vs. 对立行为）取激活差值的平均。推理时，在指定层（如第13层）将向量加到所有位置的隐藏表示上（CAA+）或减去（CAA-）。
  - **提示前缀（PP）**：将角色陈述直接拼接在有害查询前。
  - **早期层解码（Early Decoding）**：通过将早期层的隐藏表示直接用于最终解码，绕过后期层可能存在的安全过滤器。
  - **开放补丁扫描（Patchscopes）**：用于解释隐藏表示的含义，分析角色向量如何改变模型对有害查询的解读（例如更慈善或更恶意的解释）。
- **公式或算法流程**：未给出具体公式，但CAA的核心是 $v_{persona} = \frac{1}{N}\sum (h_{pos} - h_{neg})$，推理时 $h'_l = h_l \pm \alpha v_{persona}$，α为乘数。

### 3. 实验设计

- **数据集**：
  - **AdvBench**（500条有害查询）作为起点。
  - 作者生成了更具挑战性的 **SneakyAdvBench**：通过PaLM text-unicorn@001将AdvBench查询改写得更隐蔽（保留有害意图但不易察觉），从中随机保留100条作为评估集（SneakyAdvBench-eval）。
  - 自动分类出若干攻击类型（歧视、盗窃、阴谋论、网络攻击等），其中约10%为非对抗性查询（作为对照）。
- **基准和对比方法**：
  - **Baseline Prompting**：不加任何干预。
  - **Prompt Prefix (PP)**：在查询前拼接角色陈述。
  - **CAA+ / CAA-**：在选定的最优层（实验发现层13效果最好）施加正/负的引导向量。
  - **直接操控拒绝/服从**：分别构建“拒绝”和“服从”的CAA向量和PP，与角色操控对比。
  - **早期解码**：对上述所有条件，在层l>13进行早期解码。
- **评价指标**：使用自动评分器（text-unicorn@001）判断模型响应是否开始回答或表示愿意回答有害查询。人类标注验证（Krippendorff's α ≈ 0.4），确认自动评分器可作为合理代理。

### 4. 资源与算力

- 论文中明确说明：所有实验在 **A100 80GB 或 40GB GPU** 上运行，每次实验耗时20分钟到6小时不等。自动评分使用Cloud Vertex AI上的 text-unicorn@001 模型。未说明具体GPU数量，但总体计算量较大。

### 5. 实验数量与充分性

- **实验数量**：
  - 主要实验覆盖10种行为/政治/性别角色以及基线“咖啡偏好”角色，共约20余种角色。
  - 每个角色在PP、CAA+、CAA-三种处理下进行测试，并组合早期解码，形成大量条件（图2、图3展示部分）。
  - 同时测试了直接操控拒绝/服从的对比实验。
  - 另在Gemma 7B上进行初步泛化实验（表5）。
- **充分性评估**：实验设计较为系统，覆盖了多种角色、干预手段和攻击类型，并进行了统计显著性检验（paired t-test，表3）。但主要依赖单一模型（Llama 2 13B chat），泛化性有待验证。消融实验（如层选择、乘数影响）较为充分。

### 6. 主要结论与发现

1. **用户角色操控比直接操控拒绝更有效**：CAA引导用户角色（如利他CAA+、自私CAA-）可使响应率提升至52%（图1），而直接操控拒绝/服从仅提升7.7%。
2. **激活引导（CAA）显著优于自然语言提示（PP）**：CAA效果更强且更对称，PP对非对抗性查询也造成广泛拒绝，效果不对称。
3. **安全过滤是局部、层级的**：早期解码（从层>13解码）可恢复有害内容，表明安全机制主要分布在后期层，早期层仍保留有害知识。
4. **引导向量几何可预测效果**：余弦相似性分析显示，与拒绝向量相似度高的角色向量（如自私CAA-）更易增加响应率，且向量几何随层数变化反映Transformer处理阶段。
5. **角色操控改变模型对查询的解释**：通过Patchscopes发现，某些角色（如自私CAA-）使模型将有害查询解读为更无辜或更有动机的慈善行为，从而降低拒绝。

### 7. 优点

- **方法创新**：首次系统比较用户角色操控与直接拒绝操控，并揭示激活引导在绕过安全过滤器上的优势。
- **机理分析深入**：利用早期解码、Patchscopes、几何相似性等方法，从多个角度解释“潜在对齐失效”的机制，不仅展示现象，还提供理解。
- **数据质量**：构建了更具挑战性的SneakyAdvBench数据集，并区分对抗性/非对抗性查询，确保实验可靠性。
- **验证充分**：包含人类标注验证、统计检验、跨模型初步验证（Gemma 7B），结果可信度较高。

### 8. 不足与局限

- **模型单一**：主要实验集中在Llama 2 13B chat，虽有Gemma 7B的初步结果，但泛化性仍需更多模型验证。
- **仅关注有害输出类型**：未覆盖其他限制行为（如幻觉、隐私泄露等），结论可能不适用于所有安全场景。
- **角色定义有限**：仅测试了有限的角色集合，且角色描述由PaLM生成，可能存在模型自身偏见。
- **评估依赖自动评分器**：虽然与人类标注一致性尚可，但自动评分器仍可能出错（Krippendorff's α≈0.38），影响部分结论的精确性。
- **计算成本较高**：需在每层进行引导实验，大规模部署可能不现实。
- **潜在滥用风险**：论文指出激活引导可有效绕过安全过滤器，但这一发现本身可能被恶意使用。作者已讨论更广泛影响，但未提供具体防护措施。

（完）

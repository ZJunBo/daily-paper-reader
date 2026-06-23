---
title: "Not All Inconsistency Is Equal: Decomposing LVLM Uncertainty into Belief Divergence and Belief Conflict"
title_zh: 并非所有不一致都相等：将LVLM不确定性分解为信念分歧与信念冲突
authors: "Jie Shi, Xiaodong Yue, Wei Liu, Yufei Chen, Feifan Dong"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39727/43688"
tags: ["query:luq"]
score: 8.0
evidence: 使用Dempster-Shafer理论分解不确定性，类似于证据语义熵方法
tldr: 现有离散语义熵（DSE）无法区分良性语义歧义与严重信念冲突。本文基于Dempster-Shafer证据理论，将不确定性分解为信念分歧（度量歧义）和信念冲突（度量矛盾）。该方法在LVLM幻觉检测中显著优于DSE，提供了更细粒度的不确定性解释。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有离散语义熵在区分歧义与冲突时失效，导致幻觉检测不可靠。
method: 基于Dempster-Shafer证据理论，将不确定性分解为信念分歧和信念冲突两个互补指标。
result: 在LVLM幻觉检测任务上，方法优于离散语义熵，更准确区分歧义与冲突。
conclusion: 细粒度不确定性分解提升了模型可靠性。
---

## Abstract
Uncertainty Quantification (UQ) is critical for detecting hallucinations in black-box Large Vision-Language Models (LVLMs). However, prevailing methods like Discrete Semantic Entropy (DSE) are unreliable, as their scores are primarily dominated by the number of semantic clusters. This renders them incapable of distinguishing between benign semantic ambiguity (varied but coherent responses) and severe belief conflict (contradictory responses). We address this limitation by proposing a novel framework rooted in Dempster-Shafer theory of evidence, built on the premise that not all inconsistency is equal. Our method decomposes uncertainty into two complementary metrics: Belief Divergence, which quantifies ambiguity by measuring the separation between viewpoints, and Belief Conflict, which captures direct logical contradictions. Extensive experiments demonstrate that our framework provides a more reliable measure of uncertainty.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

当前黑盒大型视觉语言模型（LVLM）的不确定性量化（UQ）多采用离散语义熵（DSE）等方法，其分数主要由语义簇的数量主导，无法区分两种本质不同的不一致性：**良性语义歧义**（多样但连贯的回应）与**严重信念冲突**（自相矛盾的回应）。论文指出“并非所有不一致都相等”，并基于Dempster-Shafer证据理论，提出将不确定性分解为**信念分歧**（度量歧义）和**信念冲突**（度量矛盾）两个互补指标，从而提供更可靠、更细粒度的不确定性度量，增强幻觉检测能力。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：利用Dempster-Shafer理论（DST）显式建模“未知”（ignorance），将每个回答表示为基本信念分配（BBA），在此基础上分别测量簇间的分离度（信念分歧）和簇间的直接矛盾（信念冲突），最终加权得到全局一致性分数。
- **关键技术细节**：
  1. **扰动生成答案集**：对图像（高斯模糊）和文本（LLM生成释义）施加语义保持扰动，得到N个输入对，再以低温度（0.1）让LVLM生成回答集。
  2. **语义结构化建模**：
     - NLI模型进行双向蕴含硬聚类，得到Nc个簇。
     - 使用图注意力网络（GAT）在聚类图基础上精炼嵌入，计算相似度矩阵S。
  3. **信念表示（BBA构建）**：
     - 识别框架Θ = {C1, ..., C_Nc}，焦点集为单点集和全集。
     - 计算每个回答对各簇的支持度（成员相似度平均），进而得到语义亲和分布p_i。
     - 全集（未知）质量m_i(Θ) = 归一化熵；剩余质量按比例分配给各单点集。
  4. **信念分歧（歧义度量）**：
     - 计算每个簇的质心BBA（簇内回答BBA的平均）。
     - 对所有簇对计算Jousselme距离并求和得到原始d，映射为S_div = exp(-d)。
  5. **信念冲突（矛盾度量）**：
     - 计算不同簇间每个回答对的Dempster冲突系数κ（简化形式为不同焦元质量乘积之和）。
     - 逐簇平均后取所有簇对的平均κ，映射为S_con = exp(-κ)。
  6. **最终一致性分数**：S_overall = α·S_div + (1-α)·S_con，默认α=0.5。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - **LLaVA-Bench**（60个挑战性问题，测试常规、细节、复杂推理）
  - **MM-Vet-V2**（218个问题，覆盖6种核心和16种组合能力，如OCR、图表理解）
  - **VQA-RAD**（医学视觉问答，约3500个问题，315张放射图像，测试领域特定能力）
- **评估的LVLM**：13个模型，来自四个家族：
  - Qwen（Qwen2-VL 7B, Qwen2.5-VL 7B/32B/72B）
  - LLaVA（LLaVA-1.5 7B/13B, LLaVA-NeXT 7B/13B）
  - InternVL（InternVL2 8B, InternVL3 8B/9B/14B）
  - DeepSeek（DeepSeek-VL 7B）
- **对比方法（8种）**：
  - 基于词汇相似度：LexSim
  - 基于语义聚类和熵：DSE, NumSet
  - 基于图：SumEigv, Deg, Eccen
  - 其他：LUQ, SNNE-ROUGE
- **评估指标**：AUROC（区分正确/错误回答的能力）、AUARC（拒绝低质量回答的实用效果）
- **公平性设置**：所有方法在相同实验条件下评估（N=10回答，扰动参数相同），均视为黑盒。

## 4. 资源与算力

- 文中明确说明：**所有实验均在单个NVIDIA A100 40GB GPU上进行**。
- 未报告具体训练时长或推理时间，仅提到时间复杂度为O(N²)，与DSE相当。

## 5. 实验数量与充分性

- **主实验**：表1（AUROC）和表2（AUARC）覆盖3个数据集×13个模型×9种方法（包括所提方法），共约117组AUROC+117组AUARC数据。
- **消融实验**：表3对GAT、S_div、S_con三个组件进行6种组合的消融，在所有13个模型上报告AUROC（共13×6=78组）。
- **参数分析**：
  - N（答案数）在{5,10,15}上的影响（图3），涉及4个模型。
  - α（权重）从0到1的连续变化（图4），在MM-Vet-V2上所有13个模型。
- **验证性实验**：专门构造4个案例（图5）分别验证分解的必要性以及两个指标独立测量歧义和冲突的有效性。
- **充分性评价**：实验覆盖面广（多数据集、多模型、多基线），消融完整，参数分析充分，并设计了针对性验证案例，结论客观、公平。唯一不足是未在不同扰动策略（如不同模糊核或释义模型）下验证鲁棒性。

## 6. 主要结论与发现

- 所提框架在大多数配置下达到SOTA，尤其在复杂基准（MM-Vet-V2、VQA-RAD）上优势明显。
- 分解不确定性比单一分数更有效：α=0.5的加权组合优于单独使用信念分歧或信念冲突。
- 两个独立度量分别准确捕获歧义和冲突：在构造的案例中，信念冲突正确将矛盾案例判断为更高不确定性，而基线方法（DSE等）全部分配错误。
- 消融实验表明GAT精炼和两个度量的集成均贡献性能提升。

## 7. 优点（方法与实验亮点）

1. **理论创新**：首次将LVLM不确定性分解为歧义和冲突两种不同形态，基于Dempster-Shafer证据理论提供严格数学框架。
2. **黑盒可用**：仅需模型最终文本输出，无需内部参数，适用于实际API场景。
3. **细粒度可解释性**：两个指标分别指示“观点分散”和“逻辑矛盾”，可辅助用户理解模型失效原因。
4. **实验设计严谨**：覆盖13个模型、3个多样化基准（含医学领域），对比8种基线，消融完整，参数分析有洞察（如α平衡点）。
5. **验证性案例具说服力**：直接驳斥基线方法的缺陷，直观展示分解优越性。

## 8. 不足与局限

1. **外部依赖**：NLI模型和GAT精炼均需额外预训练模型，可能引入领域偏差或错误传播。
2. **计算成本**：虽然复杂度为O(N²)，但需要多次调用NLI（N²次）和一次GAT前向，N较大时成本高；默认N=10并非最优（N=15效果更好）。
3. **简单场景优势不足**：在LLaVA-Bench（相对简单）上，方法并未显著超越全部基线，说明分解在多样性不足时增益有限。
4. **参数敏感性**：α=0.5是经验默认值，不同任务或模型可能需要调参，文中未提供自适应选择策略。
5. **扰动策略局限**：仅使用高斯模糊和LLM释义一种扰动组合，未探索其他扰动（如裁剪、颜色变换、不同温度策略等）的影响。
6. **实验未覆盖**：未在不同语言（如中文）或更多开放域场景下验证泛化性；未讨论模型规模与不确定性分解效果的关系。

（完）

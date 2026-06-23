---
title: "COIN: Uncertainty-Guarding Selective Question Answering for Foundation Models with Provable Risk Guarantees"
title_zh: COIN：具有可证明风险保证的基础模型不确定性守卫选择性问答
authors: "Zhiyuan Wang, Jinhao Duan, Qingni Wang, Xiaofeng Zhu, Tianlong Chen, Xiaoshuang Shi, Kaidi Xu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40667/44628"
tags: ["query:luq"]
score: 7.0
evidence: 基础模型的不确定性守卫选择性问答
tldr: 该论文针对基础模型生成文本中的幻觉问题，提出COIN框架：通过校准统计有效的不确定性阈值，从模型生成中筛选单个答案并提供可证明的风险保证。解决了现有共形预测集包含错误候选的缺陷。实验证明COIN有效控制错误发现率的同时保持高准确率，提升了LLM在关键任务中的可信度。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有不确定性启发式方法缺乏统计保证，共形预测集含错误候选。
method: 校准统计有效的不确定性阈值，筛选单一答案并保证错误发现率。
result: 在多个数据集上实现了可控的错误率和较高准确率。
conclusion: COIN为LLM幻觉缓解提供了具有统计保证的实用方案。
---

## Abstract
Uncertainty quantification (UQ) in foundation models is crucial for identifying and mitigating hallucinations in automatically generated text. 
However, heuristic UQ approaches lack statistical guarantees for key metrics such as the false discovery rate (FDR) in selective prediction tasks. Previous research adopts the split conformal prediction (SCP) framework to ensure desired coverage of admissible answers by constructing data-driven prediction sets, yet these sets typically contain incorrect candidates, undermining their practical effectiveness. To address this, we introduce COIN, an uncertainty-guarding selection framework that calibrates statistically valid uncertainty thresholds to filter a single generated answer per question under user-specified FDR constraints. COIN estimates the empirical error rate on the calibration set and applies confidence interval methods such as Clopper–Pearson to establish a high-probability upper bound on the true error rate (i.e., FDR). This enables the selection of the largest threshold that ensures FDR control on test data while significantly increasing sample retention. We demonstrate COIN's robustness in risk control, strong test-time power in retaining admissible answers, and predictive efficiency under limited calibration data across both general and multimodal text generation tasks. Furthermore, we show that employing alternative UQ and upper bound construction strategies can further boost COIN's power performance, which underscores its extensibility and adaptability to diverse application scenarios.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大型语言模型（LLM）和多模态大模型（LVLM）在问答（QA）任务中容易产生幻觉，生成看似合理但实际错误的信息，影响其在风险敏感领域的可靠部署。现有启发式不确定性量化（UQ）方法在实践中表现良好，但无法对选择性生成场景中的关键指标如错误发现率（FDR）提供统计保证。之前采用分裂共形预测（SCP）框架构建预测集以覆盖合理答案的方法，虽然提供了统计覆盖保证，但预测集常包含错误候选，限制了实际效用。
- **动机**：需要一个能在用户指定FDR约束下，对每个问题筛选单一生成答案的统计有效框架，同时最大化保留正确样本。现有方法如Conformal Alignment (CA)虽能控制FDR，但需遍历整个校准集计算p值，效率低且可能过度拒绝正确样本。
- **整体含义**：COIN框架为LLM/LVLM的可信部署提供了具有可证明风险保证的选择性问答方案，填补了统计严格性与实际效率之间的空白。

## 2. 提出的方法论：核心思想、关键技术细节

### 核心思想
COIN是一个三阶段框架，通过校准集上的经验错误率分析，构建高概率上界，选择最大不确定性阈值，确保测试时FDR受控的同时最大化样本保留。

### 三阶段流程
1. **校准集错误估计**：对每个校准样本，计算模型输出的不确定性分数（如预测熵、语义熵）。针对给定阈值t，保留不确定性≤t的样本，统计保留数m̂_cal(t)和其中失败数ŵ_cal(t)，计算经验条件失败率（ECFR）ˆr_cal(t)=ŵ_cal(t)/m̂_cal(t)。
2. **上界构造**：基于保留子集的二项分布结构，采用Clopper-Pearson精确单侧置信区间或Hoeffding不等式，构造真实条件失败率（TCFR）R(t)的高概率上界ˆR_upper^{1-δ}(t)，满足Pr(R(t)≤ˆR_upper(t))≥1-δ。
   - Clopper-Pearson形式：ˆR_upper(t) = BetaInv(1-δ; ŵ_cal+1, m̂_cal-ŵ_cal)
   - Hoeffding形式：ˆR_upper-H(t) = ˆr_cal(t) + sqrt( log(1/δ) / (2 m̂_cal(t)) )
3. **阈值选择**：利用TCFR关于阈值的非递减性，选择满足对所有t' ≤ t有ˆR_upper(t') ≤ α的最大阈值t̂，保证Pr(R(t̂) ≤ α) ≥ 1-δ。

### 关键技术细节
- 假设数据i.i.d.，且选择指标仅取决于输入X（确定性），因此被选子集服从条件分布，失败指示变量为i.i.d. Bernoulli变量。
- 采用Learn Then Test (LTT)思想避免多重假设校正。
- 模块化设计：各阶段可独立优化（如更换UQ方法、上界构造策略）。

## 3. 实验设计
- **数据集**：
  - 文本QA：Closed-ended CommonsenseQA、Open-domain TriviaQA
  - 多模态：MMVet
- **模型**：
  - LLMs（5个）：包括Qwen-2.5-14B-Instruct、Vicuna-13B-V1.5等，大小从3B到14B
  - LVLMs（5个）：用于多模态任务
- **基准对比方法**：Conformal Alignment (CA)框架
- **UQ方法**：默认使用预测熵（PE，封闭式QA）和语义熵（SE，开放式QA），还测试了Ecc、Deg、Eigv等黑盒方法。
- **正确性指标**：句子相似度（阈值0.7），还考虑了蕴含和LLM判断。
- **评估指标**：
  - 统计有效性：测试集ECFR（即FDR）
  - 效力（Power）：保留的正确答案比例
- **超参数**：束搜索num_beams=5，封闭式生成长度1，开放式32，显著性水平δ=0.05，默认校准-测试分割比0.5。

## 4. 资源与算力
- **明确说明**：论文未明确提及使用的GPU型号、数量或训练时长。所有实验基于预训练模型进行推理和校准，未进行模型训练，因此算力需求相对较低。
- **推断**：模型规模最大为14B参数，可能使用单卡或多卡A100或类似GPU进行推理，但论文未提供具体细节。

## 5. 实验数量与充分性
- **主要实验组**：
  1. 在CommonsenseQA和TriviaQA上，分别对COIN-CP和COIN-HFD在5个LLM上进行测试（各风险水平，100次重复，如图3）。
  2. 效力对比：COIN-CP vs CA，在4个LLM上，多风险水平（图4）。
  3. 敏感性分析：不同校准-测试分割比（1:1、3:7、1:9）下的ECFR（表1）。
  4. 多模态MMVet数据集（附录提供）。
  5. 额外实验：不同UQ方法（黑盒/白盒）、不同正确性标准、不同分割比例（附录）。
- **充分性与公平性**：
  - 实验覆盖了封闭式、开放式、多模态任务，模型规模和类型多样，对比方法为当前最优CA。
  - 100次随机重复减小了随机性影响，统计显著性有保证。
  - 附录补充了大量额外实验，验证了模块化适应性。
  - 公平性：采用与CA相同的评估设定（ECFR和Power），报告了均值和标准差。
  - 总体充分、客观。

## 6. 主要结论与发现
- COIN（CP和HFD两个变体）均能严格将测试ECFR控制在用户指定风险水平α以下，具有统计可靠性。
- COIN-CP的ECFR紧贴α附近，COIN-HFD更保守（更低）。
- 效力上，COIN-CP显著优于CA：例如在CommonsenseQA上使用Qwen-2.5-14B-Instruct，在α=0.15时效力0.85，比CA高0.36；在TriviaQA上高出最多0.4。
- COIN-HFD在某些场景下效力甚至超过COIN-CP（如Vicuna-13B上α=0.25时效力0.92）。
- 即使校准数据有限（1:9分割），COIN仍能维持FDR控制，具有鲁棒性和预测效率。
- 采用更具区分力的UQ方法或更优上界策略可进一步提升COIN效力，体现了模块化的可拓展性。

## 7. 优点
- **统计严格性**：提供了PAC风格的高概率FDR保证，而非仅启发式。
- **高效性**：仅需在一次性校准集上计算阈值，测试时仅比较不确定性与阈值，比CA遍历整个校准集高效。
- **模块化与灵活性**：三阶段可独立替换（UQ方法、上界构造策略），易于适应不同应用场景和计算预算。
- **鲁棒性**：在少量校准数据、黑盒UQ、不同正确性标准下均表现稳健。
- **广泛适用性**：覆盖文本和多模态QA任务，支持多种输出格式（封闭式、开放式）。
- **明确开源代码**：提供GitHub仓库，可复现。

## 8. 不足与局限
- **i.i.d.假设**：框架基于校准集与测试集来自同一分布且i.i.d.的假设，在分布漂移（OOD）场景下可能不成立，论文未讨论。
- **资源细节缺失**：未披露GPU型号、数量、推理时间等，不利于复现和效率对比。
- **对比方法单一**：仅与CA对比，未与其他选择性预测方法（如直接阈值法、风险控制选择法）对比。
- **正确性指标简化**：开放域中使用句子相似度（阈值0.7），可能对语义等价性判断不完美，虽然附加了蕴含和LLM判断，但仅作辅助。
- **计算开销**：Clopper-Pearson方法需要二分查找，当校准规模极大时可能耗时，Hoeffding方法虽快速但更保守。
- **未考虑多步推理生成**：在长文本、链式推理场景下的有效性和效率未验证。

（完）

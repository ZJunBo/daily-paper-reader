---
title: "COM-BOM: Bayesian Exemplar Search for Efficiently Exploring the Accuracy-Calibration Pareto Frontier"
title_zh: COM-BOM：高效探索准确度-校准帕累托前沿的贝叶斯示例搜索
authors: "Gaoxiang Luo, Aryan Deshwal"
date: 2025-11-01
pdf: "https://aclanthology.org/2025.emnlp-main.1027.pdf"
tags: ["query:uq-safety"]
score: 6.0
evidence: 用于准确度和校准的示例选择，属于不确定性量化范畴
tldr: 上下文学习中的示例选择通常只优化预测准确度，忽略模型校准。本文将示例选择建模为同时最大化准确度和最小化校准误差的多目标优化问题，并提出组合贝叶斯优化算法COM-BOM来探索帕累托前沿。实验表明COM-BOM能在保持高准确度的同时显著改善校准，提升了模型的可靠性与安全部署潜力。
source: EMNLP-2025-Main
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 803, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 794, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 798, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1615, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1615, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 766, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 761, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 774, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/emnlp-2025-main/anthology-2025.emnlp-main.1027/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1622, \"height\": 1279, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1464, \"height\": 681, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1624, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 834, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1620, \"height\": 680, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1231, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/emnlp-2025-main/anthology-2025.emnlp-main.1027/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1464, \"height\": 681, \"label\": \"Table\"}]"
motivation: 现有示例选择忽略校准，影响模型可信度。
method: 将示例选择转化为多目标优化，使用组合贝叶斯优化搜索帕累托最优集。
result: 在多个任务上实现准确度和校准的最佳权衡。
conclusion: 为上下文学习提供可信赖的示例选择方法。
---

## Abstract
Selecting an optimal set of exemplars is critical for good performance of in-context learning. However, prior exemplar search methods narrowly optimize for predictive accuracy, critically neglecting model calibration—a key determinant of trustworthiness and safe deployment. In this paper, we formulate exemplar selection as a multi-objective optimization problem, explicitly targeting both the maximization of predictive accuracy and the minimization of expected calibration error. We solve this problem with a sample-efficient Combinatorial Bayesian Optimization algorithm (COM-BOM) to find the Pareto-front that optimally trade-offs the two objectives of accuracy and calibration. We evaluate COM-BOM on multiple tasks from un-saturated MMLU-pro benchmark and find that COM-BOM beats or matches the baselines in jointly optimizing the two objectives, while requiring a minimal number of LLM API calls.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：上下文学习（ICL）中，示例选择（exemplar selection）对性能至关重要，但现有方法**仅优化预测准确度**，完全忽略模型校准（calibration），即模型置信度与真实正确率之间的匹配程度。  
- **问题**：在高风险应用（如医疗、金融、法律）中，模型不仅需要高准确度，还需要**可靠的置信度估计**。欠校准的模型可能过度自信于错误预测或对正确预测缺乏信心，降低实用价值。  
- **贡献**：首次将示例选择重新定义为**多目标优化问题**，同时最大化预测准确度（f_acc）和最小化期望校准误差（f_ECE），并设计**样本高效的组合贝叶斯优化算法（COM-BOM）** 来探索准确度-校准的帕累托前沿。

## 2. 方法论

### 核心思想
将示例选择视为黑盒、昂贵、含噪声的**组合多目标优化问题**，利用贝叶斯优化框架，通过代理模型和采集函数智能引导搜索，以最少LLM API调用找到帕累托最优解。

### 关键技术细节
1. **问题形式化**  
   - 搜索空间：二进制向量 \( z \in \{0,1\}^m \)，其中 \( m \) 为候选示例池大小，\( z_i = 1 \) 表示选择第 \( i \) 个示例。  
   - 目标：\( \max_{z} (f_{acc}(z), -f_{ECE}(z)) \)。

2. **评估方法**  
   - 对每个示例集 \( z \)，在验证集 \( D_{val} \) 上：  
     - 生成 \( M \) 个输出样本，通过语义聚类得到预测答案和置信度（最大簇比例）。  
     - 计算准确度 \( f_{acc}(z) = \frac{1}{|D_{val}|}\sum acc(x,z) \)。  
     - 计算期望校准误差 \( f_{ECE}(z) = \sum_{k=1}^K \frac{|B_k|}{|D_{val}|} |acc_{B_k} - conf_{B_k}| \)，其中 \( B_k \) 为置信度落在第 \( k \) 个区间的样本。

3. **COM-BOM 算法流程**  
   - **初始**：随机采样 \( t_0 \) 个示例集，评估并获得初始数据 \( D_{t_0} \) 和帕累托前沿 \( P_{t_0} \)。  
   - **循环**（从 \( n = t_0 \) 到 \( t_{max} \)）：  
     1. 为每个目标（准确度、ECE）训练独立的**高斯过程（GP）代理模型**，核函数为**指数化汉明距离核**（含自动相关性确定长度尺度 \( \ell_j \)）。  
     2. 优化多目标采集函数（**Noisy Expected Hypervolume Improvement, NEHVI**），计算在候选点 \( z \) 上评估后期望的帕累托前沿超体积增量。  
     3. 通过**贪心爬山算法**在信任区域（汉明球）内最大化采集函数，得到下一个评估点 \( z_{n+1} \)。  
     4. 在 \( z_{n+1} \) 上调用LLM获取准确度和ECE，更新数据集和帕累托前沿。  
   - **输出**：近似帕累托前沿及对应的示例集。

4. **关键创新**：  
   - 直接使用超体积指标（而非标量化）同时优化两个目标。  
   - 利用噪声感知的NEHVI处理评估噪声。  
   - 通过信任区域局部搜索提高组合空间优化效率。

## 3. 实验设计

- **数据集**：MMLU-Pro（13个领域：生物、商业、化学、计算机科学、经济学、工程、健康、历史、法律、数学、哲学、物理、心理学），选择**未饱和任务**以确保评估有意义。  
- **模型**：Qwen3-8B（主要实验）、LLaMA-3.3-70B（泛化验证）。  
- **基准方法**：  
  - **优化无关**：无示例、全部示例、Nearest检索（k=5/10/20）、Diversity检索（k-means聚类）。  
  - **优化方法**：随机搜索（RS）、遗传算法（GA）、模拟退火（SA）、爬山（HC）——均使用标量化。  
  - **消融**：单目标优化（仅Acc/仅ECE）、标量化、是否使用噪声处理/信任区域。  
- **评估指标**：测试集上的预测准确度（Acc）和期望校准误差（ECE），以及验证集上的超体积（HV）。  
- **超参数**：32个候选示例，评估预算200次迭代，初始点20，温度0.7，采样16个，重复3个随机种子。

## 4. 资源与算力

- **Qwen3-8B实验**：使用**2× NVIDIA A100-SXM4-40GB**，总运行时间约**126 GPU小时**。  
- **LLaMA-3.3-70B实验**：未明确说明算力，推测使用相似或更大规模GPU（如A100 80GB）。  
- 论文未报告具体能耗或成本，但强调方法**样本高效**，减少LLM API调用次数。

## 5. 实验数量与充分性

- **数量**：在13个领域上均进行了对比，每个优化方法重复3次随机种子；对比了6种优化无关方法和5种优化方法，外加消融实验。  
- **充分性**：  
  - 覆盖不同领域（STEM、人文、社会科学），模型规模差异（8B vs 70B）。  
  - 多角度消融：单目标 vs 多目标、是否噪声处理/信任区域、不同检索k值。  
  - 实验设计客观公平：离线搜索方法只使用验证集，测试集完全隔离。  
- **结论**：实验较为全面，结论可信。

## 6. 主要结论与发现

1. COM-BOM在**大多数任务上实现了最佳准确度-校准权衡**，尤其在ECE上显著优于所有基准（例如Qwen3-8B平均ECE 25.24% vs 全部示例28.06%）。  
2. 离线搜索方法（COM-BOM）**优于在线检索方法**（Nearest/Diversity），且推理时成本更低。  
3. 多目标优化公式**优于单目标或标量化**：仅优化准确度会牺牲校准，仅优化ECE会损失准确度，标量化次优。  
4. 使用**噪声处理和信任区域**对提升帕累托前沿质量至关重要。  
5. COM-BOM在**更少LLM调用**下（样本效率）达到更好或相当的帕累托前沿。

## 7. 优点

1. **问题定义新颖**：首次将校准纳入示例选择目标，提升LLM部署可靠性。  
2. **方法成熟有效**：利用贝叶斯优化处理黑盒、昂贵、多目标问题，采样高效。  
3. **技术细节扎实**：  
   - 基于语义一致性的置信度与ECE估计，与准确度评估共享LLM样本，无额外成本。  
   - 组合GP核（指数化汉明距离）适合二进制搜索空间。  
   - NEHVI适应噪声评估，信任区域加速组合优化。  
4. **实验充分**：跨模型、跨任务、多基线、消融实验完备，结论可靠。  
5. **实用价值**：离线搜索后部署，推理时零额外成本，适合实际应用。

## 8. 不足与局限

1. **搜索空间限制**：仅考虑32个候选示例池，规模增大时GP可扩展性面临挑战（高维组合爆炸）。  
2. **模型规模局限**：实验限于<100B参数模型（Qwen3-8B、LLaMA-3.3-70B），未验证更大模型（如500B+）。  
3. **任务类型单一**：仅评估英文选择题（MMLU-Pro），未扩展到开放生成任务（如代码生成、长文本回答），可能需更复杂的准确度/置信度度量。  
4. **忽略顺序**：未考虑示例在提示中的排列顺序（排列空间优化），可能影响性能。  
5. **伦理风险**：方法可被恶意用于搜索最大化攻击成功率且校准误差最小的对抗示例（如越狱）。  
6. **计算成本**：虽然样本高效，但GP拟合和采集函数优化仍需要计算资源；初始随机采样20个点也需要LLM调用。  
7. **未公开代码/超参数敏感性**：论文未提供代码库，部分细节（如信任区域半径）未深入讨论。

（完）

---
title: "Learning to Steer: Input-dependent Steering for Multimodal LLMs"
title_zh: 学习引导：多模态大语言模型的输入依赖引导
authors: "Jayneel Parekh, Pegah KHAYATAN, Mustafa Shukor, Arnaud Dapogny, Alasdair Newson, Matthieu Cord"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QSLlPljXxz"
tags: ["query:dg"]
score: 8.0
evidence: 面向多模态大语言模型的输入依赖激活引导
tldr: 该论文针对多模态大语言模型的引导控制问题，提出输入依赖的细粒度引导方法。现有均值引导使用单一向量，无法适应不同输入所需的不同行为（如拒绝非法活动或建议医疗咨询）。本文通过计算输入特定的线性偏移，结合概念器理论，实现基于上下文的自适应引导。实验证明该方法在安全相关行为控制上优于传统均值引导。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 732, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1431, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1416, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1364, \"height\": 2053, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1438, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1291, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 428, \"height\": 637, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 703, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1255, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1457, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1450, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 804, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1426, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qsllpljxxz/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 630, \"height\": 453, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qsllpljxxz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 631, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qsllpljxxz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1342, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qsllpljxxz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1488, \"height\": 761, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qsllpljxxz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1090, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qsllpljxxz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1375, \"height\": 183, \"label\": \"Table\"}]"
motivation: 现有均值引导策略无法根据查询内容动态调整，导致安全行为不适当。
method: 利用概念器和线性模型，为每个输入计算特定的引导向量，实现输入依赖的激活引导。
result: 输入依赖引导在拒绝和提供咨询等安全相关场景中表现优于均值引导。
conclusion: 输入依赖引导为多模态LLM提供了更灵活且上下文相关的行为控制方法。
---

## Abstract
Steering has emerged as a practical approach to enable post-hoc guidance of LLMs towards enforcing a specific behavior. 
However, it remains largely underexplored for multimodal LLMs (MLLMs); furthermore, existing steering techniques, such as \textit{mean} steering, rely on a single steering vector, applied independently of the input query. This paradigm faces limitations when the desired behavior is dependent on the example at hand. For example, a safe answer may consist in abstaining from answering when asked for an illegal activity, or may point to external resources or consultation with an expert when asked about medical advice. In this paper, we investigate a fine-grained steering that uses an input-specific linear shift. This shift is computed using contrastive input-specific prompting. However, the input-specific prompts required for this approach are not known at test time. Therefore, we propose to train a small auxiliary module to predict the input-specific steering vector. Our approach, dubbed as L2S (Learn-to-Steer), demonstrates that it reduces hallucinations and enforces safety in MLLMs, outperforming other static baselines. We will open-source our code.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：多模态大语言模型（MLLMs）在安全性和可靠性方面仍存在不足，如幻觉（生成不基于输入的内容）和安全问题（提供有害或非法回复）。现有引导方法（如均值引导 Mean Steering）使用一个固定的、与输入无关的线性向量来调整模型输出，但这种方法在期望行为依赖于具体输入时效果有限。例如，对于非法活动的查询，安全响应应直接拒绝；而对于医疗咨询，安全响应应建议咨询专家，而非一概拒绝。
- **整体含义**：论文提出一种**输入依赖的细粒度引导**方法，使引导向量根据每个输入查询动态调整，从而更灵活地实现多样化行为控制，提升 MLLM 的安全性和可靠性。

## 2. 方法论

### 核心思想
- 使用**对比提示（Contrastive Prompting）** 生成每个输入样本特定的引导向量（称为 Prompt-to-Steer，P2S），但该向量在测试时未知（需要知道理想/不理想的行为提示）。因此，训练一个轻量级辅助网络（称为 Learn-to-Steer，L2S），从输入上下文的隐藏表示中预测该引导向量。

### 关键技术细节
1. **P2S（Prompt-to-Steer，训练免费但不可实践）**：
   - 对每个输入 \(X=(I,T)\)，构造正负对比提示 \(T_X^+\) 和 \(T_X^-\)（例如：安全场景下，正提示引导模型输出“有害”，负提示引导输出“安全”）。
   - 在教师强制模式下分别前向计算 \(X^+\) 和 \(X^-\)，提取指定层 \(L^*\) 的最后一个 token 的隐藏表示 \(h_{q^+}^{L^*}\) 和 \(h_{q^-}^{L^*}\)。
   - 引导向量定义为两者之差： \(z_{X,L^*} = h_{q^+}^{L^*} - h_{q^-}^{L^*}\)。
   - 推理时，将该向量以幅度 \(\alpha\) 加到所有生成 token 的同一层隐藏表示上： \(h_p^{L^*} \leftarrow h_p^{L^*} + \alpha z_{X,L^*}\)。

2. **L2S（Learn-to-Steer，训练小型网络预测引导向量）**：
   - 训练阶段：对每个样本，提取输入上下文（原始查询的最后一个 token 在层 \(L'\) 的表示 \(h_{X,L'}\)），以及 P2S 引导向量 \(z_{X,L^*}\)。训练一个 2 层 MLP（隐藏层 100 维）以 L2 损失学习映射： \(\Theta^* = \arg\min_\Theta \mathbb{E}_X[\|z_{X,L^*} - g_\Theta(h_{X,L'})\|_2^2]\)。
   - 推理阶段：使用训练好的 \(g_{\Theta^*}\) 预测引导向量，并应用线性偏移： \(h_p^{L^*} \leftarrow h_p^{L^*} + \alpha g_{\Theta^*}(h_{X,L'})\)。

### 公式与算法流程（文字描述）
- 输入：图像 \(I\) 和文本 \(T\)。
- 提取上下文表示：通过 MLLM 前向传播，在层 \(L'\) 获取最后一个 token 的隐藏状态。
- 预测引导向量：MLP 将该上下文映射为引导向量。
- 推理：在层 \(L^*\) 对所有生成 token 的隐藏状态加上该向量（乘以超参数 \(\alpha\)）。

## 3. 实验设计

### 使用数据集 / 场景
- **安全任务**：MMSafetyBench（1531 个多模态查询，涵盖 12 个场景：9 个非法/有害活动 + 3 个敏感咨询如法律、金融、健康）。还使用了 VLGuard 数据集进行选择性引导验证。
- **幻觉缓解任务**：POPE 数据集（9000 个图像-问答对，分为随机、流行、对抗三个子集）；COCO 验证集（500 张图像用于 caption 评估）。

### Benchmark 与对比方法
- 对比方法：No-steering（原始模型）、Prompt（附加安全提示）、Norm-Rnd（随机噪声引导）、Mean-S（均值引导，即对所有训练样本的 P2S 向量求平均）、Mean-S(BA)（行为无关的均值引导，仅使用一组固定对比提示）、P2S（oracle，不可实践）。
- 评估指标：
  - 安全：Unsafe-score（基于 Llama-Guard-3-8B 评估有害概率）、Expert-Deferring score（检测是否提及咨询专家）、Response quality（Gemini-2.0-Flash 评分）。
  - 幻觉：Accuracy、F1、CHAIRs/CHAIRi（caption 级）、Gemini Win-rate（偏好比较）。

## 4. 资源与算力

- 论文明确说明：所有实验在**单张 RTX5000（24GB）GPU** 上完成。
- 训练辅助网络 gΘ 非常轻量：安全任务仅需 10–20 秒，幻觉任务约 1 分钟。主要显存消耗来自加载 MLLM 模型（如 LLaVA-v1.5-7B 或 Qwen2-VL-7B）及前向传播，辅助网络本身占用极小。
- 未提及训练 MLLM 大模型所需的算力（因为方法无需微调大模型）。

## 5. 实验数量与充分性

- **实验组数**：
  - 安全任务：在 LLaVA-v1.5 和 Qwen2-VL 两个模型上分别测试，对比 6 种方法，报告多个指标（Unsafe-score 在不同阈值、ED-score、质量评分）。
  - 幻觉任务：同样在两个模型上测试 POPE 的 Accuracy/F1，并在 COCO 上做 caption 评估（CHAIR 和 Gemini Win-rate）。
  - 消融实验：包括引导层选择（L*）、幅度α、上下文提取层（L'）的消融。
  - 附加实验：VLGuard 上验证选择性引导；P2S 向量分析（t-SNE 可视化、同类/异类相似度）。
  - 统计显著性检验：报告了 p 值（表 5）。
- **充分性**：实验覆盖两个主流 MLLM 系列，多个标准数据集，评估指标全面，且有消融和统计分析。但未在更大规模模型（如 13B/70B）或更多样化的场景（如多步推理）上测试，可能有一定偏差风险。

## 6. 主要结论与发现

- **输入依赖引导显著优于静态引导**：L2S 在安全任务上 Unsafe-score 大幅低于 Mean-S（例如 LLaVA 上 Ep≥0.5 从 0.161 降至 0.082），同时 ED-score 更高（0.395 vs 0.329）；在幻觉任务上 POPE Accuracy 和 F1 均有提升。
- **P2S oracle 表现最好，L2S 接近 P2S**：说明 L2S 能够有效学习预测引导向量。
- **L2S 保持响应质量**：在安全任务中，L2S 的响应质量与无引导模型相当（约 6.56 vs 6.92），且远好于随机噪声引导。
- **L2S 能实现选择性引导**：在 VLGuard 实验中，对有害查询有效引导，对安全查询保留原始响应（87.4% 完全相同，而 Mean-S 仅 5.2%）。
- **引导向量的分析**：同一行为类型的 P2S 向量相似度高，不同行为类型差异大，且即使是同一对比提示，向量仍部分编码场景信息，这支持了输入依赖建模的必要性。

## 7. 优点

- **轻量与高效**：无需微调大模型，仅需训练一个 2 层 MLP（约 0.8M 参数），训练时间极短，推理时仅增加一次前向。
- **细粒度与上下文感知**：首次实现 MLLM 的输入依赖引导，能针对不同查询自适应调整行为（如拒绝 vs 推荐专家）。
- **多任务验证**：在安全和幻觉两个重要问题上的有效性验证，且跨模型（LLaVA、Qwen2-VL）表现一致。
- **丰富的分析和消融**：提供了层选择、幅度、向量结构等深入分析，增强可解释性。

## 8. 不足与局限

- **对比提示的选择非最优**：虽然 P2S 快速可用，但最优的正负对比提示可能难以确定，存在改进空间。
- **单层线性干预**：仅对残差流的一个层做线性偏移，更复杂的干预（多层、非线性）可能进一步提升效果，但会增加计算开销。
- **潜在恶意使用风险**：引导技术可被逆向用于生成有害内容，论文虽提及组织内部防护，但未提出具体防御机制。
- **实验覆盖有限**：仅测试 7B 参数级别模型，未在更大模型（如 13B、70B）或其他架构（如 Flamingo）上验证；在更多样化的安全场景（如偏见、越狱）上未评估。
- **某些失败案例**：附录显示仍存在部分样本引导效果不足（如仍提及有害步骤）或生成内容与查询无关。
- **对训练数据的依赖**：L2S 需要每个样本的 P2S 标签（即正负对比提示），在缺乏此类标注的现实场景下可能难以直接应用。

（完）

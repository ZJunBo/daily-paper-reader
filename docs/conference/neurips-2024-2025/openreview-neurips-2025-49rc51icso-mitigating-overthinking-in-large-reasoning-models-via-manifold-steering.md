---
title: Mitigating Overthinking in Large Reasoning Models via Manifold Steering
title_zh: 通过流形引导缓解大型推理模型中的过度思考
authors: "Yao Huang, Huanran Chen, Shouwei Ruan, Yichi Zhang, Xingxing Wei, Yinpeng Dong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=49Rc51iCso"
tags: ["query:dg"]
score: 7.0
evidence: 使用激活引导来缓解推理模型中的过度思考
tldr: 大型推理模型在推理过程中常出现过度思考现象，导致计算开销增大。本文从机械可解释性角度发现，过度思考的倾向可由激活空间中的单一方向捕捉。通过沿该方向干预激活（即激活引导），可以缓解过度思考。但该方法的效果很快达到瓶颈，提示需要更复杂的干预策略。本文为推理模型的行为控制提供了基于激活引导的新视角。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 429, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1463, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 483, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 429, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-49rc51icso/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 283, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 527, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1444, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1443, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49rc51icso/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 886, \"height\": 147, \"label\": \"Table\"}]"
motivation: 大型推理模型在推理时存在过度思考问题，造成计算浪费，需要理解其机制并寻找缓解方法。
method: 利用机械可解释性定位与过度思考相关的激活方向，通过沿该方向进行激活干预来抑制冗余思考。
result: 实验表明单方向干预可有效缓解过度思考，但效果有限，需更精细的多层或组合干预。
conclusion: 激活引导是控制推理模型行为的有力工具，但需进一步改进以实现更稳健的性能。
---

## Abstract
Recent advances in Large Reasoning Models (LRMs) have demonstrated remarkable capabilities in solving complex tasks such as mathematics and coding. However, these models frequently exhibit a phenomenon known as *overthinking* during inference, characterized by excessive validation loops and redundant deliberation, leading to substantial computational overheads. In this paper, we aim to mitigate overthinking by investigating the underlying mechanisms from the perspective of mechanistic interpretability. We first showcase that the tendency of overthinking can be effectively captured by a single direction in the model's activation space and the issue can be eased by intervening the activations along this direction. However, this efficacy soon reaches a plateau and even deteriorates as the intervention strength increases. We therefore systematically explore the activation space and find that the overthinking phenomenon is actually tied to a low-dimensional manifold, which indicates that the limited effect stems from the noises introduced by the high-dimensional steering direction. Based on this insight, we propose **Manifold Steering**, a novel approach that elegantly projects the steering direction onto the low-dimensional activation manifold given the theoretical approximation of the interference noise. Extensive experiments on DeepSeek-R1 distilled models validate that our method reduces output tokens by up to 71\% while maintaining and even improving the accuracy on several mathematical benchmarks. Our method also exhibits robust cross-domain transferability, delivering consistent token reduction performance in code generation and knowledge-based QA tasks. Code is available at: https://github.com/Aries-iai/Manifold_Steering.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型推理模型（LRMs，如 OpenAI o-series、DeepSeek-R1 系列）在推理过程中存在严重的**过度思考（overthinking）** 现象。模型会生成过多、不必要的推理步骤（如重复验证、冗余讨论），即使对于简单问题也是如此。这不仅大幅增加了推理延迟和计算开销，还可能因陷入重复验证循环而降低回答质量。
- **研究动机**：现有缓解方法多从外部行为视角入手（如外部监控、辅助模型干预），这些方法要么引入额外计算开销，要么依赖外部模型性能，未能从根本上理解并消除过度思考的内部机制。本文旨在**从机械可解释性（mechanistic interpretability）角度**，深入分析过度思考在模型激活空间中的表现形式，并设计内在的干预方法。
- **整体含义**：本文发现过度思考的倾向可以被激活空间中的一个单一方向有效表征，并且通过沿该方向进行激活干预（activation steering）可以部分缓解过度思考。但直接干预在高维空间中存在噪声干扰，导致效果有限。进一步发现过度思考与一个**低维流形（low-dimensional manifold）** 相关，通过将干预方向投影到该流形上，可以消除噪声，实现更好的缓解效果。

## 2. 论文提出的方法论

### 2.1 核心思想

- 利用**差异均值法（difference-in-means）**，从冗余推理（过度思考）和简洁推理的样本对比中，提取出表征过度思考的**单一方向向量** \( \mathbf{r}^{(l)} \)。
- 直接沿该方向减去激活成分（式 3）可缓解过度思考，但高维空间中存在**干扰噪声（interference noise）**，导致随着干预强度增加，效果先提升后反弹甚至恶化（Token 数在 α=1.5 后回升）。
- 观察到模型的激活分布集中在一个**低维线性流形**上（通过 PCA 验证前 10 个主成分解释超过 70% 方差）。过度思考方向也应位于该流形上，而高维计算引入的噪声分量则位于流形的正交补空间 \(\mathcal{M}^\perp\) 中。
- 提出 **Manifold Steering**：将原始的干预方向投影到该低维流形上，消除噪声分量的影响，从而实现更纯净、更有效的干预。

### 2.2 关键技术细节

- **提取方向**：对每个模型，从 OpenMathInstruct-2 训练集随机采样问题，生成 5 个回答，根据 Token 长度（>16k 或 <1k）和犹豫关键词（“wait”、“alternatively” 等）筛选出冗余集 \(D_{\text{redundant}}\) 和简洁集 \(D_{\text{concise}}\)。对最后 token 的残差流激活求差，得到方向 \( \mathbf{r}^{(l)} \)。
- **低维流形获取**：对所有样本的激活矩阵进行 PCA，取前 k 个主成分（k=10）构成投影矩阵 \(P_{\mathcal{M}}\)。
- **流形方向**：\(\mathbf{r}_{\text{overthinking}} = P_{\mathcal{M}} \mathbf{r}^{(l)}\)，之后归一化。
- **干预方式**：在每个 token 位置，从残差流激活 \( \mathbf{h}^{(l)}(x_i) \) 中减去 α 倍沿流形方向的成分（式 10）。
- **理论分析**：定理 4.1 证明干扰噪声的期望范数可由 \(\operatorname{tr}\left((I-P_{\mathcal{M}})\Sigma_{\text{noise}}\right)\) 给出；定理 4.2 证明该噪声会逐层放大并破坏模型能力。

### 2.3 算法流程（文字描述）

1. 数据构建：对目标模型生成回答，得到冗余集和简洁集。
2. 方向提取：计算两组残差流激活的均值差，得到原始干预方向。
3. 流形学习：对所有推理样本的激活矩阵做 PCA，取前 k 个主成分构成流形。
4. 流形投影：将原始方向投影到流形上，得到流形方向。
5. 推理时干预：在每个 token 的残差流中减去 α 倍沿流形方向的成分（所有层均应用）。

## 3. 实验设计

### 3.1 使用的数据集/场景

- **数学推理**：GSM8K、MATH500、AMC2023、AIME2024（难度递增）。
- **代码生成**：LiveCodeBench。
- **知识 QA**：GPQA-Diamond（专家级学科知识）。
- **跨任务迁移（安全）**：AdvBench（jailbreak 攻击评测）。

### 3.2 Benchmark 与对比方法

- **目标模型**：DeepSeek-R1 蒸馏系列：R1-1.5B、R1-7B、R1-8B（基于 Llama）、R1-14B。
- **对比方法**：
  - **Dynasor**：通过定期探测中间状态（Certaindex 指标）决定是否提前停止，需要额外计算。
  - **SEAL**：使用思想分类（执行/反思/过渡）提取方向，进行干预。
  - 此外还有**直接干预（Direct Steering）** 作为基线对比。

### 3.3 评估指标

- **Pass@1**：准确率（↑）。
- **平均 Token 数（#Tokens）**：衡量推理长度（↓）。

## 4. 资源与算力

- 文中未明确说明所使用的 GPU 型号、数量及训练时长等具体资源信息。仅在附录 E 的延迟分析中提到实验在 **Ubuntu 22.04 系统 + A800 GPU** 上运行。未提供模型训练或干预所需的完整算力统计。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 主实验（Table 1）：在 4 个数学数据集上对比 4 个模型 + 3 种方法，共 48 组结果。
  - 跨域迁移（Figure 3）：代码和知识 QA 两项任务。
  - 方向分析（Figure 4）：正向/反向干预的案例展示。
  - 超参数调优（Figure 5）：对 α 进行 5 个值的扫描，并在 Figure 7 中展示四个模型的 α 扫描。
  - 层选择（Appendix D）：对每个模型进行 7~11 个层的对比。
  - 跨任务转移（Figure 6）：安全 jailbreak 实验，验证方向投影的通用性。
  - 时间延迟（Appendix E）：对比三种方法的推理时间。
- **充分性评估**：实验较充分，覆盖了多个模型规模、多个难度数据集、跨域迁移、消融分析，且与最新基线公平对比。所有实验均在同一设置下进行，结果透明。但未提及多次运行的标准差/误差棒，未明确说明采样随机性的影响（虽然提到 temperature=0 用于评估，但生成初始方向时可能涉及随机性）。总体而言实验设计客观、较公平。

## 6. 论文的主要结论与发现

- **Manifold Steering 显著优于基线方法**：在数学任务上实现最高 **71% Token 减少**（GSM8K，R1-1.5B），同时准确率保持甚至提升（+0.5%~+3.3%）。
- **跨域转移能力强**：在代码生成和知识 QA 任务上同样有效减少 Token 12%~27%，准确率基本不变。
- **低维流形假设得到验证**：激活空间存在低维结构，投影可消除高维噪声。
- **方向性分析证实干预的有效性**：正向干预使输出简洁自信，反向干预则加剧过度思考。
- **跨任务可转移**：该方法还可用于抑制模型的拒绝回答特征（安全 jailbreak），实现 100% 攻击成功率，说明方法具有通用性。
- **模型规模与过度思考关系**：大模型（如 R1-14B）的过度思考相对较轻，但干预仍有效果。

## 7. 优点

- **理论基础扎实**：通过定理量化干扰噪声的范数及其逐层放大机制，为方法提供了严格的数学支撑。
- **方法简单有效**：仅需 PCA 投影即可显著提升干预效果，不引入额外推理开销（几乎没有延迟增加）。
- **跨域、跨任务泛化能力强**：从数学到代码、知识 QA 甚至安全任务均表现稳定。
- **实验结果丰富**：多模型、多数据集、多基线对比，结论可靠。
- **可解释性强**：方向分析直观展示干预对输出风格的影响。

## 8. 不足与局限

- **未涉及多模态模型**：方法仅在纯文本 LRM 上验证，能否推广到视觉-语言模型等未知。
- **与专业领域交互未充分探索**：如法律、医学等高度专业化推理场景，过度的流形投影可能丢失关键信息。
- **动态策略未实现**：当前使用固定的 α 和固定的层选择，未根据任务复杂度自适应调整干预强度。
- **方向提取依赖领域内数据**：需要预先收集冗余/简洁样本，可能不适用于零样本或全新任务（但跨域实验表明有一定泛化性）。
- **未提供详细的算力消耗统计**：不利于可重复性评估。
- **未进行多次运行的统计分析**：缺少误差棒，可能对结果的小幅波动缺乏稳健性说明。
- **安全任务中 100% jailbreak 成功率的反作用**：尽管展示了方法可转移性，但也暴露了滥用风险，论文本身未讨论相应的防御措施。

（完）

---
title: Adaptive Defense against Harmful Fine-Tuning for Large Language Models via Bayesian Data Scheduler
title_zh: 基于贝叶斯数据调度器的自适应有害微调防御
authors: "Zixuan Hu, Li Shen, Zhenyi Wang, Yongxian Wei, Dacheng Tao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=sm2e1SnMK4"
tags: ["query:smd"]
score: 9.0
evidence: 贝叶斯数据调度器用于自适应防御有害微调，涉及数据调度
tldr: 针对有害微调攻击，该论文提出贝叶斯数据调度器（BDS），将防御问题转化为贝叶斯推理，在微调阶段自适应地选择安全数据与普通数据的混合比例，无需攻击模拟。实验表明BDS能动态适应不同攻击策略，有效保持模型安全性，同时不牺牲微调性能，为数据调度防御提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 705, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 701, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 630, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 722, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 713, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 706, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 1956, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1428, \"height\": 2219, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-sm2e1snmk4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 711, \"height\": 326, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 719, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 711, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1007, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 719, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 714, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1362, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 951, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1354, \"height\": 190, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 750, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 807, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1012, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 775, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1152, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1141, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 808, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 523, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 583, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1375, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1019, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-sm2e1snmk4/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1414, \"height\": 124, \"label\": \"Table\"}]"
motivation: 现有防御依赖攻击模拟，难以应对未知攻击且适应性差。
method: 将防御建模为贝叶斯推理，学习安全数据与普通数据的后验分布，动态调度训练数据。
result: 在多种攻击场景下，BDS均能保持高安全性且性能损耗小，优于已有防御方法。
conclusion: 数据调度是一种无需先验攻击知识的高效防御思路，具有广阔应用前景。
---

## Abstract
Harmful fine-tuning poses critical safety risks to fine-tuning-as-a-service for large language models. Existing defense strategies preemptively build robustness via attack simulation but suffer from fundamental limitations: (i) the infeasibility of extending attack simulations beyond bounded threat models due to the inherent difficulty of anticipating unknown attacks, and (ii) limited adaptability to varying attack settings, as simulation fails to capture their variability and complexity. To address these challenges, we propose Bayesian Data Scheduler (BDS), an adaptive tuning-stage defense strategy with no need for attack simulation. BDS formulates harmful fine-tuning defense as a Bayesian inference problem, learning the posterior distribution of each data point's safety attribute, conditioned on the fine-tuning and alignment datasets. The fine-tuning process is then constrained by weighting data with their safety attributes sampled from the posterior, thus mitigating the influence of harmful data. By leveraging the post hoc nature of Bayesian inference, the posterior is conditioned on the fine-tuning dataset, enabling BDS to tailor its defense to the specific dataset, thereby achieving adaptive defense. Furthermore, we introduce a neural scheduler based on amortized Bayesian learning, enabling efficient transfer to new data without retraining. Comprehensive results across diverse attack and defense settings demonstrate the state-of-the-art performance of our approach. Code is available at https://github.com/Egg-Hu/Bayesian-Data-Scheduler.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：LLM 的“微调即服务”模式中，恶意用户可在微调数据中混入有害样本（harmful fine-tuning），导致模型安全对齐被破坏。现有防御方法（如 Vaccine、Booster、RepNoise）通常基于**攻击模拟**预先生成假设的对抗样本，但存在两个根本局限：
    - 无法模拟未知攻击（威胁模型有界）；
    - 适应性差，难以应对攻击策略的多样性和可变性。
- **整体含义**：本文提出一种**无需攻击模拟**的自适应防御框架 BDS，将有害微调防御转化为贝叶斯推理问题，通过推断每个数据点的安全属性后验分布，动态调度训练数据权重，从而在不牺牲微调性能的前提下抑制有害数据的影响。

## 2. 方法论

### 2.1 核心思想
- 将防御视为**联合贝叶斯推理**：给定安全对齐数据集 \(D_{\text{safe}}\) 和用户提供的微调数据集 \(D_{\text{ft}}\)，推断潜在变量——数据权重向量 \(w\) 和模型参数 \(\theta\) 的联合后验 \(p(w, \theta \mid D_{\text{ft}}, D_{\text{safe}})\)。
- **数据权重** \(w_i\) 表示第 \(i\) 个样本的安全属性，权重越高越可能是安全数据。
- 微调过程中，每个样本的损失被其权重 \(w_i\)（经过 softmax 变换）调制，从而自动降低有害样本的影响。

### 2.2 关键技术细节
- **后验分解**：利用概率图模型和贝叶斯公式分解联合后验：
  \[
  p(\theta, w \mid D_{\text{ft}}, D_{\text{safe}}) \propto p(D_{\text{safe}} \mid \theta) \cdot p(D_{\text{ft}} \mid \theta, w) \cdot p(D_{\text{ft}} \mid w)^{-1} \cdot p(\theta, w)
  \]
  其中 \(p(D_{\text{ft}} \mid \theta, w) = \prod_i \exp(-\sigma(w_i) \cdot \ell(z_i^{\text{ft}}; \theta))\)，\(\sigma\) 为权重变换函数。
- **SGLD 采样**：采用随机梯度 Langevin 动力学（SGLD）近似后验采样，迭代更新 \(\theta\) 和 \(w\)（或神经网络参数 \(\phi\)）。
  - 模型更新（式7）：结合安全数据损失和加权的微调数据损失。
  - 权重更新（式8）：利用损失差，让“安全感知模型”与“安全无关模型”的损失差异指导权重下降/上升。
- **权重变换**：对比了 identity、sigmoid、softmax 三种变换，**softmax** 能实现双向适应：低于加权平均损失的数据权重上升，否则下降，从而有效区分安全与有害数据。
- **两种实现**：
  - **贝叶斯标量调度器（Scalar）**：为每个数据点独立学习一个标量权重 \(w_i\)，需随数据集大小扩展。
  - **摊销贝叶斯神经网络调度器（Neural）**：用一个小网络 \(N(\cdot; \phi)\) 将数据点映射到权重，共享参数 \(\phi\)，可迁移至新数据而无需重训练。

### 2.3 算法流程（文字描述）
1. 初始化调度器参数（标量 \(w\) 或网络 \(\phi\)）；
2. 每轮：
   - 从 \(D_{\text{safe}}\) 和 \(D_{\text{ft}}\) 采样小批量；
   - 计算当前 \(\theta\) 在安全数据上的损失和加权微调数据损失，更新 \(\theta\)（式7）；
   - 根据加权的微调数据损失，更新调度器参数（标量式8或网络式11）；
3. 重复直至收敛，最终 \(\theta^{(T)}\) 即为定制的安全模型。

## 3. 实验设计

### 3.1 数据集与场景
- **安全数据集** \(D_{\text{safe}}\)：来自 BeaverTails 的增强版（有害提示-安全回答对）。
- **微调数据集** \(D_{\text{ft}}\)：混合不同比例 \(p\) 的有害数据（BeaverTails）与良性数据（SST2、AGNews、GSM8K、AlpacaEval、GEM等）。
- **攻击场景**：
  - 不同有害比例（\(p = 0.05 \sim 1.0\)）；
  - 良性攻击（\(p=0\)）；
  - OOD 攻击（RealToxicityPrompts、AdvBench）；
  - 身份偏移攻击（ISA）。
- **模型架构**：Llama2-7B、Gemma2-9B、Qwen2-7B。

### 3.2 Benchmark 与对比方法
- **评价指标**：
  - **有害分数（HS）**：模型输出被 BeaverTails 审核模型判定为有害的比例（越低越好）。
  - **微调准确率（FA）**：在对应微调任务上的标准准确率（越高越好）。
- **对比基线**：SFT（无防御）、Lisa、RepNoise、Vaccine、Booster（SOTA 攻击模拟方法）。

### 3.3 主要实验内容
- **主表（表1）**：低有害比例（0~0.2）下 BDS 与所有基线的对比。
- **高有害比例鲁棒性（表2）**：\(p=0.3 \sim 1.0\)，仅与 Booster 对比。
- **多任务泛化（表3）**：SST2、AGNews、GSM8K、AlpacaEval。
- **多架构泛化（表4）**：Llama2、Gemma2、Qwen2。
- **不同 \(|D_{\text{ft}}|\) 和 \(|D_{\text{safe}}|\) 的鲁棒性（表5、表6）**。
- **神经网络调度器的有效性及迁移性（表7）**：域内/域外迁移。
- **高级攻击鲁棒性（表8、表9）**：OOD 攻击和 ISA 攻击。
- **消融实验（附录E）**：权重变换函数、先验、初始化、对齐数据集影响等。
- **额外实验（附录D）**：GEM 数据到文本生成、检测方法对比、确定性数据策展方法对比等。

## 4. 资源与算力

- 文中明确说明：**所有实验在单张 NVIDIA A100-40GB GPU 上运行**（附录 G.1）。
- BDS 每轮只需两次反向传播，时间与内存开销接近标准微调；对比之下，Booster 需要 H100-80GB GPU 且耗时多 3 倍以上。
- 未见关于具体训练时长（总 GPU 小时数）的定量说明，但给出了每个 epoch 约 2.04 分钟（A100）。

## 5. 实验数量与充分性

- **实验组数丰富**：主实验涵盖 5 个数据集、3 种模型架构、多种有害比例（0~1.0）、多种攻击策略，并包含不同 \(|D_{\text{ft}}|\)、\(|D_{\text{safe}}|\) 的鲁棒性测试、神经网络迁移测试、消融实验、检测方法对比等，总计超过 20 个表格。
- **充分性评价**：实验设计较全面，覆盖了典型和极端攻击场景，对比方法均为当前代表工作，评估指标同时包含安全性和可用性。但在以下方面可进一步提升：
  - 缺少对更多样化模型家族（如 GPT 风格 moe 模型）的验证；
  - 未报告多次重复实验的误差棒（文中解释为社区惯例和计算成本）；
  - 部分消融（如权重先验）仅在默认设置下测试，未见跨设置稳定性分析。
- **公平性**：超参数设置尽可能遵循基线原论文，较合理。

## 6. 主要结论与发现

- BDS 在所有有害比例、攻击策略、数据集和模型架构下均**显著优于所有基线**，尤其在极端高有害比例（\(p=0.9\)）下有害分数降低 74.4%。
- **无需攻击模拟**是核心优势：Bayesian 后验条件于实际微调数据，实现自适应防御。
- 权重变换函数 **softmax** 是成功的关键，可实现双向、自适应的权重调度。
- 神经网络调度器不仅性能接近标量版本，还能**零样本迁移**到新数据（域内/域外），展示了学习到的数据安全属性的可迁移性。
- 在“有用性-无害性”权衡上，BDS 通过联合优化（多任务学习）比两阶段的 SFT 更好地平衡两者。

## 7. 优点：方法与实验设计的亮点

- **方法创新**：首次将有害微调防御形式化为贝叶斯推理问题，提供了一种无需攻击模拟的、有理论依据的软权重调度框架。
- **自适应强**：后验条件于实际数据集，能自动适应不同攻击策略和有害比例。
- **计算高效**：相比 Booster，BDS 在单卡 A100 上即可运行，训练时间和显存接近标准微调，更具实用性。
- **实验设计扎实**：覆盖多种攻击情景（良性、OOD、ISA）、跨模型、跨数据集、跨数据集规模的系统评估，消融分析完善。
- **神经网络调度器**展示了良好的迁移能力，为实际部署提供了灵活性。

## 8. 不足与局限

- **依赖安全对齐数据集** \(D_{\text{safe}}\)：其质量和规模会影响防御效果，极端情况下（如 \(D_{\text{safe}}\) 极小时）有害分数仍会略微上升（但远优于基线）。
- **权重先验选择**：默认采用无信息先验，虽避免误导但缺乏正则化，论文未深入分析先验敏感性的边界。
- **未报告统计显著性**：缺少多次运行的误差棒，影响结果稳健性判断。
- **仅测试了 LoRA 微调**：未探索全参数微调场景下方法是否依然高效。
- **未讨论防御可能被绕过的方式**：如自适应攻击者可能针对权重更新机制设计特殊有害样本。

（完）

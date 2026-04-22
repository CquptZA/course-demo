
# 测试时自适应（TTA）

## 任务背景

近年来，深度学习模型在标准数据集上取得了优异表现，但在实际应用中往往面临**分布偏移（Distribution Shift）**问题，例如噪声干扰、领域变化或数据风格变化等。这些变化会导致模型性能显著下降。

测试时自适应（Test-Time Adaptation, TTA）作为一种新兴技术，旨在**在不使用训练数据或标签的情况下，仅利用测试数据对模型进行动态调整**，从而提升模型在未知环境中的泛化能力。

本任务旨在让同学们在掌握深度学习模型基础的前提下，深入理解并实践主流TTA方法，并通过实验对比它们在分布偏移场景中的性能、稳定性与效率。

---

## 任务目标

* 阅读并理解主流TTA方法的核心原理与实现机制
* 选择至少三种TTA方法进行实现或调用现有开源工具
* 在统一的分布偏移任务上进行测试与评估
* 比较它们的性能（准确率、鲁棒性等）、推理开销等指标
* 撰写实验报告，分析各方法的优劣和适用场景

---

## 任务内容

### 1. 选题与准备

* 可选任务（任选其一）：

  * 图像分类（如 CIFAR-10 → CIFAR-10-C）
  * 情感分类（如 IMDb + 噪声/扰动数据）
  * 新闻分类（如 AG News + 领域迁移）
  * （进阶）跨领域任务（如训练在一个数据集，测试在另一个）

* 分布偏移类型（至少选择一种）：

  * 噪声干扰（Gaussian Noise / Blur）
  * 风格变化（Style Shift）
  * 领域变化（Domain Shift）

* 模型基线：

  * 图像任务：ResNet-18 / ViT
  * 文本任务：BERT-base

---

### 2. 方法实现（至少选择三种，需覆盖不同策略类别）：

#### **基于预测优化类**

* TENT（Test-time Entropy Minimization）
* MEMO（Test-time Augmentation）

#### **统计调整类**

* BN Adaptation（BatchNorm统计更新）
* AdaBN（Adaptive BatchNorm）

#### **参数更新类**

* SHOT（Source Hypothesis Transfer）
* CoTTA（Continual Test-Time Adaptation）

可以使用PyTorch、开源实现或自行复现。

---

### 3. 实验与评估

* 在相同任务和模型初始化下，分别应用各TTA方法

* 控制变量（模型结构、数据、训练方式一致）

* 评估并记录以下指标：

  * 测试集性能（Accuracy / F1-score 等）
  * 不同分布偏移强度下的鲁棒性
  * 推理时间开销（是否影响实时性）
  * 是否需要额外存储（缓存/历史数据）
  * 是否存在性能退化或不稳定现象

---

## 进阶方向

* 尝试结合多个TTA方法（如 TENT + BN Adaptation）
* 比较**在线TTA vs 离线TTA**效果
* 分析**灾难性遗忘（Catastrophic Forgetting）**问题
* 探索在小批量甚至单样本情况下的TTA表现
* 可视化模型在测试时的参数变化或预测分布变化

---

## 评分标准

| **评分项**           | **分值** |
| ----------------- | ------ |
| 实现完整性（≥3种方法）      | 30%    |
| 实验设计科学性（控制变量、复现性） | 20%    |
| 结果分析与对比深度         | 20%    |
| 报告规范性与表达清晰度       | 20%    |
| 创新点（改进方法、扩展实验等）   | 10%    |

---

## 参考资源

* TENT论文: [https://arxiv.org/abs/2006.10726](https://arxiv.org/abs/2006.10726)
* MEMO论文: [https://arxiv.org/abs/2110.09506](https://arxiv.org/abs/2110.09506)
* CoTTA论文: [https://arxiv.org/abs/2203.13591](https://arxiv.org/abs/2203.13591)
* SHOT论文: [https://arxiv.org/abs/2002.08546](https://arxiv.org/abs/2002.08546)
* CIFAR-10-C数据集: [https://github.com/hendrycks/robustness](https://github.com/hendrycks/robustness)



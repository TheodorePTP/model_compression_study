## 🧪 知识蒸馏方法分类总览

本表系统梳理了知识蒸馏（Knowledge Distillation）领域的经典与前沿工作，按 **蒸馏信号来源** 分为三类：

- **Logits 层**：仅利用最终输出 logits
- **Feature 层**：利用中间特征图或表示
- **Relation 层**：利用样本间关系或结构信息

---

### 1️⃣ Logits-based KD（基于输出层）

| 方法 | 核心思想 | 论文 |
| :--- | :--- | :--- |
| KD | 使用带温度的软标签蒸馏 logits | [arXiv:1503.02531](https://arxiv.org/abs/1503.02531) |
| DKD | 将 logits 蒸馏解耦为目标类与非目标类两部分，提升优化效率 | [arXiv:2203.08679](https://arxiv.org/abs/2203.08679) |

### 2️⃣ Feature-based KD（基于中间特征）

| 方法 | 核心思想 | 论文 |
| :--- | :--- | :--- |
| FitNet | 通过回归损失对齐教师与学生的中间层特征（Hints） | [arXiv:1412.6550](https://arxiv.org/abs/1412.6550) |
| AT | 蒸馏注意力图（activation 的 L2 范数），保留空间重要性 | [arXiv:1612.03928](https://arxiv.org/abs/1612.03928) |
| NST | 蒸馏神经元选择性（Gram 矩阵），捕捉高阶统计特性 | [arXiv:1707.01219](https://arxiv.org/abs/1707.01219) |
| OFD | 通过在小样本学习中过拟合来创建更强的教师模型进行蒸馏 | [arXiv:1904.01866](https://arxiv.org/abs/1904.01866) |
| ReviewKD | 通过"复习"机制聚合多层教师特征指导学生 | [arXiv:2104.09044](https://arxiv.org/abs/2104.09044) |

### 3️⃣ Relation-based KD（基于样本关系）

| 方法 | 核心思想 | 论文 |
| :--- | :--- | :--- |
| PKT | 将特征映射为概率分布，蒸馏分布间的相似性 | [arXiv:1803.10837](https://arxiv.org/abs/1803.10837) |
| KDSVD | 对特征矩阵做 SVD，蒸馏主成分方向 | [arXiv:1807.06819](https://arxiv.org/abs/1807.06819) |
| RKD | 蒸馏样本对之间的距离与角度关系 | [arXiv:1904.05068](https://arxiv.org/abs/1904.05068) |
| VID | 建模教师特征的不确定性，用变分推断传递信息 | [arXiv:1904.05835](https://arxiv.org/abs/1904.05835) |
| SP | 要求学生保留教师中样本对的相似性（内积） | [arXiv:1907.09682](https://arxiv.org/abs/1907.09682) |
| CRD | 借鉴对比学习，将教师特征作为正样本进行蒸馏 | [arXiv:1910.10699](https://arxiv.org/abs/1910.10699) |

---

### 📊 方法演进趋势

- **Logits 层**：实现简单，适合快速部署
- **Feature 层**：适合 CNN 架构对齐，提升特征表达
- **Relation 层**：适合表示学习、度量任务，保持embedding 空间结构
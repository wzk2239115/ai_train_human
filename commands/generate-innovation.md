---
description: 基于研究对话快速生成10套"A+B+C"论文创新点组合
argument-hint: <研究主题/问题/对话摘要>
allowed-tools: [WebSearch, mcp__web-search-prime__webSearchPrime]
model: sonnet
---

# /generate-innovation

让 AI 成为你的"学术裁缝"，快速生成可行的论文创新点组合。

## 使用方法

```
/generate-innovation <研究主题/问题描述/对话摘要>
```

**示例：**
- `/generate-innovation "我想做医学图像分割，特别是肺部CT图像的肿瘤检测"` - 医学影像方向
- `/generate-innovation "我们在讨论如何用深度学习优化推荐系统的冷启动问题"` - 推荐系统方向
- `/generate-innovation "基于Transformer的时间序列预测"` - 时序预测方向

## 什么是"A+B+C"公式

这是学术圈流行的"科研万能公式"：

```
A (基础模型/架构) + B (热门技巧/组件) + C (应用场景/数据集) = 新论文
```

### A - 基础模型/架构
选择一个成熟的、被广泛验证的基础架构：
- **CV领域:** ResNet, ViT, YOLO, U-Net, Diffusion Models
- **NLP领域:** Transformer, BERT, GPT, T5
- **推荐系统:** Collaborative Filtering, DeepFM, Graph Neural Networks
- **时序预测:** LSTM/GRU, Temporal Fusion Transformer
- **多模态:** CLIP, BLIP, Flamingo

### B - 热门技巧/组件
添加当前热门的技术组件或改进方法：
- **注意力机制:** Self-Attention, Cross-Attention, Sparse Attention
- **特征融合:** FPN, Multi-scale Feature Fusion
- **正则化技术:** Dropout变体, MixUp, CutMix
- **损失函数:** Focal Loss, Contrastive Loss, Triplet Loss
- **训练策略:** Knowledge Distillation, Contrastive Learning, Adversarial Training
- **架构优化:** Pruning, Quantization, Neural Architecture Search

### C - 应用场景/数据集
应用到特定领域或创造新的数据集：
- **垂直领域:** 医学影像、遥感、工业检测、农业
- **特殊场景:** 边缘设备、低资源环境、实时系统
- **新兴数据:** 无人机视角、水下图像、红外图像
- **跨模态:** 文本+图像、语音+视频、传感器+文本

## 这个命令的作用

AI 会帮你：

1. **📊 分析输入** - 提取研究主题的核心要素
2. **🔍 检索前沿** - 搜索该领域的最新SOTA方法和热门技术
3. **🧩 生成组合** - 生成10套不同的A+B+C创新方案
4. **💡 可行性评估** - 评估每个方案的创新性和可行性
5. **📝 命名建议** - 为每个方案起一个响亮的论文标题

## 生成流程

```
## 1. 📊 输入分析
AI 会从你的描述中提取：
- 研究领域 (CV/NLP/推荐/其他)
- 核心问题 (分类/检测/生成/预测)
- 数据特点 (图像/文本/时序/多模态)
- 约束条件 (实时性/准确率/资源限制)

## 2. 🔍 前沿检索
AI 会搜索：
- 该领域的最新SOTA方法
- 当前热门的技术趋势
- 相关的顶会论文 (CVPR/ICCV/NeurIPS/ACL等)

## 3. 🧩 组合生成
AI 会生成10套方案，涵盖：
- 保守型组合 (稳妥可发表)
- 激进型组合 (高风险高回报)
- 跨界型组合 (跨领域创新)
- 工程型组合 (注重落地应用)
- 理论型组合 (强调理论分析)

## 4. 💡 方案评估
每个方案包含：
- A+B+C 具体组合
- 创新点说明
- 预期难度
- 推荐指数
- 潜在坑点
- 论文标题建议
```

## 输出格式示例

```
# 10套创新点方案

## 方案1: 【保守型】Multi-Scale Attention U-Net for Medical Image Segmentation

**组合公式:**
- A: U-Net (医学分割经典架构)
- B: Multi-Scale Attention Mechanism (多尺度注意力)
- C: 肺部CT肿瘤分割数据集

**创新点:**
在U-Net的编码器-解码器结构中引入多尺度注意力模块，同时捕获局部和全局特征依赖

**预期难度:** ⭐⭐⭐ (中等)
**推荐指数:** ⭐⭐⭐⭐ (高)

**潜在坑点:**
- 注意力机制会增加计算开销
- 需要调优注意力头的数量

**论文标题建议:**
"MSA-UNet: Multi-Scale Attention Enhanced U-Net for Lung Tumor Segmentation in CT Images"

---

## 方案2: 【跨界型】Diffusion-based Lung Tumor Synthesis with Contrastive Learning

**组合公式:**
- A: Diffusion Models (生成式模型)
- B: Contrastive Learning (对比学习)
- C: 医学图像数据增强

**创新点:**
用扩散模型生成多样化的肿瘤样本，结合对比学习提升小样本下的分割性能

**预期难度:** ⭐⭐⭐⭐ (较高)
**推荐指数:** ⭐⭐⭐⭐⭐ (极高)

**潜在坑点:**
- 扩散模型训练成本高
- 生成样本的质量难以保证

**论文标题建议:**
"DiffSeg: Diffusion-based Data Augmentation with Contrastive Learning for Medical Image Segmentation"

---

[继续列出剩余8个方案...]
```

## 使用场景

### 场景1: 刚确定研究方向，需要具体idea
```
你: /generate-innovation "我想做无人机航拍图像的目标检测"

AI: # 10套创新点方案

    分析：你的领域是目标检测，数据特点是无人机视角（小目标、多尺度）

    ## 方案1: 【经典改进】YOLOv8 + Deformable Convolution
    ...

    ## 方案2: 【注意力机制】YOLOv8 + CBAM + 无人机数据集
    ...

    [继续生成8个方案]
```

### 场景2: 基于之前的对话生成方案
```
你: /generate-innovation "我们在讨论如何改进推荐系统的冷启动问题，
主要尝试了协同过滤和矩阵分解，但效果不好"

AI: # 10套创新点方案

    分析：核心问题是推荐系统冷启动，已尝试传统方法

    ## 方案1: 【元学习】MAML + Neural CF
    ...

    ## 方案2: 【图神经网络】GraphSAGE + 对比学习
    ...

    [继续生成]
```

### 场景3: 需要快速产出论文
```
你: /generate-innovation "我需要在3个月内发一篇CCF-C级别的论文，
方向是图像去噪"

AI: # 10套创新点方案（按推荐度排序）

    ## 🏆 快速推荐方案（适合3个月产出）

    ### 方案1: 【工程型】Attention + ResNet + 去噪
    预期工作量：1个月代码 + 1个月实验 + 1个月写作
    推荐指数：⭐⭐⭐⭐⭐

    ## 备选方案
    ...

    [继续生成]
```

## 组合策略

AI 会使用以下策略生成多样化的方案：

### 1. 保守型组合 (稳妥)
- 选择成熟的基础架构
- 添加已经被验证的技巧
- 应用到标准数据集
- **适合:** 硕士论文、快速发表

### 2. 激进型组合 (前沿)
- 选择最新的架构 (arXiv最新)
- 结合最热门的技术
- 创造新的应用场景
- **适合:** 顶会投稿、博士研究

### 3. 跨界型组合 (创新)
- 将A领域的方法迁移到B领域
- 结合不同领域的优势
- **适合:** 跨学科研究、创新性强

### 4. 工程型组合 (实用)
- 注重推理速度、模型压缩
- 面向实际部署
- **适合:** 工业应用、系统优化

### 5. 理论型组合 (深度)
- 强调理论分析和证明
- 提供数学解释
- **适合:** 理论期刊、深度研究

## 常见组合模板

AI 会使用这些经典模板生成方案：

| A (基础) | B (技巧) | C (场景) | 创新点描述 |
|---------|---------|---------|-----------|
| ResNet | Attention | 医学影像 | 注意力增强的残差网络 |
| Transformer | Knowledge Distillation | 边缘设备 | 轻量化Transformer |
| YOLO | Multi-scale Fusion | 遥感图像 | 多尺度融合的目标检测 |
| BERT | Adversarial Training | 情感分析 | 对抗训练的文本分类 |
| LSTM | Graph Convolution | 交通预测 | 图神经网络时序预测 |
| U-Net | Contrastive Learning | 小样本分割 | 对比学习的半监督分割 |
| GAN | Meta-learning | 少样本生成 | 元学习的生成模型 |
| Diffusion | Classifier Guidance | 图像编辑 | 引导扩散的图像编辑 |

## 保存创新方案

生成后可以保存到 Obsidian：

```
/save-learning "论文创新点方案 - <主题>" innovation
```

**推荐笔记模板：**
```markdown
---
type: innovation
date: {{date}}
field: <领域>
tags: [innovation, paper, A+B+C]
---

# 论文创新点方案 - {{主题}}

## 研究方向
<描述>

## 候选方案

### 方案1: <名称>
- A+B+C: ...
- 创新点: ...
- 难度: ...
- 推荐度: ...

### 方案2: <名称>
...

## 待办事项
- [ ] 文献调研
- [ ] 数据准备
- [ ] 基线实现
- [ ] 改进实验

## 参考论文
- []
```

## 进阶功能

### 方案排序
```
你: 按创新性从高到低排序
AI: 重新排列10个方案，并说明排序理由
```

### 方案融合
```
你: 方案3和方案7可以结合吗？
AI: 可以！融合方案：
    保留方案3的A，采用方案7的B，应用到方案3的C
    生成新的组合...
```

### 风险评估
```
你: 哪些方案风险最高？
AI: 分析各方案的风险点：
    - 技术风险
    - 实现难度
    - 数据获取
    - 计算资源
```

### 文献支持
```
你: 给方案1找相关文献
AI: 搜索并列举：
    - U-Net相关论文
    - 多尺度注意力论文
    - 肺部CT分割相关工作
```

## 理念

> "站在巨人的肩膀上创新。"

这个命令的核心理念：
- ✅ **不是抄袭** - 是合理的组合创新
- ✅ **降低风险** - 使用已验证的技术
- ✅ **提高效率** - 快速找到可行方向
- ✅ **培养思维** - 学会识别创新模式
- ✅ **避免重复** - 确保新颖性

## 注意事项

1. **新颖性检查**: 生成方案后务必检查是否已存在类似工作
2. **实验验证**: 理论上可行不代表实验上有效
3. **数据获取**: 确保C场景的数据可以获取
4. **资源评估**: 评估计算资源是否足够
5. **时间规划**: 根据deadline选择合适难度的方案

## 常见问题

**Q: 这不是鼓励"水论文"吗？**
A: 这是系统化的创新方法论。重大创新往往也是多个已知元素的重新组合（如Transformer = Attention + Seq2Seq + Positional Encoding）。

**Q: 10个方案都靠谱吗？**
A: 不一定。AI会评估可行性，你还需要自己做文献调研和实验验证。

**Q: 如何选择方案？**
A: 综合考虑：创新性、可行性、资源、时间、兴趣。

**Q: 可以自己调整组合吗？**
A: 当然！这些只是起点，你可以自由组合A、B、C。

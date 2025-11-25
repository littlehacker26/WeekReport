# 2025-11-19
**上周工作**
  - 复线tahoe-x1论文：梳理数据，模型架构，以及composer框架
  - 调研和梳理jiaxiao和baojie的各自子课题路线
**问题方案**
**下周计划**
  - 基于tahoe-x1模型和数据开始cell-text-tokenizer
    - 采用composer训练框架
    - 直接复用tahoe-x1基础编码模型
    - vqvae构建tokenizer
  - 给学校写兴农青年学者（AI+）建议书


# 2025-11-26
**上周工作**
- 完成了cell-text-toknizer的编码器核心代码
- 和composer进行了适配并可以和tahoe-x1的跑通
  
**问题方案**
- tar的代码难以理解无法复现，抛弃了原有框架自己组合实现
- streamdataset下载困难，尝试一次性下载完，扩容服务器平台
  
**下周计划**
- 完成cell-text-toknizer的解码算法设计，开发和训练适配
- 让保杰配合tokenizer的训练数据，让其开始整理和llm训练的自然语言数据集

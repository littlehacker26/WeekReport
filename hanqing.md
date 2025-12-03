## 2025-11-19
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


## 2025-11-26
**上周工作**
- 完成了cell-text-toknizer的编码器核心代码
- 和composer进行了适配并可以和tahoe-x1的跑通
  
**问题方案**
- tar的代码难以理解无法复现，抛弃了原有框架自己组合实现
- streamdataset下载困难，尝试一次性下载完，扩容服务器平台
  
**下周计划**
- 完成cell-text-toknizer的解码算法设计，开发和训练适配
- 让保杰配合tokenizer的训练数据，让其开始整理和llm训练的自然语言数据集

## 2025-12-03
**上周工作**
- 完成了cell-text-toknizer编码解码全部代码实现工作
- 思考两个小同学的研究点
  - jiaoxiao考虑decode-time的抗菌肽生成
  - baojie 考虑自回归式的cell-语言模型
  
**问题方案**
- cell-text-toknizer的训练效果不及预期，测试指标较差像是不太work
  
**下周计划**
- 分步调试cell-text-toknizer，完善到较好的状态

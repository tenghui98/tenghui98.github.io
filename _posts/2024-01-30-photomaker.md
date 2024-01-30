---
title: PhotoMaker论文
date: 2024-01-24
categories: [read paper]
tags: [zero-shot lora]     # TAG names should always be lowercase
---

# PhotoMaker要解决什么问题
Stable Diffusion（简称SD）存在一个缺点，那就是不能生成某个特定的目标对象。比如可以生成猫，但是不能生成自己家的猫。因此为了让SD具有这种生成自定义特定对象的能力，研究者提出了两种finetune SD的方法，分别是Dreambooth和Text Inversion。通过收集几张某个特定对象的不同角度的照片用这两种方法对SD进行finetune，便能使得SD能生成该特定的对象。但这两种方法对每个需要生成的特定对象都需要一个finetune的训练过程，需要耗费时间和机器资源，限制了使用。（在新的SDXL模型上进行Dreambooth的finetune至少需要24G的显存）。为了解决这个问题，PhotoMaker提出了一种新的finetune-free的方法，能在推理时直接根据几张某个特定对象的图片让SD完成对该对象的生成。

# 主要创新点是什么
只需使用一张或几张图片作为SD的额外输入，便可以让SD在推理时生成该对象的多样性图片。  
对比之前的Dreambooth和Text Inversion方法，PhotoMaker不需要耗时耗力的进行finetune，便能达到同样的目的。

# PhotoMaker是怎么做的
方法的核心在于不少工作指出一个特定对象的信息在SD中能够用少数的token进行表示。
![photomaker](/assets/photomaker.png)
# 和其他方案的对比

# 总结和思考
能否代替Dreambooth

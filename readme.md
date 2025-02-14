# 基于Wnet的字体生成


**本仓库代码还有一些问题，没有时间修复，对这个算法感兴趣的朋友们请移步作者的原版实现**

[作者实现代码](https://github.com/falconjhc/W-Net)


训练：

```
python main.py
```

图例：

```
python main.py inference
```

现阶段的训练结果：

原始字体（黑体加粗）protype
---
![](./img/src.png)

目标字体（一个batch里面混合了多种字体）real
---
![](./img/target.png)

生成字体 fake
---
![](./img/out.png)


与原论文的差别
---

1. Discriminator中没有使用LayerNorm，而是用了BatchNorm
2. 没有额外再训练一个VGG分类模型，而是用Discriminator替代

TODO:
---

- [ ] 推理代码完善
- [ ] 添加更多字体
- [ ] 添加对字体支持汉字的检测功能 / 使用mask屏蔽掉不支持的字符对loss的影响
- [x] 自定义字符集

待添加的一些tricks:

- [x] label smoothing
- [ ] 在G的训练和测试阶段都添加dropout
- [ ] 使用LeaklyReLU替代ReLU
- [ ] Generator的最后一层使用Tanh激活
- [ ] 在Discriminator中使用LayerNorm
- [x] 每个batch中使用同一种字体（据说可以使训练变得更简单）
- [ ] 监控训练中的梯度变化
- [x] 添加梯度惩罚
- [ ] 历史均值
- [x] 模型推理代码

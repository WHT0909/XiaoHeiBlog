---
title: Tensorboard学习笔记
date: 2026-01-19 19:56:56
tags:
    - 深度学习
categories:
    - 其他计算机技术
---

参考 b 站资源的 Tensorboard 学习笔记
<!-- more -->

Tensorboard 是一个用于可视化 pytorch 训练的工具，这篇博客是 b 站资源<a href="https://www.bilibili.com/video/BV1Qf4y1C7kz/?spm_id_from=333.337.search-card.all.click&vd_source=0ea0c7956df75b2935422822b2001158">"在Pytorch中使用Tensorboard可视化训练过程"</a>的学习笔记

<div class="catalog">
    <h3>目录</h3>
    <a href="#chapter1">1. Tensorboard 包的导入与实例化</a><br>
    <a href="#chapter2">2. 计算图的创建</a><br>
    <a href="#chapter3">3. 添加要监控的指标</a><br>
    <a href="#chapter4">4. 绘制直方图</a><br>
    <a href="#chapter5">5. 启动 Tensorborad</a>
</div>

<h2 id="chapter1">1. Tensorboard 包的导入与实例化</h2>

```python
from torch.utils.tensorboard import SummaryWriter
tb_writer = SummaryWriter(log_dir="./test") # 将结果保存在目标文件夹下
```

<h2 id="chapter2">2. 计算图的创建</h2>

```python
# 实例化模型
model = resnet34(num_classes=args.num_classes).to(device)
# 创建一个全零的图像，作为模型的输入
init_img = torch.zeros((1, 3, 224, 224), device=device)
# 创建计算图
tb_writer.add_graph(model, init_img)
```

<h2 id="chapter3">3. 添加要监控的指标</h2>

```python
tags = ["train_loss", "accuracy", "learning_rate"]
tb_writer.add_scaler(tags[0], mean_loss, epoch)
tb_writer.add_scaler(tags[1], acc, epoch)
tb_writer.add_scaler(tags[2], optimizer.param_groups[0]["lr"], epoch)
```

第一个参数表示要监控的指标是哪个，将作为图像的标题出现

第二个参数是具体的指标

第三个参数代表在什么时候记录，例如上面使用的是 epoch，就是一个 epoch 记录一次

<h2 id="chapter4">4. 绘制直方图</h2>

```python
tb_writer.add_histogram(tag="conv1", values=model.conv1.weight, global_step=epoch)
```

常用于反映模型权重从训练开始到训练结束时的变化

<h2 id="chapter5">5. 启动 Tensorborad</h2>

```bash
tensorboard --logdir "/path/to/dir"
```
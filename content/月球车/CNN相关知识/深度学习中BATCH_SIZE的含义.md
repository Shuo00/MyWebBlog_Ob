[深度学习中BATCH_SIZE的含义 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/133864576)

按照我的经验来说，当batch_size增大后，适当增大epoch就行。最终的目的都是为了loss函数收敛。这其实也算是一种经验之谈，不必要求iterations一样。如果batch=32,epoch=10能够收敛的话，改变batch=64后，可以设置epoch=15~40都是可以的。epoch太小了可能还未收敛，epoch太大的话也没有意义。合适就好

---

**深度学习中BATCH_SIZE的含义**

在目标检测SSD算法代码中，在训练阶段遇见代码

```python
BATCH_SIZE = 4
steps_per_epoch=num_train // BATCH_SIZE
```

即每一个epoch训练次数与BATCH_SIZE大小设置有关。因此如何设置BATCH_SIZE大小成为一个问题。

  

**BATCH_SIZE的含义**

BATCH_SIZE:即一次训练所抓取的数据样本数量；

BATCH_SIZE的大小影响训练速度和模型优化。同时按照以上代码可知，其大小同样影响每一epoch训练模型次数。

  

**BATCH_SIZE带来的好处**

最大的好处在于使得CPU或GPU满载运行，提高了训练的速度。

其次是使得**梯度下降**的方向更加准确。

因此为了弄懂BATCH_SIZE的优点，需要学习梯度下降的方法。可以参见另一篇文章：

[孰能与我天下事：梯度下降的意义13 赞同 · 4 评论文章!

**BATCH_SIZE大小的影响**

若BATCH_SIZE=m(训练集样本数量);相当于直接抓取整个数据集，训练时间长，但梯度准确。但不适用于大样本训练，比如IMAGENET。只适用于小样本训练，但小样本训练一般会导致**过拟合**[[1]](https://zhuanlan.zhihu.com/p/133864576#ref_1)现象，因此不建议如此设置。

若BATCH_SIZE=1;梯度变化波动大，网络不容易收敛。

若BATCH_SIZE设置合适，梯度会变准确。

此时再增加BATCH_SIZE大小，梯度也不会变得更准确。

同时为了达到更高的训练网络精度，应该增大epoch，使训练时间变长。

  

**BATCH_SIZE大小如何影响训练梯度**

梯度的方差表示为：

![](../../💼背包/📎附件/Pasted%20image%2020230402105920.png)
m即BATCH_SIZE设置大小，即增大BATCH_SIZE的大小可以使得梯度方差的大小减小。直接使梯度更加准确。

**BATCH_SIZE的来源**

首先需要明白的是两个概念，一是以前的Gradient Descent（GD）和如今常用的SDG（Stochastic Gradient Descent）的梯度更新方法

**GD**：用所有样本的平均梯度更新每一步

**SDG**:用每一个样本的梯度更新每一步

根据含义可知GD的每一步的计算都大于SDG。在实际上，GD往往容易陷入局部最小值，使训练的loss达不到最小。而SDG的出现正好缓解了这一现象。该部分在以后专门讲解，可以参考该博主的一些视频解释。

目前的最好的解决是使用所以有了 Minibatch Gradient Descent来解决该问题，简单的说，**该方法能够自主找到最合适的BATCH_SIZE进行训练**

[怎么选取训练神经网络时的Batch size?1765 关注 · 28 回答问题](https://www.zhihu.com/question/61607442)

  

**公开的神经网络模拟网站**

该网站可以对所学的知识进行简单的验证，手机端和PC端均可以使用。左侧DATA选择数据样本，调整好Learning Rate和BATCH_SIZE大小，再点击加号添加layers，点击左上角的“播放”键可以观察到Loss曲线和结果的变化。

该部分可以通过调整BATCH_SIZE的大小来观察其与epoch之间的关系。

**当然，BATCH_SIZE越大，在得到同样精度时，需要的epoch也自然越大。**

[http://playground.tensorflow.org​playground.tensorflow.org](https://link.zhihu.com/?target=http%3A//playground.tensorflow.org)

持续更新中。。。
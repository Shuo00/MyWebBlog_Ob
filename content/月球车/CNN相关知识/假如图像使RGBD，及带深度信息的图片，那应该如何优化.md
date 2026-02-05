如果图像是RGBD，即带有深度信息的图片，可以考虑在CNN中添加额外的通道来处理深度信息。这样，CNN就可以同时学习RGB和深度信息之间的关系，从而提高模型的性能。

以下是在PyTorch中如何修改CNN模型以处理RGBD图像的示例代码：
```python
import torch.nn as nn

class RGBDNet(nn.Module):
    def __init__(self):
        super(RGBDNet, self).__init__()
        self.conv1 = nn.Conv2d(4, 6, 5)
        self.pool = nn.MaxPool2d(2, 2)
        self.conv2 = nn.Conv2d(6, 16, 5)
        self.fc1 = nn.Linear(16 * 5 * 5, 120)
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        x = self.pool(F.relu(self.conv1(x)))
        x = self.pool(F.relu(self.conv2(x)))
        x = x.view(-1, 16 * 5 * 5)
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x

```
这个示例中，我们将输入通道数从3改为4，以便同时处理RGBD图像。在第一个卷积层中，我们使用6个5x5的卷积核处理输入，产生6个特征图。在第二个卷积层中，我们使用16个5x5的卷积核处理6个特征图，产生16个特征图。在全连接层中，我们将16个特征图展平为一维向量，并将其输入到3个全连接层中。

另外，对于RGBD图像，还可以考虑使用3D卷积神经网络（3D CNN）来处理。3D CNN在处理视频等时间序列数据时具有良好的性能。对于RGBD图像，我们可以将RGB和深度信息沿时间轴组合起来，形成一个4D张量，然后使用3D卷积神经网络进行处理。
nvidia-smi 有信息

1.  [**Download NVIDIA CUDA Toolkit**](https://pub.towardsai.net/installing-pytorch-with-cuda-support-on-windows-10-a38b1134535e#98b9)
2.  [**Download and Install cuDNN**](https://pub.towardsai.net/installing-pytorch-with-cuda-support-on-windows-10-a38b1134535e#98b9)
3.  [**Get the driver software for the GPU**](https://pub.towardsai.net/installing-pytorch-with-cuda-support-on-windows-10-a38b1134535e#d233)
4.  [**Download Anaconda**](https://pub.towardsai.net/installing-pytorch-with-cuda-support-on-windows-10-a38b1134535e#c60e)
5.  [**Download Pycharm**](https://pub.towardsai.net/installing-pytorch-with-cuda-support-on-windows-10-a38b1134535e#d2a)


```shell
CondaHTTPError: HTTP 000 CONNECTION FAILED for url
```
[『技术随手学』解决CondaHTTPError: HTTP 000 CONNECTION 问题 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/260034241)
[(58条消息) 解决：win10下 Anaconda使用conda连接网络出现错误(CondaHTTPError: HTTP 000 CONNECTION FAILED for url）_anaconda prompt连不上网_我是如子啊的博客-CSDN博客](https://blog.csdn.net/u012961177/article/details/105808889)

failed with initial frozen solve. Retrying with flexible solve

would-pytorch-for-cuda-11-6-work-when-cuda-is-actually-12-0/169569

## 完成一个Anaconda3的Pytorch环境
```shell
(base) C:\Users\Shuo>conda info --envs
# conda environments:
#
base                  *  D:\Anaconda3
PyTorch                  D:\Anaconda3\envs\PyTorch


(base) C:\Users\Shuo>source activate PyTorch
'source' 不是内部或外部命令，也不是可运行的程序
或批处理文件。

(base) C:\Users\Shuo>activate PyTorch

(PyTorch) C:\Users\Shuo>python
Python 3.9.12 (main, Apr  4 2022, 05:22:27) [MSC v.1916 64 bit (AMD64)] :: Anaconda, Inc. on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> x = torch.rand(5,3)
>>> print(x)
tensor([[0.5061, 0.5863, 0.6718],
        [0.5575, 0.6196, 0.8931],
        [0.9293, 0.6167, 0.4019],
        [0.1210, 0.6879, 0.0146],
        [0.0827, 0.8286, 0.8701]])
>>>
>>> import torch
>>> print(torch.cuda.is_available())
True
>>>
```

## Anaconda 与 Pytorch环境

## 然后装Pycharm

在指定目录下创建新的虚拟环境，输入命令：

```bash
conda create --prefix=C:/ProgramData/Anaconda3/envs/pytorch python=3.8
```

```shell
NameError: name 'train_dataset' is not defined
```

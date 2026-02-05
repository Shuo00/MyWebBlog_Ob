Hyper-parameters   

input_size = 784  

hidden_size类似于全连接网络的结点个数
就是我们的隐藏节点（神经元）
hidden_size = 500  

input_size+hidden_size肯定等于权重参数的列数

num_class是标签中共有多少种类  
num_classes = 10  
 
epoch数量
num_epochs = 5  

BATCH_SIZE:即一次训练所抓取的数据样本数量；  
BATCH_SIZE的大小影响训练速度和模型优化。其大小同样影响每一epoch训练模型次数。  
batch_size = 100  

学习率  
learning_rate = 0.001
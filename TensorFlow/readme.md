# Content

- [TensorFlow基础](#tensorflow基础)
  * [TensorFlow的功能与特征](#tensorflow的功能与特征)
  * [TensorFlow开发环境搭建](#tensorflow开发环境搭建)
  * [TensorFlow核心编程基础](#tensorflow核心编程基础)
    + [编程模型](#编程模型)
    + [TensorFlow基础操作](#tensorflow基础操作)
    + [自动求导机制](#自动求导机制)
- [TensorFlow常用API](#tensorflow常用api)
  * [数据运算](#数据运算)
    + [tf.bitwise](#tfbitwise)
    + [tf.compat](#tfcompat)
    + [tf.dtypes](#tfdtypes)
    + [tf.linalg](#tflinalg)
    + [tf.math](#tfmath)
    + [tf.random](#tfrandom)
    + [tf.sets](#tfsets)
    + [tf.signal](#tfsignal)
    + [tf.sparse](#tfsparse)
    + [tf.strings](#tfstrings)
  * [非结构化数据处理](#非结构化数据处理)
    + [tf.audio](#tfaudio)
    + [tf.image](#tfimage)
  * [数据预处理](#数据预处理)
    + [tf.data](#tfdata)
    + [tf.feature_column](#tffeature-column)
    + [tf.nn](#tfnn)
    + [tf.ragged](#tfragged)
  * [调试部署工具](#调试部署工具)
    + [tf.debugging](#tfdebugging)
    + [tf.estimator](#tfestimator)
    + [tf.metrics](#tfmetrics)
    + [tf.distribute](#tfdistribute)
    + [tf.lite](#tflite)
    + [tf.saved_model](#tfsaved-model)
    + [tf.queue](#tfqueue)
    + [tf.summary](#tfsummary)
- [TensorFlow开发概述](#tensorflow----)
  * [TensorFlow开发流程](#tensorflow----)
    + [准备数据](#准备数据)
    + [搭建模型](#搭建模型)
    + [训练模型](#训练模型)
    + [使用模型](#使用模型)
  * [基础示例：全连接神经网络](#基础示例-全连接神经网络)
  * [进阶模型](#进阶模型)
    + [卷积神经网络](#卷积神经网络)
    + [循环神经网络](#循环神经网络)
    + [对抗神经网络](#对抗神经网络)
    + [深度强化学习](#[深度强化学习)
  * [自定义层、损失函数与评估指标](#自定义层-损失函数与评估指标)
- [TensorFlow开发实战](#tensorflow开发实战)
  * [Mnist手写数字识别](#mnist手写数字识别)
    + [网络构建](#网络构建)
    + [模型保存与加载](#模型保存与加载)
    + [可视化训练](#可视化训练)
    + [引入卷积神经网络](#引入卷积神经网络)
  * [物体检测](#物体检测)
    + [RPN](#rpn)
    + [YOLO-v3](#yolo-v3)
  * [图像分割](#图像分割)
    + [Unet](#unet)
    + [FCN](#fcn)
  * [图像生成](#图像生成)
    + [DCGAN](#dcgan)
    + [Pix2Pix](#pix2pix)
  * [强化学习](#强化学习)
    + [监督学习实战CartPole-v0游戏](#监督学习实战cartpole-v0游戏)
    + [Q-Learning实战MountainCar-v0游戏](#q-learning实战mountaincar-v0游戏)
    + [Deep Q-Learning实战MountainCar-v0游戏](#deep-q-learning实战mountaincar-v0游戏)
    + [策略梯度算法实战CartPole-v0](#策略梯度算法实战cartpole-v0)
- [TensorFlow的部署](#tensorflow的部署)
  * [TensorFlow模型导出](#tensorflow模型导出)
  * [TensorFlow Serving](#tensorflow-serving)
  * [TensorFlow Lite](#tensorflow-lite)
  * [TensorFlow in JavaScript](#tensorflow-in-javascript)








# TensorFlow基础
## TensorFlow的功能与特征

TensorFlow2.0相比TensorFlow1.x更加简单与灵活，主要特征如下：

 - 基于Keras的快速模型设计与高级控制；
 - 用于机器学习工作流的估计器api，带有用于回归、提升树和随机森林的预定义模型；
 - 基于Eager execution的命令式编程，通过AutoGraph将Python代码（转换为TensorFlow的计算图代码；
 - 支持保存Saved Model格式模型，并在其他平台部署。
 
## TensorFlow开发环境搭建
TensorFlow2.x的安装需要用Python3.x，CPU版仅需要在终端运行以下命令：

`pip install tensorflow -U`

如果要安装GPU版本，首先安装CUDA 10.0(及以上)与cndnn。然后设置LD_LIBRARY_PATH环境变量。最后通过以下命令安装：

`pip install tensorflow-gpu  -U`

安装完成后进行测试：
```python
import tensorflow as tf
tf.__version__
```
输出结果为：`'2.0.0'`

如果安装的是GPU版本，进行以下测试：

`tf.test.is_gpu_available()`

输出结果为`True`则说明安装成功。

## TensorFlow核心编程基础
### 编程模型
### TensorFlow基础操作
### 自动求导机制
 
# TensorFlow常用API
## 数据运算
### tf.bitwise
### tf.compat
### tf.dtypes
### tf.linalg
### tf.math
### tf.random
### tf.sets
### tf.signal
### tf.sparse
### tf.strings
## 非结构化数据处理
### tf.audio
### tf.image
## 数据预处理
### tf.data
### tf.feature_column
### tf.nn
### tf.ragged
## 调试部署工具
### tf.debugging
### tf.estimator
### tf.metrics
### tf.distribute
### tf.lite
### tf.saved_model
### tf.queue
### tf.summary
 
# TensorFlow开发概述
## TensorFlow开发流程
### 准备数据
### 搭建模型
### 训练模型
### 使用模型

## 基础示例：全连接神经网络

本节将通过MNIST手写数字识别为例，熟悉TensorFlow2.0的模型搭建与训练流程，主要用到以下三个核心特性：

 - tf.keras：用于深度学习模型快速原型的高级面向对象api；
 - tf.GradientTape:动态记录梯度以实现自动梯度计算和反向传播；
 - tf.function：用Autograph从python函数预编译计算图。
 
首先通过keras.datasets导入MNIST数据集，将它们预处理成784维向量（图片像素是`28*28`）。
```python
#导入必要的库
import os
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers, optimizers, datasets
#设置TensorFlow日志级别
"""
'TF_CPP_MIN_LOG_LEVEL'取值0（默认）：输出所有信息
                      取值1：屏蔽通知信息
                     取值2：屏蔽通知信息和警告信息
                     取值3：屏蔽通知信息、警告信息和报错信息
"""
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'  # or any {'0', '1', '2'}

def mnist_dateset():
    #从 tf.keras.datasets 加载需要的数据集(获取到的是numpy数据) 
     (x, y), _ = datasets.mnist.load_data()   # _ 是占位符（用作“不关心”的变量）
     ds = tf.data.Dateset.from_tensor_slices((x,y)) #使用 tf.data.Dataset.from_tensor_slices 进行加载
     ds = ds.map(prepare_mnist_features_and_labels)  #预处理 (预处理函数在下面)
     ds = ds.take(20000).shuffle(20000).batch(100)  #抽取20000数据，打乱20000数据，设置 batch size 一次喂入100个数据
     return ds
def prepare_mnist_features_and_labels(x,y):
    x = tf.cast(x, tf.float32) / 255.0  # 把numpy数据转为Tensor,并归一化
    y = tf.cast(y, tf.int64)  # 把numpy数据转为Tensor
    return x, y      
```    
数据准备好以后，基于keras.sequential进行模型构建，并从keras.optimizers中实例化一个adam优化器。
```python
model = keras.Sequential([
    layers.Reshape(target_shape=(28 * 28,), input_shape=(28, 28)),  #定义输入、输出的形状
    layers.Dense(100, activation='relu'),  #100代表kernel，这一层神经元的个数；激活函数取Relu
    layers.Dense(100, activation='relu'),
    layers.Dense(10)])

optimizer = optimizers.Adam()
```
设定好数据和模型以后，接下来对模型进行训练。这里，采用`@tf.function`的`AutoGraph`装饰器将我们的方法预编译为TensorFlow计算图。签名装饰器对于我们的代码工作来说是不必要的，但是它加快了执行速度，让我们能够利用图执行的优势，因此`@tf.function`在我们的例子中绝对值得使用。
```python
@tf.function
#损失函数的计算
def compute_loss(logits, labels):
  return tf.reduce_mean(    #tf.reduce_mean 函数用于计算张量tensor沿着指定的数轴（tensor的某一维度）上的的平均
      tf.nn.sparse_softmax_cross_entropy_with_logits(
          logits=logits, labels=labels))
#传入的logits为神经网络输出层的输出，shape为[batch_size，num_classes]
#传入的label为一个一维的vector，长度等于batch_size
#每一个值的取值区间必须是[0，num_classes)，其实每一个值就是代表了batch中对应样本的类别

@tf.function
#预测精确度的计算
def compute_accuracy(logits, labels):
  predictions = tf.argmax(logits, axis=1)
  return tf.reduce_mean(tf.cast(tf.equal(predictions, labels), tf.float32))
  
@tf.function
#训练一步的函数
def train_one_step(model, optimizer, x, y):
  with tf.GradientTape() as tape:
    logits = model(x)
    loss = compute_loss(logits, y)
  #计算梯度
  grads = tape.gradient(loss, model.trainable_variables)
  #更新权重
  optimizer.apply_gradients(zip(grads, model.trainable_variables))
  accuracy = compute_accuracy(logits, y)
  # 损失和精确度都是标量张量
  return loss, accuracy
  
#定义训练过程  
def train(epoch, model, optimizer):   #一个epoch指代所有的数据送入网络中完成一次前向计算及反向传播的过程。
  train_ds = mnist_dataset()
  loss = 0.0
  accuracy = 0.0
  for step, (x, y) in enumerate(train_ds):
    loss, accuracy = train_one_step(model, optimizer, x, y)
    if step % 500 == 0:   #每500步打印一次
      print('epoch', epoch, ': loss', loss.numpy(), '; accuracy', accuracy.numpy())
  return loss, accuracy 
```
至此已经建立了训练程序，我们可以把它循环起来，开始训练。
```python
for epoch in range(20):   #将所有数据迭代训练一次是不够的，需要反复多次才能拟合收敛。
  loss, accuracy = train(epoch, model, optimizer)
print('Final epoch', epoch, ': loss', loss.numpy(), '; accuracy', accuracy.numpy())
```


## 进阶模型
### 卷积神经网络
### 循环神经网络
### 对抗神经网络
### 深度强化学习
## 自定义层、损失函数与评估指标
 
# TensorFlow开发实战
## Mnist手写数字识别
### 网络构建
### 模型保存与加载
### 可视化训练
### 引入卷积神经网络
## 物体检测
### RPN
### YOLO-v3
## 图像分割
### Unet
### FCN
## 图像生成
### DCGAN
### Pix2Pix
## 强化学习
### 监督学习实战CartPole-v0游戏
### Q-Learning实战MountainCar-v0游戏
### Deep Q-Learning实战MountainCar-v0游戏
### 策略梯度算法实战CartPole-v0
 
# TensorFlow的部署
## TensorFlow模型导出
## TensorFlow Serving
## TensorFlow Lite
## TensorFlow in JavaScript

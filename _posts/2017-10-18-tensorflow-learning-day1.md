---
layout: post
title: Tensorflow学习笔记(一):入门
date: 2017-10-18
tags:
- tensorflow
- 深度学习
categories: 
- tensorflow
description: 正在学习Tensorflow，想做一些笔记，会定期更新。
---
## 前言
关于Tensorflow的安装，这里不再累赘，Tensorflow目前已经支持了Python，C++，java等多种语言的接口，这个笔记是再python的环境下使用tensorflow的，学习的资源也是主要来自官方的文档教程，所以你也可以直接去看官方的文档。我做这个笔记的目的有三个：1.官方的文档是英文的，因此想做成简化版的中文教程，方便以后阅读。2.好记性不如烂笔头，做些笔记应该能加深印象。3.对官方的文档做一些比较好理解的逻辑归类，并记录自己的理解。
## 编程环境
* Tensoflow我装的是CPU版本的，版本是1.3
* python3.5(使用Anaconda)
* window下和linux都可以
## Tensorflow的hello world
在学习一门新的编程语言时，我们都习惯先打印出`hello world`来表示“入门”，tensorflow也不例外。
```
import tensorflow as tf
hello=tf.constant('hello world')
sess=tf.Session()
print(sess.run(hello))
```
## 用Tensorflow求解简单的拟合问题
```python
import tensorflow as tf
import numpy as np

#使用 NumPy 生成假数据(phony data), 总共 100 个点.
x_data = np.float32(np.random.rand(2, 100))  # 随机输入
y_data = np.dot([0.100, 0.200], x_data) + 0.300

#构造一个线性模型
b = tf.Variable(tf.zeros([1]))
W = tf.Variable(tf.random_uniform([1, 2], -1.0, 1.0))
y = tf.matmul(W, x_data) + b

#最小化方差
loss = tf.reduce_mean(tf.square(y - y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

#初始化变量
init = tf.global_variables_initializer()

#启动图 (graph)
sess = tf.Session()
sess.run(init)

#拟合平面
for step in range(0, 201):
    sess.run(train)
    if step % 20 == 0:
        print(step, sess.run(W), sess.run(b))
print('W:' + str(sess.run(W)) + '\tb' + str(sess.run(b)))
```
结果如下：
|epoch  |          W                 |      b      |
|-------|----------------------------|-------------|
|0      |[[ 0.0816893   0.74690914]] |[ 0.03610746]|
|20     |[[ 0.09405872  0.36626741]] |[ 0.21660915]|
|40     |[[ 0.09842868  0.25089166]] |[ 0.27433687]|
|60     |[[ 0.0995898   0.21557841]] |[ 0.29210457]|
|80     |[[ 0.09989469  0.20476907]] |[ 0.2975716] |
|100    |[[ 0.09997357  0.20146006]] |[ 0.29925328]|
|120    |[[ 0.09999356  0.20044702]] |[ 0.29977044]|
|140    |[[ 0.09999852  0.2001369 ]] |[ 0.29992944]|
|160    |[[ 0.09999969  0.20004191]] |[ 0.29997832]|
|180    |[[ 0.09999994  0.20001282]] |[ 0.29999334]|
|200    |[[ 0.1         0.20000391]] |[ 0.29999796]|

可见最后得到的结果是很接近真实的W和b。















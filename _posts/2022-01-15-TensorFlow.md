---
title: Tensorflow实战
tags: 深度学习
mathjax: true
mode: immersive
comment: true
pageview: true
key: A0005
header:
  theme: dark
article_header:
  type: cover
  image:
    src: /men1.jpg

---

* content
  
  {:toc}

# Tensorflow

## Tensorflow介绍

TensorFlow是由谷歌大脑团队基于谷歌内部第一代深度学习系统DistBelief改进而来的通用计算框架。DistBelief是谷歌2011年开发的内部深度学习工具，且在谷歌内部取得了巨大成功。随谈DistBelief已经被谷歌内部很多产品使用，但由于其过度依赖谷歌内部的系统架构，很难对外开源，所以谷歌大脑团队对它进行了改进，并在2015年正式公布了基于Apache2.0开源协议计算框架TensorFlow。相比于DistBelief，TensorFlow的计算模型更加通用、计算更快、支持的平台更多、支持的深度学习算法更广且系统的稳定性也更高。

## 环境搭建

TensorFlow依赖两个主要的工具包——Protocol Buffer 和 Bazel，当然也不仅限于这两个（这两个是作者认为比较重要的）

### 安装

conda环境安装：

```
conda install -c anaconda tensorflow
```

## 入门

### 计算图

> 计算图是TensorFlow最基本的一个概念，它定义了计算。但它不计算任何东西，也不包含任何值，它只是定义您在代码中指定的操作。TensorFlow中的所有计算都会被转化为图上的节点。

TensorFlow中Tensor是张量，Flow是流，张量可以理解为多维数组，流表达了张量之间通过计算相互转化的过程。

### 张量

> 张量是TensorFlow管理数据的形式

在TensorFlow中，所有数据都通过中张量的形式来表示，其中零阶张量表示标量（scalar），也就是一个数字，第一阶张量为向量（vector），也就是一维数组，第n阶张量可以理解为n维数组，但张量在TensorFlow中的实现不是采用数组的形式，只是对TensorFlow中运算结果的引用。张量中没有真正保存数字，它保存的是如何得到这些数字的过程。

### 会话

>  回话拥有并管理TensorFlow程序运行时的所有资源，它允许执行图形或部分图形。它为此分配资源（在一台或多台机器上）并保存中间结果和变量的实际值。

TensorFlow种实用会话的模式一般有两种，第一种需要明确调用回话生成函数和关闭会话函数，流程为

```python
#创建一个会话
sess = tf.Session()
# 使用这个创建好的会话来得到关心的运算的结果，比如可以调用sess.run(result)
#来得到张量result的取值
sess.run(...)
#关闭会话是本次运行中使用到的资源可以被释放
sess.close()
```

因为这本书是基于TF1.0，而TF2 默认运行 Eager Execution，因此不再需要 Session。如果要运行静态图，更合适的方法是`tf.function()`在 TF2 中使用。虽然 Session 仍然可以`tf.compat.v1.Session()`在 TF2 中访问，但并不推荐。

这里列出TF1.x和TF2.x hello world！的区别

TF1.x：

```python
import tensorflow as tf
msg = tf.constant('Hello, TensorFlow!')
sess = tf.Session()
print(sess.run(msg))
```

TF2.x

```python
import tensorflow as tf
msg = tf.constant('Hello, TensorFlow!')
tf.print(msg)
```


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

> 计算图是TensorFlow最基本的一个概念，TensorFlow中的所有计算都会被转化为图上的节点。

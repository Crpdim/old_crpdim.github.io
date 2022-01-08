---
title: softmax回归
tags: 深度学习
mathjax: true
mode: immersive
comment: true
pageview: true
key: A0003
header:
  theme: dark
article_header:
  type: cover
  image:
    src: /City.jpg

---


* content
{:toc}




# Softmax回归

> 线性回归适用于输出为连续值的场景，在需要输出像图像类别的离散值时，可以采用softmax回归在内的分类模型。不同于线性回归，softmax回归的输出单元是多个离散值，且引入了softmax运算，使输出更适合离散值的预测和训练。

## softmax回归模型：

softmax回归跟线性回归一样将输入特征与权重做线性叠加。与线性回归的一个主要不同在于，softmax回归的输出值个数等于标签里的类别数。

对于输入数据![[公式]](https://www.zhihu.com/equation?tex=%5C%7B%28x_1%2Cy_1%29%2C%28x_2%2Cy_2%29%2C%5Cldots%2C%28x_m%2Cy_m%29%5C%7D)有 ![[公式]](https://www.zhihu.com/equation?tex=k) 个类别，即![[公式]](https://www.zhihu.com/equation?tex=y_i+%5Cin+%5C%7B1%2C2%2C%5Cldots%2Ck%5C%7D)，那么 softmax 回归主要估算输入数据 ![[公式]](https://www.zhihu.com/equation?tex=x_i) 归属于每一类的概率，即

![[公式]](https://www.zhihu.com/equation?tex=h_%7B%5Ctheta%7D%5Cleft%28x_i%5Cright%29%3D%5Cleft%5B%5Cbegin%7Barray%7D%7Bc%7D%7Bp%5Cleft%28y_i%3D1+%7C+x_i+%3B+%5Ctheta%5Cright%29%7D+%5C%5C+%7Bp%5Cleft%28y_i%3D2+%7C+x_i+%3B+%5Ctheta%5Cright%29%7D+%5C%5C+%7B%5Cvdots%7D+%5C%5C+%7Bp%5Cleft%28y_i%3Dk+%7C+x_i+%3B+%5Ctheta%5Cright%29%7D%5Cend%7Barray%7D%5Cright%5D%3D%5Cfrac%7B1%7D%7B%5Csum_%7Bj%3D1%7D%5E%7Bk%7D+e%5E%7B%5Ctheta_%7Bj%7D%5E%7BT%7D+x_i%7D%7D%5Cleft%5B%5Cbegin%7Barray%7D%7Bc%7D%7Be%5E%7B%5Ctheta_%7B1%7D%5E%7BT%7D+x_i%7D%7D+%5C%5C+%7Be%5E%7B%5Ctheta_%7B2%7D%5E%7BT%7D+x_i%7D%7D+%5C%5C+%7B%5Cvdots%7D+%5C%5C+%7Be%5E%7B%5Ctheta_%7Bk%7D%5E%7BT%7D+x_i%7D%7D%5Cend%7Barray%7D%5Cright%5D%5Ctag%7B1%7D+%5C%5C)

其中，![[公式]](https://www.zhihu.com/equation?tex=%5Ctheta_1%2C%5Ctheta_2%2C%5Cldots%2C%5Ctheta_k+%5Cin+%5Ctheta)是模型的参数，乘以![[公式]](https://www.zhihu.com/equation?tex=%5Cfrac%7B1%7D%7B%5Csum_%7Bj%3D1%7D%5E%7Bk%7D+e%5E%7B%5Ctheta_%7Bj%7D%5E%7BT%7D+x_i%7D%7D)是为了让概率位于[0,1]并且概率之和为 1，softmax 回归将输入数据 ![[公式]](https://www.zhihu.com/equation?tex=x_i) 归属于类别 ![[公式]](https://www.zhihu.com/equation?tex=j) 的概率为

![[公式]](https://www.zhihu.com/equation?tex=p%5Cleft%28y_i%3Dj+%7C+x_i+%3B+%5Ctheta%5Cright%29%3D%5Cfrac%7Be%5E%7B%5Ctheta_%7Bj%7D%5E%7BT%7D+x_i%7D%7D%7B%5Csum_%7Bl%3D1%7D%5E%7Bk%7D+e%5E%7B%5Ctheta_%7Bl%7D%5E%7BT%7D+x_i%7D%7D%5Ctag%7B2%7D+%5C%5C)


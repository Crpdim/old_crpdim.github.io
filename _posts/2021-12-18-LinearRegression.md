---
title: 线性回归
tags: 深度学习
mathjax: true
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---


* content
{:toc}
# 线性回归

>  回归是求回归系数的过程

## 用线性回归找到最佳拟合直线

#### 原理

回归目的是预测数值型的目标值，最直接的办法就是输入写出一个目标值的计算公式。也就是所谓的回归方程。

将输入的数据存放在矩阵X中，回归系数存放在w中，对于给定的数据X1，预测结果Y<sub>1</sub> = X<sup>T</sup><sub>1</sub> ·w，所以为了找到所以给出一些x，y，就是为了寻找使误差最小的w。在这里可以采用平方误差,平方误差可以写为：
$$
\sum_{i=1}^m(y_i - x^T_iw)^2
$$
用矩阵可以写作：（y-Xw)<sup>T</sup>(y-Xw). 如果对w求导,得到X<sup>T</sup>(Y-Xw),使其等于0,解得 
$$
\hat{w} = (X^TX)^{-1} X^Ty
$$
此时可以得到w最优解.

#### 代码实现:

```python
from numpy import * 
def loadDataSet(filename):     #数据导入函数:打开一个tab键分隔的文本文件
    numFeat = len(open(filename).readline().split('\t'))-1 
    dataMat = []
    labelMat = []
    fr = open(filename)
    for line in fr.readlines():
        lineArr = []
        curLine = line.strip().split('\t')
        for i in range(numFeat):
            lineArr.append(float(curLine[i]))
        dataMat.append(lineArr)
        labelMat.append(float(curLine[-1]))
    return dataMat,labelMat
def standRegres(xArr,yArr):     #标准回归函数:计算最佳拟合直线
    xMat = mat(xArr)            #mat将数组转换为矩阵，才可以进行线代操作
    yMat = mat(yArr).T
    xTx = xMat.T * xMat 
    if (linalg.det(xTx)) == 0.0:#计算行列式
        print("行列式为0")
        return
    ws = xTx.I * (xMat.T*yMat)  #.I表示求逆
    # ws = linalg.solve(xTx,xMat.T*yMat) #numpy线代库中的解位置矩阵的函数，可以替换上一句
    return ws
```

使用样例:

```python
import regression
from numpy import *
xArr,yArr = regression.loadDataSet("ex0.txt")
ws = regression.standRegres(xArr,yArr) #ws为回归系数
xMat = mat(xArr)
yMat = mat(yArr)
yHat = xMat*ws 
import matplotlib.pyplot as plt
fig = plt.figure()
ax = fig.add_subplot(111)
ax.scatter(xMat[:,1].flatten().A[0],yMat.T[:,0].flatten().A[0])
xCopy = xMat.copy()
xCopy.sort(0)
yHat = xCopy*ws
ax.plot(xCopy[:,1],yHat)
plt.show()
```



便得到了最佳拟合直线

## 局部加权线性回归

线性回归的一个问题是有可能出现欠拟合现象，因为他求得是具有最小均方差的无偏估计。


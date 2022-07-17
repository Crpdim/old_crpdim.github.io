---
title: python命名规范
tags: python
mathjax: true
mode: immersive
comment: true
pageview: true
key: A2277
header:
  theme: dark
article_header:
  type: cover
  image:
    src: //photos/mounts.jpg




---


* content
{:toc}






# Python变量命名规范

## 1. 不要与内置函数取同样名

## 2. 文件不要与内置module同名

## 3. 规范

### 小写下划线（ it_is_a_name )

除常量和类，其他地方都使用小写字母加下划线

#### 大写下划线  ( IT_IS_A_NAME )

表示常量

#### 驼峰命名 ( ItIsAName )

表示类名

### 前置下划线 

###### 单下划线 (_name)

弱私有，有好的告诉别人不要使用

`  import *`不会引入单下划线变量

###### class definition中双下划线 (__name)

强私有命名，无法从class外访问变量名，但仍然不安全

`  python执行时会将双下划线变量改为： 类名__变量`

###### 前后双下划线 (__name__)

表示Python中魔术方法（不要用）

### 尾部下划线 （class_）

避免与Python关键字冲突

### 单个下划线 （ _ )

表示不使用的变量 

```python
for _ in range(10):
```




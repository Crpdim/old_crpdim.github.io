---
title: RobotFramework框架
tags: 测试框架
mathjax: true
mode: immersive
comment: true
pageview: true
key: A0002
header:
  theme: dark
article_header:
  type: cover
  image:
    src: /Apple_Park.png
---

* content
  {:toc}

# Robot Framework

>  Robot Framework是一款python编写的功能自动化测试框架。具备良好的可扩展性，支持关键字驱动，可以同时测试多种类型的客户端或者接口，可以进行分布式测试执行。主要用于轮次很多的验收测试和验收测试驱动开发（ATDD）。

## 高层架构

Robot Framework 是一个通用的、独立于应用程序和技术的框架。它具有高度模块化的架构，如下图所示。

![src/GettingStarted/architecture.png](https://robotframework.org/robotframework/latest/images/architecture.png)

## 特点：

- 入门快（门槛低）：对于编程能力比较薄弱的测试人员也能快速入手
- 丰富的开源库包支持：大家都知道Selenium自动化只能在web下进行，而Robot Framework几乎可以在任何测试场景下使用（导入相应的扩展包）

## 安装

直接 `pip install robotframework-ride`就ok了

## 浏览器打开测试

进入python环境的Scrips目录，运行`python ride.py`,就可以打开程序窗口，点击窗口菜单栏的File中的New Project即可创建一个Project，创建新项目的方法和其他软件大同小异。

在左边的Test Suites窗口中可以看到创建的第一个项目，右键该项目，点击New Suite，创建一个Suite，再在Suite中创建第一个测试。

分别在project和suite中导入测试需要的库（表格中库的名称为红色时，说明导入失败，没有找到该库）：

![](https://github.com/Crpdim/crpdim.github.io/raw/main/screenshots/page1.png)

向表格里写入第一个脚本：

![](https://github.com/Crpdim/crpdim.github.io/raw/main/screenshots/project1.png)

> 1. 使用Chrome访问Url
> 2. 等待5s
> 3. 最大化浏览器窗口
> 4. 向id=user的文本框输入123
> 5. 剩下的同理。。。

接下来进入run页面，点击Start按钮或按F8 便可以执行脚本，并生成测试报告。（*使用RobotFramework打开谷歌浏览器需要安装**对应版本**的chromedriver.exe，其他浏览器同理。）

![](https://github.com/Crpdim/crpdim.github.io/raw/main/screenshots/result.png)

点击report查看测试报告

![](https://github.com/Crpdim/crpdim.github.io/raw/main/screenshots/report.png)

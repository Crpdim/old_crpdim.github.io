# CSS浮动&盒子

> 让块级标签不独占一行，把块级标签元素可以排在同一行。

## 浮动

让元素脱离文档流，不占用标准流

### float属性值

* left
* right
* none：默认值（不浮动），可以取消浮动

### 浮动问题：

浮动后，后面的元素不会显示在下一行

### 清除浮动

目的：让后面的元素自动掉到下一行

方法（一般使用第二种）：

1. 添加空标签，设置样式：clear:both;

   clear:left;清除左浮动

   clear:right;清除右浮动

   clear:both;清除左右浮动

   clear:none;都不清除

2. 在需要清除浮动的父级添加样式：overflow:hidden

   overflow:hidden; 超出部分隐藏，可以实现清除浮动

3. 添加伪元素after，并设定样式：

   .父元素:after {

   content:"";

   display:block;

   clear:both;

   }

## CSS盒子模型

每个元素都是一个盒子，由margin外边距，border边框线，padding内边距，content内容组成

### display ：设置元素显示方式

属性值：

* none：不显示
* block：块显示，将行级标签转换为块显示
* inline：行显示，将块级标签转换为行显示
* inline：行或块转为行内块
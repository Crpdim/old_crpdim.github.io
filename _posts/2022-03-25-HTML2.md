# CSS 层叠样式表

> html表达内容结构，css表达样式美化网页，做到结构（html）表现（css）分离

## 语法：

​	选择器 {

​		属性:属性值;

}

## 引用方式：

* 行间样式：直接在标签上书写样式

* 内部样式：在文件内部书写样式

  ```html
  <style>
  	样式内容
  </style>
  ```

* 外部样式：先创建css文件，在用link标签引入这个文件

  ```html
  <link rel="stylesheet" href="style.css">
  ```

* 导入外部样式 ：先创建css文件，在style标签中import导入样式文件。

  ```html
  <style>
  	 @import "test.css";
  </style>
  ```

#### 区别：

行间样式只作用于当前标签，内部样式作用于当前文件，外部样式可以被多个html文件引用

实际项目开发中，最多使用外部样式

link引入和import引入，这两种方式区别：

* link除了加载css外还可以定义其他事务，@import只能加载css
* **link引入css时在页面载入时同时加载（异步加载），而@import需要网页完全载入后加载**
* link是xhtml标签，无兼容问题，@import在css2.1提出，低版本浏览器不支持
* **link支持使用javascript控制DOM改变样式，@import不支持**

## 选择器分类

1. *：匹配html中所有元素 （慎用 *性能非常差，因为他需要匹配所有元素）

2. 标签选择器：匹配标签

   ```html
   span {
   		display: block;
   }
   ```

3. 类选择器：用来匹配class命名的标签

   ```html
   .lab {
   	color: aqua;
   }
   ```

   

4. id选择器： 选择用id命名标签

   ```html
   #name {
   	color: pink;
   }
   ```

5. 排除选择器：根据上下文选择标签

   ```html
   .lab li {
   	color: chartreuse;
   
   }
   ```

6. 伪类选择器

   伪类：专门表示元素的一种特殊状态

   常用伪类选择题：

   1. a标签：

   ​		a:visited已被访问 a:link 未被访问 a:hover 鼠标悬停 a:active 用户激活

   	2. :focus 获得焦点
   	2. :first-child/ :last-child 

## 选择器分组

> 多个选择器具有相同样式，一般用于设置公共样式

## 选择器继承

> 子元素可以继承父元素内容

## 优先级

外部样式<内部样式<内部样式<内联样式

样式权重：!import 10000 > 内联样式 1000> id选择器10 > 类、伪类1

## 字体

### 属性

* font-size px像素 %基于父元素
* font-family 字体 包含空格必须用引号
* font-style 样式 normal常规 italic斜体 oblique倾斜的字体
* font-weight 加粗 normal默认，bold 粗 bolder更粗 lighter细 100-900由细到粗
* line-height 行高normal常规，20px像素，1.5文字大小
* color 
* text-decoration 修饰（上下划线）
* text-align 对其方式
* text-transform 字母大小写 none默认，capitalize将每个单词第一个字母转换成大写，uppercase全转换成大写 lowercase 转换成小写
* test-indent 首行缩进，20px缩进像素 2em缩进几个字符

### CSS背景

1. background-color 
2. background-image
3. background-repeat：背景图片铺排方式
4. background-position:背景图像位置
5. background-attachment背景图像滚动样式 scroll随页面其余部分滚动，fixed背景图像不移动
6. background 复合属性

## 属性选择器

「属性名称」：包含置顶属性名元素

「属性名=值」：属性名的值为指定值的元素

「属性名~=值」：属性名的值包含指定值的元素

「属性名^=值」：属性名的值以指定值开头的元素

「属性名$=值」：属性名的值以指定值结尾的元素

## 关系选择器

#### 后代选择器

1. 空格：后代选择器
2. 大于符号：只选择儿子元素
3. 加号：兄弟选择器

## CSS伪元素

> 伪类和伪元素是为了修饰不在文档树中的部分

伪类用于当已有元素处于某种状态时，为其添加对应的样式，这状态根据用户行为动态变化

伪元素用于创建一些不存在文档数中的元素，并为其添加样式。伪元素无法被选中

* :before/:after/:first-letter/:first-line 可以一个冒号或两个
* ::selection/::placeholder/::backdrop 前面只能双冒号。
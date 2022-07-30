---
title: 层次遍历应用
tags: 数据结构
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


# 层次遍历应用

## 获取树的高度

### 流程图

![](https://github.com/Crpdim/crpdim.github.io/raw/main/get_max_level.png)

### 代码实现

```c
int get_depth(Tree root) {
    if (!root) return 0;
    queue<Node*>Q;
    Q.push(root);
    int level = 0;
    Node* temp;
    Node *rear = root;
    Node *last = root;
    while (!Q.empty()) {
        temp = Q.front();
        Q.pop();
        if (temp->left) {
            Q.push(temp->left);
            rear = temp->left;
        }
        if (temp->right) {
            Q.push(temp->right);
            rear = temp->right;
        }
        if (temp == last) {
            ++level;
            last = rear;
        }
    }
    return level;
}
```



## 获取树的最大宽度

### 流程图

![](https://github.com/Crpdim/crpdim.github.io/raw/main/get_max_width.png)

### 代码实现

```c
int get_Width(Tree root) {
    if (!root) return 0;
    queue<Node*> Q;
    Q.push(root);
    int level = 0;
    Node *temp;                     //指向队首本次循环中出队的元素
    Node *rear = root;              //指向最后入队的元素
    Node *last = root;              //指向每层最后一个元素
    int width = 0, maxwidth = 0;
    while (!Q.empty()) {
        temp = Q.front();
        Q.pop();
        width += 1;
        if (temp->left) {
            Q.push(temp->left);
            rear = temp->left;
        }
        if (temp->right) {
            Q.push(temp->right);
            rear = temp->right;
        } 
        if (temp == last) {
            level++;
            maxwidth = maxwidth > width? maxwidth: width;
            width = 0;
            cout << last->data << endl;
            last = rear;
        }
    }
   
```





# 
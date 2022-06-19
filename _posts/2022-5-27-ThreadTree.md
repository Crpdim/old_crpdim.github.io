---
title: 线索二叉树
tags: 数据结构
mathjax: true
mode: immersive
comment: true
pageview: true
key: A0021
header:
  theme: dark
article_header:
  type: cover
  image:
    src: /escape.jpg

---


* content
{:toc}


# ThreadTree(C语言实现)

## 节点定义

```c
typedef struct ThreadNode {
    char val;
    int l_tag, r_tag;
    struct ThreadNode* left, *right;
}ThreadNode, *ThreadTree;
```

## 二叉树建立

```c
void creatTree(ThreadTree* t) {         //二叉树建立
    char c;
    scanf("%c", &c);
    if (c != '#') {
        (*t) = (ThreadTree)malloc(sizeof (ThreadNode));
        (*t)->val = c;
        (*t)->l_tag = 0;
        (*t)->r_tag = 0;
        creatTree(&(*t)->left);
        creatTree(&(*t)->right);
    } else {
        (*t) = NULL;
    }
}
```

## 先序线索化

```c
void PreThread(ThreadTree *tree) {
    if ((*tree) == NULL) return;
    ThreadNode *temp = (*tree);
    if (temp->left == NULL) {
        temp->left = pre;
        temp->l_tag = 1;
    }
    if (pre != NULL && pre->right == NULL) {
        pre->right = temp;
        pre->r_tag = 1;
    }
    pre = temp;
    if (temp->l_tag == 0)
        PreThread(&(temp->left));
    if (temp->r_tag == 0)
        PreThread(&(temp->right));
}

void creatPreThread(ThreadTree *tree) {     //建立先序线索二叉树
    PreThread(tree);
    pre->right = NULL;
    pre->r_tag = 1;
}
```

### 先序线索后继节点

```c
ThreadNode *Pre_NextNode(ThreadNode *node) { //先序线索二叉树找后继
    if (node->l_tag == 0) {
        return node->left;
    }
    return node->right;
}   //先序遍历找后继
```

### 先序线索二叉树先序遍历

```c
void T_PreOrder(ThreadTree *tree) {         //先序线索二叉树先序遍历
    ThreadNode *vis = (*tree);
    printf("先序线索二叉树的先序遍历\n");
    while (vis != NULL) {
        printf("%c ", vis->val);
        vis = Pre_NextNode(vis);
    }
    printf("\n");
}   //先序线索二叉树先序遍历
```



## 中序线索化

```c
ThreadNode* pre = NULL;
void InTherad(ThreadTree* tree) {
    if ((*tree) == NULL) return;
    InTherad(&(*tree)->left);
    if ((*tree)->left == NULL) {
        (*tree)->left = pre;
        (*tree)->l_tag = 1;
    }
    if (pre != NULL && pre->right == NULL) {
        pre->right = (*tree);
        pre->r_tag = 1;
    }
    pre = (*tree);
    InTherad(&(*tree)->right);
}

void creatInTherad(ThreadTree* tree) {  //中序线索化
    InTherad(tree);
    pre->right = NULL;
    pre->r_tag = 1;
}
```

### 寻找后继节点

```c
ThreadNode *FirstNode(ThreadTree* tree) {   //寻找树中序遍历首节点
    ThreadNode* vis = (*tree);
    while (vis->l_tag == 0) vis = vis->left;
    return vis;
}

ThreadNode *NextNode(ThreadNode* node) {    //寻找后继节点
    if (node->r_tag == 0) return FirstNode(&(node->right));
    return node->right;
}
```

### 利用线索二叉树中序遍历

```c
void T_Inorder(ThreadTree *tree) {      //使用线索二叉树中序遍历
    printf("线索二叉树正序中序遍历\n");
    ThreadNode* vis = FirstNode(tree);
    while (vis != NULL) {
        printf("%c ", vis->val);
        vis = NextNode(vis);
    }
    printf("\n");
}
```

### 寻找前驱节点

```c
ThreadNode *LastNode(ThreadTree* tree) {    //线索二叉树最后一个节点
    ThreadNode *vis = (*tree);
    while (vis->r_tag == 0) vis = vis->right;
    return vis;
}

ThreadNode *PreNode(ThreadNode* node) {     //线索二叉树前驱节点
    if (node->l_tag == 0) return LastNode(&(node->left));
    return node->left;
}
```

### 逆序中序遍历二叉搜索树

```c
void revInOrder(ThreadTree* tree) {     //逆序中序遍历
    printf("线索二叉树逆序中序遍历\n");
    ThreadNode *vis = LastNode(tree);
    while (vis != NULL) {
        printf("%c ", vis->val);
        vis = PreNode(vis);
    }
    printf("\n");
}
```

## 主函数

```c
int main() {
    ThreadTree tree;
    creatTree(&tree);
    creatInTherad(&tree);
    T_Inorder(&tree);
    revInOrder(&tree);
    return  0;
}

//测试样例
/*
ABD#G##E##CF###
线索二叉树正序中序遍历
D G B E A F C 
线索二叉树逆序中序遍历
C F A E B G D 
*/
```


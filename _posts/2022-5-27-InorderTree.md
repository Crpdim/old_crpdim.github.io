# InorderTree(C语言实现)

## 节点定义

```c
typedef struct BTNode {
    char val;
    int l_tag, r_tag;
    struct BTNode* left, *right;
}BTNode, *BTTree;
```

## 二叉树建立

```c
void creatTree(BTTree* t) {         //二叉树建立
    char c;
    scanf("%c", &c);
    if (c != '#') {
        (*t) = (BTTree)malloc(sizeof (BTNode));
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

## 中序线索化

```c
void InTherad(BTTree* tree) {
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

void creatInTherad(BTTree* tree) {  //中序线索化
    InTherad(tree);
    pre->right = NULL;
    pre->r_tag = 1;
}
```

## 寻找后继节点

```c
BTNode *FirstNode(BTTree* tree) {   //寻找树中序遍历首节点
    BTNode* vis = (*tree);
    while (vis->l_tag == 0) vis = vis->left;
    return vis;
}

BTNode *NextNode(BTNode* node) {    //寻找后继节点
    if (node->r_tag == 0) return FirstNode(&(node->right));
    return node->right;
}
```

## 利用线索二叉树中序遍历

```c
void T_Inorder(BTTree *tree) {      //使用线索二叉树中序遍历
    printf("线索二叉树正序中序遍历\n");
    BTNode* vis = FirstNode(tree);
    while (vis != NULL) {
        printf("%c ", vis->val);
        vis = NextNode(vis);
    }
    printf("\n");
}
```

## 寻找前驱节点

```c
BTNode *LastNode(BTTree* tree) {    //线索二叉树最后一个节点
    BTNode *vis = (*tree);
    while (vis->r_tag == 0) vis = vis->right;
    return vis;
}

BTNode *PreNode(BTNode* node) {     //线索二叉树前驱节点
    if (node->l_tag == 0) return LastNode(&(node->left));
    return node->left;
}
```

## 逆序中序遍历二叉搜索树

```c
void revInOrder(BTTree* tree) {     //逆序中序遍历
    printf("线索二叉树逆序中序遍历\n");
    BTNode *vis = LastNode(tree);
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
    BTTree tree;    //Node指针
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


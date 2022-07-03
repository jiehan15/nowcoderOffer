# JZ27 二叉树的镜像

操作给定的二叉树，将其变换为源二叉树的镜像。

```c
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param pRoot TreeNode类 
 * @return TreeNode类
 */
struct TreeNode* Mirror(struct TreeNode* pRoot ) {
    // write code here
    
    if(pRoot == NULL) return NULL; 
    
    struct TreeNode* tmp = NULL;
    
    tmp = pRoot->left; 
    pRoot->left = pRoot->right; 
    pRoot->right = tmp; 
    
    // no need for return value here 
    Mirror(pRoot->left);
    Mirror(pRoot->right);
    
    return pRoot;
}
```

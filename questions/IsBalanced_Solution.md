# JZ79 判断是不是平衡二叉树

输入一棵节点数为 n 二叉树，判断该二叉树是否是平衡二叉树。  
在这里，我们只需要考虑其平衡性，不需要考虑其是不是排序二叉树  
平衡二叉树（Balanced Binary Tree），具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。  

思路：利用之前求树的深度的代码，若左右子树深度差值超过1，则不为平衡二叉树。

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
 * 
 * @param pRoot TreeNode类 
 * @return bool布尔型
 */

static bool isBalanced = true; 

int TreeDepth(struct TreeNode* pRoot){
    if(pRoot == NULL) return 0; 
    
    int leftDepth; 
    int rightDepth; 
    int depth; 
    int depthDiff;
    
    leftDepth = TreeDepth(pRoot->left);
    rightDepth = TreeDepth(pRoot->right); 
    
    // 当某个子树为非平衡二叉树时提前返回
    if(leftDepth == -1) return -1; 
    else if(rightDepth == -1) return -1; 
    
    // 求子树深度差值
    depthDiff = leftDepth > rightDepth ? (leftDepth-rightDepth) : (rightDepth-leftDepth);
    if(depthDiff > 1) {
        // 不是平衡二叉树
        isBalanced = false; 
        return -1; 
    } else {
        // 子树是平衡二叉树，返回当前节点深度
        depth = leftDepth > rightDepth ? (leftDepth+1) : (rightDepth+1);
        return depth;
    }
}

bool IsBalanced_Solution(struct TreeNode* pRoot ) {
    // write code here
    if(pRoot == NULL) return true; 
    TreeDepth(pRoot);
    return isBalanced; 
}
```

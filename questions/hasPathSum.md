# JZ82 二叉树中和为某一值的路径(一)

给定一个二叉树root和一个值 sum ，判断是否有从根节点到叶子节点的节点值之和等于 sum 的路径。  
1.该题路径定义为从树的根结点开始往下一直到叶子结点所经过的结点  
2.叶子节点是指没有子节点的节点  
3.路径只能从父节点到子节点，不能从子节点到父节点  
4.总节点数目为n  

```c
/**
 * struct TreeNode {
 *	int val;
 *	struct TreeNode *left;
 *	struct TreeNode *right;
 * };
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param root TreeNode类 
 * @param sum int整型 
 * @return bool布尔型
 */
bool hasPathSum(struct TreeNode* root, int sum ) {
    // write code here
    if(root == NULL)
        return false;
    sum = sum - root->val;
    if(sum == 0 && root->left == NULL && root->right == NULL)
        return true;
    return hasPathSum(root->left, sum) || hasPathSum(root->right, sum);
}
```

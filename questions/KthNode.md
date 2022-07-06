# JZ54 二叉搜索树的第k个节点

给定一棵结点数为n 二叉搜索树，请找出其中的第 k 小的TreeNode结点值。  
1.返回第k小的节点值即可  
2.不能查找的情况，如二叉树为空，则返回-1，或者k大于n等等，也返回-1  
3.**保证n个节点的值不一样**  

要求时间复杂度为O(n)
深度优先

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
 * @param proot TreeNode类 
 * @param k int整型 
 * @return int整型
 */
int KthNode(struct TreeNode* proot, int k ) {
    // write code here
    // empty tree 
    if(proot == NULL) return -1;
    
    struct TreeNode* stack[1001] = {NULL};
    struct TreeNode* tmp = proot; 
    int sptr = 0; 
    
    int count = 0;
    // find the left most elment (smallest)
    while(sptr || tmp != NULL){
        while(tmp != NULL){
            stack[sptr++] = tmp;
            tmp = tmp->left;
        }
        // pop the top element 
        sptr--;
        count++;
        if(count == k) return stack[sptr]->val;
        
        tmp = stack[sptr]->right;
    }
    
    return -1;
}
```

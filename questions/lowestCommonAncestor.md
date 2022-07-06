# JZ68 二叉搜索树的最近公共祖先

给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。  
1.对于该题的最近的公共祖先定义:对于有根树T的两个节点p、q，最近公共祖先LCA(T,p,q)表示一个节点x，满足x是p和q的祖先且x的深度尽可能大。在这里，一个节点也可以是它自己的祖先.  
2.二叉搜索树是若它的左子树不空，则左子树上所有节点的值均小于它的根节点的值； 若它的右子树不空，则右子树上所有节点的值均大于它的根节点的值  
3.所有节点的值都是唯一的。  
4.p、q 为不同节点且均存在于给定的二叉搜索树中。  
数据范围:  
3<=节点总数<=10000  
0<=节点值<=10000  

`int lowestCommonAncestor(struct TreeNode* root, int p, int q )`

因为是二叉搜索树，在遍历过程中比较左右节点和p q的大小，并把路径加入栈中。最后比较即可

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
 * @param root TreeNode类 
 * @param p int整型 
 * @param q int整型 
 * @return int整型
 */
int lowestCommonAncestor(struct TreeNode* root, int p, int q ) {
    // write code here
    
    int stack1[10001] = {0};
    int stack2[10001] = {0};
    int s1ptr = 0;
    int s2ptr = 0; 
    
    struct TreeNode* tmp = root; 

    while(tmp->val != p){
        stack1[s1ptr++] = tmp->val; 
        
        if(p < tmp->val) tmp = tmp->left;
        else tmp = tmp->right;
    }
    stack1[s1ptr] = p; 
    
    tmp = root; 
    while(tmp->val != q){
        stack2[s2ptr++] = tmp->val; 
        
        if(q < tmp->val) tmp = tmp->left;
        else tmp = tmp->right;
    }
    stack2[s2ptr] = q; 
    
    if(s1ptr < s2ptr){
        for(int i=s1ptr;i>=0;i--){
            if(stack1[i] == stack2[i]) return stack1[i];
        }
    } else {
        for(int i=s2ptr;i>=0;i--){
            if(stack1[i] == stack2[i]) return stack1[i];
        }
    }
    
    return 0;
}

```

# JZ7 重建二叉树

给定节点数为 n 的二叉树的前序遍历和中序遍历结果，请重建出该二叉树并返回它的头结点。
例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建出如下图所示。  

提示:  
1.vin.length == pre.length  
2.pre 和 vin 均无重复元素  
3.vin出现的元素均出现在 pre里  
4.只需要返回根结点，系统会自动输出整颗树做答案对比  

---  

前序遍历：前序遍历（VLR）， 是二叉树遍历的一种，也叫做先根遍历、先序遍历、前序周游，可记做根左右。前序遍历首先访问根结点然后遍历左子树，最后遍历右子树。

中序遍历： 中序遍历是二叉树遍历的一种，也叫做中根遍历、中序周游。 在二叉树中，中序遍历首先遍历左子树，然后访问根结点，最后遍历右子树。  

后序遍历：在二叉树中，先左后右再根，即首先遍历左子树，然后遍历右子树，最后访问根结点。  

e.g.,   
Step 1,  
前序遍历序列{***1***,2,4,7,3,5,6,8},  
中序遍历序列{4,7,2,***1***,5,3,8,6}, 此处1为根节点，相对于1，左侧均为左子树，右侧均为右子树。  


Step 2,  
{***2***, 4, 7}  
{4, 7, ***2***}

...

---

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
 * @param pre int整型一维数组 
 * @param preLen int pre数组长度
 * @param vin int整型一维数组 
 * @param vinLen int vin数组长度
 * @return TreeNode类
 */
struct TreeNode* reConstructBinaryTree(int* pre, int preLen, int* vin, int vinLen ) {
    // write code here
    if(pre == NULL || preLen == 0) return NULL; 
    
    // create a new node 
    struct TreeNode* node = (struct TreeNode*) malloc(sizeof(struct TreeNode));
    node->val = pre[0];
    
    int index = 0;
    while(vin[index] != node->val){
        index++;
    };
    
    node->left = reConstructBinaryTree(&(pre[1]), index, vin, index);
    node->right = reConstructBinaryTree(&(pre[index+1]), preLen-index-1, 
                                        &(vin[index+1]), vinLen-index-1);
    
    return node; 
}
```

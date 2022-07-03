# JZ28 对称的二叉树

给定一棵二叉树，判断其是否是自身的镜像（即：是否对称）  

思路2： 利用队列。对左子树从左往右遍历，并加入队列，对右子树从右往左遍历，并加入队列。  
每次循环从队列中取出一个节点进行比较，节点为空或者值相等，则可以说暂时相对称，进入下一循环。 否则，则返回false。 

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
 * @param pRoot TreeNode类 
 * @return bool布尔型
 */

bool isSymmetrical(struct TreeNode* pRoot ) {
    // write code here
    if(pRoot == NULL) return true; 
    
    struct TreeNode* fifo1[1001] = {NULL};
    int wptr1 = 0; 
    int rptr1 = 0; 

    struct TreeNode* fifo2[1001] = {NULL}; 
    int wptr2 = 0; 
    int rptr2 = 0; 
    
    fifo1[wptr1++] = pRoot->left;
    fifo2[wptr2++] = pRoot->right;
    
    // when both queue is not empty 
    while((rptr1 != wptr1) && (rptr2 != wptr2)){
        
        // pop node form left side and right side 
        struct TreeNode* left = fifo1[rptr1++];
        struct TreeNode* right = fifo2[rptr2++];
        
        if(left == NULL && right ==NULL){
            continue; 
        }
        if(left == NULL || right == NULL || left->val != right->val){
            return false; 
        }
        
        fifo1[wptr1++] = left->left;
        fifo1[wptr1++] = left->right;
        
        fifo2[wptr2++] = right->right;
        fifo2[wptr2++] = right->left;
    }
    
    return true; 
}
```

思路1： 同时遍历该二叉树，但是以两种方向进行遍历。  
根节点-> 左孩子-> 右孩子；根节点-> 右孩子 -> 左孩子；

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
 * @param pRoot TreeNode类 
 * @return bool布尔型
 */

bool treeRecursion(struct TreeNode* node1, struct TreeNode* node2){
    if(node1 == NULL && node2 == NULL){
        return true; 
    }
    if(node1 == NULL || node2 == NULL || node1->val != node2->val){
        return false; 
    }
    
    // RT -> RT.L -> RT.R
    // RT -> RT.R -> RT.L
    return treeRecursion(node1->left, node2->right) && treeRecursion(node1->right, node2->left);
}

bool isSymmetrical(struct TreeNode* pRoot ) {
    // write code here
    return treeRecursion(pRoot, pRoot);
}
```



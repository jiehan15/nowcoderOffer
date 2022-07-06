# JZ77 按之字形顺序打印二叉树

给定一个二叉树，返回该二叉树的之字形层序遍历，（第一层从左向右，下一层从右向左，一直这样交替）  

利用队列解决

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
 * @return int整型二维数组
 * @return int* returnSize 返回数组行数
 * @return int** returnColumnSizes 返回数组列数
 */
int** Print(struct TreeNode* pRoot, int* returnSize, int** returnColumnSizes ) {
    // write code here   
    if(pRoot == NULL) return NULL; 
    
    // the sapece for the returned two-dimension array  
    int** treeValues = (int**) malloc(sizeof(int*) * 1500); 
    // maximum depth of the tree is 1500 (a list essentially)
    *returnColumnSizes = (int*) malloc(sizeof(int) * 1500); 
    
    struct TreeNode* NodesFifo[1501] = {NULL}; 
    struct TreeNode* tmp; 
    int wptr = 0;
    int rptr = 0;
    
    NodesFifo[wptr++] = pRoot; 
    int depth = 0; 
    
    // when this variable is 1, means print from left to right 
    int left2right = 1;
    
    int coloumNums = 0;
    while(rptr != wptr){
        // the number of elements in the FIFO
        int gap = wptr - rptr; 
        int wptrtmp = wptr;
        coloumNums = 0;
        
        if(left2right){
            left2right = 0;
            treeValues[depth] = (int*) malloc(sizeof(int)*gap); 
            while(gap--){
                tmp = NodesFifo[rptr++];
                treeValues[depth][coloumNums++] = tmp->val;
                
                // move left child and right child into the queue 
                if(tmp->left != NULL) 
                    NodesFifo[wptr++] = tmp->left; 
                if(tmp->right != NULL) 
                    NodesFifo[wptr++] = tmp->right; 
            }
            (*returnColumnSizes)[depth] = coloumNums;
        } else {
            left2right = 1;
            treeValues[depth] = (int*) malloc(sizeof(int)*gap); 
            while(gap--){
                tmp = NodesFifo[--wptrtmp];
                treeValues[depth][coloumNums++] = tmp->val;
                
                // move left child and right child into the queue 
                tmp = NodesFifo[rptr++]; 
                if(tmp->left != NULL) 
                    NodesFifo[wptr++] = tmp->left; 
                if(tmp->right != NULL) 
                    NodesFifo[wptr++] = tmp->right; 
            }
            (*returnColumnSizes)[depth] = coloumNums;
        }
        depth++;
    }
    
    *returnSize = depth;
    return treeValues; 
}
```

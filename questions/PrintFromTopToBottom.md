# JZ32 从上往下打印二叉树

不分行从上往下打印出二叉树的每个节点，同层节点从左至右打印。例如输入{8,6,10,#,#,2,1}，如以下图中的示例二叉树，则依次打印8,6,10,2,1(空节点不打印，跳过)，请你将打印的结果存放到一个数组里面，返回。  

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
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 */
int* PrintFromTopToBottom(struct TreeNode* root, int* returnSize ) {
    // write code here
    if(root == NULL) return NULL;
    
    int* returnArr = (int*) malloc(sizeof(int) * 1001);
    int valueIndex = 0; 
    
    // fifo queue 
    struct TreeNode* fifo[1001] = {NULL}; 
    int wptr = 0;
    int rptr = 0;
    
    struct TreeNode* tmp = NULL; 
    
    fifo[wptr] = root; wptr++;
    while(wptr != rptr){
        // the number of elements in the FIFO
        int gap = wptr - rptr; 
        
        // read the nodes stores in the queue 
        while(gap){
            tmp = fifo[rptr]; 
            rptr++; 
            
            // copy the value to the return Array
            returnArr[valueIndex] = tmp->val; 
            valueIndex++;
            
            // move left child and right child into the queue 
            if(tmp->left != NULL){
                fifo[wptr] = tmp->left; 
                wptr++;
            }
            if(tmp->right != NULL){
                fifo[wptr] = tmp->right; 
                wptr++;
            }
            
            gap--; 
        }
    }
    
    *returnSize = valueIndex; 
    return returnArr; 
}
```

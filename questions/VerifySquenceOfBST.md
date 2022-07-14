# JZ33 二叉搜索树的后序遍历序列

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则返回 true ,否则返回 false 。假设输入的数组的任意两个数字都互不相同。  

提示：  
1.二叉搜索树是指父亲节点大于左子树中的全部节点，但是小于右子树中的全部节点的树。  
2.该题我们约定空树不是二叉搜索树  
3.后序遍历是指按照 “左子树-右子树-根节点” 的顺序遍历  

从最后一个节点开始， 遍历顺序变成 root -> right -> left, 由于当序列的值开始下降时，说明我们已经遍历到了左子树，找到大于当前值的最小值，该值即为局部树中的根节点。遍历过程中，逐步缩小root的值，因为所有的操作都是在当前根节点root的左子树中进行的，所以保证遍历的值小于root即可满足判断条件。  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param sequence int整型一维数组 
 * @param sequenceLen int sequence数组长度
 * @return bool布尔型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
bool VerifySquenceOfBST(int* sequence, int sequenceLen ) {
    // write code here
    if(sequence == NULL || sequenceLen == 0) return false; 
    
    int stack[1001] = {0};
    int sptr = 0;
    
    // maximum number 
    int root = 100000;
    
    for(int i=sequenceLen-1;i>=0;i--){
        // the value of current node is greater than the 
        // root node. 
        if(sequence[i] > root){
            return false; 
        }
        
        // find the minimum value which is greater than the 
        // current value who is also the new root node 
        while(sptr != 0 && sequence[i] < stack[sptr-1]){
            root = stack[sptr-1];
            sptr--;
        }
        
        stack[sptr++] = sequence[i];
    }
    return true; 
}
```

# JZ6 从尾到头打印链表

解法1： 6ms, 818kB
```c
/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 * };
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param listNode ListNode类 
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 */
int* printListFromTailToHead(struct ListNode* listNode, int* returnSize ) {
    // write code here
    if(listNode == NULL) return -1; 
    
    // 遍历数组 来取得链表长度
    unsigned int len = 0; 
    struct ListNode *p = listNode; 
    while(p){
        p=p->next;
        len++;
    }
    
    // 为新链表开辟空间
    int* returnListAddr = (int*) malloc(len * sizeof(int));
    p = listNode; 
    for(int i=len-1;i>=0;i--){
        returnListAddr[i] = p->val;
        p = p->next; 
    }
    
    // 返回值
    *returnSize = len; 
    return returnListAddr; 
}
```

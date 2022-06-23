# JZ24 反转链表

```c
/**
 * struct ListNode {
 *	int val;
 *	struct ListNode *next;
 * };
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */

/**
 * 
 * @param pHead ListNode类 
 * @return ListNode类
 */
struct ListNode* ReverseList(struct ListNode* pHead ) {
    // write code here
    // 必须初始化为NULL，否则报段错误
    struct ListNode *pPre = NULL; 
    struct ListNode *pCur = pHead; 
    struct ListNode *pNxt = NULL; 
    
    while(pCur){
        pNxt = pCur->next; 
        pCur->next = pPre; 
        
        pPre = pCur;
        pCur = pNxt; 
    }
    
    return pPre;
}
```

## 图解
![alt ReverseList](.\pics\ReverseList\ReverseList0.jpg)
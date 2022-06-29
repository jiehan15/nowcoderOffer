# JZ22 链表中倒数最后k个结点

思路二：快慢指针  
第一个指针先走k步。  
如果第一个指针为空，且走过的节点数小于k，则返回空链表。
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
 * @param pHead ListNode类 
 * @param k int整型 
 * @return ListNode类
 */
struct ListNode* FindKthToTail(struct ListNode* pHead, int k ) {
    // write code here
    if(pHead == NULL) return pHead; 
    struct ListNode *first = pHead; 
    struct ListNode *second = pHead; 
    
    while(k){
        // the length of the list is smaller than k
        if(first == NULL){
            return NULL; 
        } 
        first = first -> next;
        k--; 
    }
    
    // move the two pointer at the same time 
    while(first){
        first = first -> next; 
        second = second -> next; 
    }
    
    return second; 
}
```

思路一：先遍历链表获取标长；之后根据输入倒数数值取得输出链表入口
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
 * @param pHead ListNode类 
 * @param k int整型 
 * @return ListNode类
 */
struct ListNode* FindKthToTail(struct ListNode* pHead, int k ) {
    // write code here
    if(pHead == NULL) return pHead; 
    struct ListNode *p = pHead; 
    
    int length = 0-k; 
    // get list length 
    while(p){
        p = p->next; 
        length++;
    }
    
    // 如果k大于链表长度
    if(0 > length){
        return NULL;
    } else {
        p = pHead;
        
        while(length){
            p = p->next;
            length--; 
        }
        return p; 
    }
}
```

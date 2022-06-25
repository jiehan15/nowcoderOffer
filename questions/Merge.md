# JZ25 合并两个排序的链表

基本思路： 通过比较两个表中当前指向数据的大小，来形成一个新的链表。

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
 * 
 * @param pHead1 ListNode类 
 * @param pHead2 ListNode类 
 * @return ListNode类
 */
struct ListNode* Merge(struct ListNode* pHead1, struct ListNode* pHead2 ) {
    // write code here
    // write code here
    if(pHead1 == NULL)
        return pHead2;
    if(pHead2 == NULL)
        return pHead1;

    // 链表表头（prevHead->next）
    struct ListNode *prevHead = (struct ListNode *)malloc(sizeof(struct ListNode));

    // 合并后链表 当前项
    struct ListNode *p = prevHead;
     
    while(pHead1 != NULL && pHead2 != NULL)
    {
        if(pHead1->val < pHead2->val)
        {
            p->next = pHead1;
            p = pHead1;
            pHead1 = pHead1->next;
        }
        else
        {
            p->next = pHead2;
            p = pHead2;
            pHead2 = pHead2->next;
        }
    }
     
    if(pHead1 != NULL)
        p->next = pHead1;
    if(pHead2 != NULL)
        p->next = pHead2;
     
    return prevHead->next;
}
```

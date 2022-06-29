# JZ76 删除链表中重复的结点

示例1
```
输入：
{1,2,3,3,4,4,5}

返回值：
{1,2,5}
```
思路： 哈希表

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
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param pHead ListNode类 
 * @return ListNode类
 */
struct ListNode* deleteDuplication(struct ListNode* pHead ) {
    // write code here
    int hashTable[1001] = {0}; 
    struct ListNode *prev = NULL; 
    struct ListNode *p = pHead; 
    struct ListNode *dummyHead = pHead; 
    struct ListNode *returnHead = NULL; 
    
    while(p){
        hashTable[p->val] += 1; 
        p = p->next; 
    }
    
    // determine return head pointer 
    p = dummyHead; 
    while(p){
        if(hashTable[p->val] == 1){
            returnHead = p;
            break; 
        } else {
            prev = p;
            p = p->next; 
        }
    }
    
    // 继续遍历链表，去除重复元素
    while(p){
        if(hashTable[p->val] == 1){
            prev = p;
            p = p->next; 
        } else {
            // the value happens multiple times 
            prev->next = p->next;
            p = p->next; 
        }
    }
    
    return returnHead; 
}
```

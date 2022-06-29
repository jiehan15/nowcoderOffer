# JZ18 删除链表的节点
给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。返回删除后的链表的头节点。  
1.此题对比原题有改动  
**2.题目保证链表中节点的值互不相同**
3.该题只会输出返回的链表和结果做对比，所以若使用 C 或 C++ 语言，你不需要 free 或 delete 被删除的节点  

数据范围:  
0<=链表节点值<=10000  
0<=链表长度<=10000    

思路： 遍历链表，如果发现给定值则使前一节点的下一项等于当前节点的下一项（即从链表中删除当前项）。  
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
 * @param head ListNode类 
 * @param val int整型 
 * @return ListNode类
 */
struct ListNode* deleteNode(struct ListNode* head, int val ) {
    // write code here
    struct ListNode *perv = NULL; 
    struct ListNode *current = head; 
    struct ListNode *dummyHead = head; 
    
    // 如果头结点的值与给定值相同
    if(current->val == val) return current->next; 
    else {
        perv = current; 
        current = current->next; 
    }
    
    while(current){
        if(current->val == val){
            perv->next = current->next;
            return dummyHead; 
        }
        
        perv = current; 
        current = current->next; 
    }
    
    // no matched value 
    return dummyHead; 
}
```

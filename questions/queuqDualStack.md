# JZ9 用两个栈实现队列

用两个栈来实现一个队列，使用n个元素来完成 n 次在队列尾部插入整数(push)和n次在队列头部删除整数(pop)的功能。 队列中的元素为int类型。保证操作合法，即保证pop操作时队列内已有元素。  

基本思路：  
入栈时将数据存入栈1。  
出栈时若栈2非空，则返回栈2顶端元素；否则，现将栈1元素全部转移至栈2，然后返回栈2顶端元素。  

删除时，此方法部分元素时间复杂度不为O(1)。平均下来则时间复杂度为O(1)  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param node int整型 
 * @return 无
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
static int stack1[1001] = {0}; 
static int stack2[1001] = {0};

static int s1ptr = 0; 
static int s2ptr = 0; 

void push(int node ) {
    // write code here
    stack1[s1ptr] = node; 
    s1ptr++;
}

/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param 无 
 * @return int整型
 */
int pop() {
    // write code here
    if(s2ptr == 0){
        while(s1ptr){
            stack2[s2ptr] = stack1[(s1ptr-1)];
            s1ptr--;
            s2ptr++;
        }
    }
    
    int returnValue = stack2[(s2ptr-1)];
    s2ptr--;
    return returnValue; 
}
```

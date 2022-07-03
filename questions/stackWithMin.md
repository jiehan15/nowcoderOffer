# JZ30 包含min函数的栈

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的 min 函数，**输入操作时保证 pop、top 和 min 函数操作时，栈中一定有元素**。  

此栈包含的方法有：  
push(value):将value压入栈中  
pop():弹出栈顶元素  
top():获取栈顶元素  
min():获取栈中最小元素  

进阶：各个栈操作时间复杂度均为O(1)  
方案：在元素入栈时，进行比较大小 并记录最小值; 建立一个辅助栈来记录最大和最小值  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param value int整型 
 * @return 无
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */

static int stack1[301] = {0};
static int stack1min[301] = {0};
static int s1ptr = 0; 
static int s1min; 

void push(int value ) {
    // write code here
    // no element in the stack 
    if(s1ptr == 0) {
        s1min = value; 
    } else {
        // compare the given value and the logged minimum value in the 
        // satck 
        if(value < stack1min[(s1ptr-1)]) s1min = value; 
        else s1min = stack1min[(s1ptr-1)]; 
    }
    
    stack1[s1ptr] = value; 
    stack1min[s1ptr] = s1min; 
    s1ptr++; 
}

/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param 无 
 * @return 无
 */
void pop() {
    // write code here
    if(s1ptr != 0) s1ptr--;
}

/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param 无 
 * @return int整型
 */
int top() {
    // write code here
    return stack1[(s1ptr-1)];
}

/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param 无 
 * @return int整型
 */
int min() {
    // write code here
    return stack1min[(s1ptr-1)]; 
}
```

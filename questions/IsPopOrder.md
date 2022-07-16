# JZ31 栈的压入、弹出序列

描述  
输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否可能为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列1,2,3,4,5是某栈的压入顺序，序列4,5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。  
1. 0<=pushV.length == popV.length <=1000  
2. -1000<=pushV[i]<=1000  
3. pushV 的所有数字均不相同  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param pushV int整型一维数组 
 * @param pushVLen int pushV数组长度
 * @param popV int整型一维数组 
 * @param popVLen int popV数组长度
 * @return bool布尔型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
bool IsPopOrder(int* pushV, int pushVLen, int* popV, int popVLen ) {
    // write code here
    int stack1[1001] = {0};
    int sptr = 0;
    int pushptr = 0;
    
    for(int i=0;i<pushVLen;i++){
         // 入栈：栈为空或者栈顶不等于出栈数组
        while(pushptr < pushVLen && (sptr ==0 || stack1[sptr-1] != popV[i])){
            stack1[sptr++] = pushV[pushptr++];
        }
        
        // 栈顶等于出栈数组
        if(stack1[sptr-1] == popV[i]) sptr--;
        // 不符合
        else return false; 
    }
    
    return true;
}
```

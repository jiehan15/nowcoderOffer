# JZ71 跳台阶扩展问题

一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶(n为正整数)总共有多少种跳法。  

[JZ69 跳台阶](./jumpFloor.md)  
> 跳上n级台阶的方法等于 跳上n-1台阶的方法加上n-2台阶的方法...

同理， 跳上n级台阶的方法等于, $f(n)=f(n-1)+f(n-2)+...+f(1)$  
类似的， 跳上n-1级台阶的方法等于, $f(n-1)=f(n-2)+f(n-3)...+f(1)$  
所以有， $f(n)=2 \times f(n-1)$

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param number int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int jumpFloorII(int number ) {
    // write code here
    int res = 1;
    for(int i=1;i<number;i++){
        res = res << 1;
    }
    return res; 
}
```

# JZ69 跳台阶

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个 n 级的台阶总共有多少种跳法（先后次序不同算不同的结果）。  

跳上n级台阶的方法等于 跳上n-1台阶的方法加上n-2台阶的方法...

动态规划，优化空间

```c
/**
 * 
 * @param number int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int jumpFloor(int number ) {
    // write code here
    if(number<=2) return number;
    
    int a = 1; // 一层台阶
    int b = 2; // 两层台阶
    int res; 
    
    for(int i=2;i<number;i++){
        res = a+b;
        a=b;
        b=res;
    }
    return res; 
}
```

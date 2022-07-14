# JZ64 求1+2+3+...+n

求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。 

&&、||运算具有短路功能，示例：(A)&&(B)当A部分不成立，则B部分不会执行，(A)||(B)当A部分成立，则B部分不会执行。  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param n int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int Sum_Solution(int n ) {
    // write code here
    n && (n = n + Sum_Solution(n - 1));
    return n;
}
```

# JZ65 不用加减乘除做加法

写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。  

模拟硬件加法器

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param num1 int整型 
 * @param num2 int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int Add(int num1, int num2 ) {
    // write code here
    return num2 ? Add(num1 ^ num2, (num1 & num2) << 1) : num1;
}
```

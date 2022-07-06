# JZ15 二进制中1的个数

描述  
输入一个整数 n ，输出该数32位二进制表示中1的个数。其中负数用补码表示。  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param n int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int NumberOf1(int n ) {
    // write code here
    int res = 0; 
    for(int i =0; i<32;i++){
        res = res + (n & 0x1);
        n = n>>1;
    }
    return res; 
}

```

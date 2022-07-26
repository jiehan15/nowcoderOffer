# JZ17 打印从1到最大的n位数

输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999。  
1. 用返回一个整数列表来代替打印  
2. n 为正整数，0 < n <= 5  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param n int整型 最大位数
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int* printNumbers(int n, int* returnSize ) {
    // write code here
    if(n==0) return NULL; 
    // get the max number
    unsigned int max = 1;
    for(int i=0;i<n;i++){
        max = max * 10;
    }
    
    // print 
    *returnSize = max-1;
    int* printArray = (int*) malloc((max-1)*sizeof(int));
    
    for(int i=0;i<max;i++){
        printArray[i] = i+1;
    }
    
    return printArray; 
}
```

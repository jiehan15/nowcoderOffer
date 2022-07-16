# JZ10 斐波那契数列

描述  
大家都知道斐波那契数列，现在要求输入一个正整数 n ，请你输出斐波那契数列的第 n 项。  


解法1： 198ms
```c
/**
 * 
 * @param n int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int Fibonacci(int n ) {
    // write code here
    if(n<3) return 1;
    
    return Fibonacci(n-1)+Fibonacci(n-2);
}
```

解法2： 5ms
```c
/**
 * 
 * @param n int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int Fibonacci(int n ) {
    // write code here
    int res[41] = {0};
    res[0] = 1; 
    res[1] = 1; 
    
    for(int i=2;i<n;i++){
        res[i] = res[i-1]+res[i-2];
    }
    
    return res[n-1];
}
```

解法3: 
```c
/**
 * 
 * @param n int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int Fibonacci(int n ) {
    // write code here
    if(n<3) return 1;
    int a = 1; 
    int b = 1; 
    int res; 
    
    for(int i=2;i<n;i++){
        res = a+b;
        a = b;
        b = res;
    }
    
    return res;
}
```

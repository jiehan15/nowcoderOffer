# JZ44 数字序列中某一位的数字

数字以 0123456789101112131415... 的格式作为一个字符序列，在这个序列中第 2 位（从下标 0 开始计算）是 2 ，第 10 位是 1 ，第 13 位是 1 ，以此类题，请你输出第 n 位对应的数字。  

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
int findNthDigit(int n ) {
    // write code here
    if(n==0) return 0;
    
    // one digit number, 1-9, 1*9 digits 
    // two digits number, 10-99, 2*90 digits 
    // three digits number, 100-999, 3*900 digits 
    // four digits number, 1000-9999, 4*9000 digits 
    // ...
    
    // select appropriate range for N
    unsigned int digit = 1;
    unsigned int sumofall = 9;
    unsigned int start = 1;
    
    while(n > sumofall){
        n = n - sumofall; 
        digit++;
        start = start * 10;
        sumofall = 9 * start * digit; 
    }
    
    // locate which number n lies at 
    int num = start + (n-1)/digit; 
    int index = (n-1) % digit; 
    
    int singledigit = 0;
    for(int i=0;i<=(digit-1-index);i++){
        singledigit = num % 10;
        num = num / 10;
    }
    
    return  singledigit;
}
```

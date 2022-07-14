# JZ16 数值的整数次方

实现函数 double Power(double base, int exponent)，求base的exponent次方。  

注意：  
1.保证base和exponent不同时为0。  
2.不得使用库函数，同时不需要考虑大数问题  
3.有特殊判题，不用考虑小数点后面0的位数。  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param base double浮点型 
 * @param exponent int整型 
 * @return double浮点型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
double Power(double base, int exponent ) {
    // write code here
    int realexponent; 
    double realbase; 
    if(exponent < 0){
        realexponent = -exponent;
        realbase = 1/base; 
    } else if(exponent > 0){
        realexponent = exponent;
        realbase = base; 
    }
        
    double res = 1; 
    // fast exponent 
    while(realexponent){
        if(realexponent & 0x1) res = res * realbase;
        realbase = realbase * realbase; 
        realexponent = realexponent >> 1;
    }
    return res; 
}

```

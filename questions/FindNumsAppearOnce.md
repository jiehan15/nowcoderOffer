# JZ56 数组中只出现一次的两个数字 
一个整型数组里除了两个数字只出现一次，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。  

自己和自己异或是0， e.g. 1^2^1 = 2  
然而题目要求两个数  

^{0b1, 0b101, 0b1, 0b111} = 0b10

^{0b11. 0b110} = 0b101

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param array int整型一维数组 
 * @param arrayLen int array数组长度
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int* FindNumsAppearOnce(int* array, int arrayLen, int* returnSize ) {
    // write code here
    // 取得两个不同数的差异
    int diff = 0;
    for(int i=0;i<arrayLen;i++){
        diff = diff ^ array[i];
    }
    
    // 以二进制最低不同位为分组条件
    int mask = 0b1;
    for(int i=0;i<32;i++){
        if(mask & diff) break; 
        else mask = mask << 1;
    }
    
    // 分组异或
    int num1 = 0;
    int num2 = 0;
    for(int i=0;i<arrayLen;i++){
        if(array[i] & mask) num1 = num1 ^ array[i];
        else num2 = num2 ^ array[i];
    }
    
    // 升序返回
    int* ret = (int*) malloc(2*sizeof(int));
    if(num1 > num2){
        ret[0] = num2;
        ret[1] = num1;
    }else{
        ret[0] = num1;
        ret[1] = num2;
    }
    
    *returnSize = 2;
    return ret; 
}
```

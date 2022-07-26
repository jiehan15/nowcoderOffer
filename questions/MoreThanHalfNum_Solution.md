# JZ39 数组中出现次数超过一半的数字 

描述  
给一个长度为 n 的数组，数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
例如输入一个长度为9的数组[1,2,3,2,2,2,5,4,2]。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。  

数据范围：$n \le 50000$，数组中元素的值 $0 \le val \le 10000$  
要求：空间复杂度：$O(1)$，时间复杂度 $O(n)$  
输入描述：  
保证数组输入非空，且保证有解  

哈希表
空间复杂度：$O(n)$，时间复杂度 $O(n)$  
```c
/**
 * 
 * @param numbers int整型一维数组 
 * @param numbersLen int numbers数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int MoreThanHalfNum_Solution(int* numbers, int numbersLen ) {
    // write code here
    int halflen = numbersLen/2;
    
    int hash[10001] = {0}; 
    int res;
    
    for(int i=0; i<numbersLen;i++){
        int num = numbers[i];
        hash[num] = hash[num] + 1;
        if(hash[num] > halflen) 
        {
            res = num;
            break; 
        }
    }
    return res; 
}
```

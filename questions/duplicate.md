# JZ3 数组中重复的数字

在一个长度为n的数组里的所有数字都在0到n-1的范围内。 数组中某些数字是重复的，但不知道有几个数字是重复的。也不知道每个数字重复几次。请找出数组中任意一个重复的数字。 例如，如果输入长度为7的数组[2,3,1,0,2,5,3]，那么对应的输出是2或者3。存在不合法的输入的话输出-1  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param numbers int整型一维数组 
 * @param numbersLen int numbers数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int duplicate(int* numbers, int numbersLen ) {
    // write code here
    if(numbers == NULL) return -1;
    if(numbersLen <= 1) return -1;
    
    int hashMap[10001] = {0};
    int tmp;
    
    for(int i=0;i<numbersLen;i++){
        tmp = numbers[i]; 
        if(hashMap[tmp] == 1) return tmp;
        else hashMap[tmp] = 1;
    }
    return -1;
}
```

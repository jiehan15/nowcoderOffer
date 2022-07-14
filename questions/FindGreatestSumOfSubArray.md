# JZ42 连续子数组的最大和

输入一个长度为n的整型数组array，数组中的一个或连续多个整数组成一个子数组，子数组最小长度为1。求所有子数组的和的最大值。  

动态规划

空间复杂度1
```c
/**
 * 
 * @param array int整型一维数组 
 * @param arrayLen int array数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int FindGreatestSumOfSubArray(int* array, int arrayLen ) {
    // write code here
    if(array == NULL) return NULL;
    if(arrayLen == 1) return array[0]; 
    
    int sum = array[0];
    int max = array[0];
    
    for(int i=1;i<arrayLen;i++){
        sum = ((sum + array[i]) > array[i]) ?
                    (sum+array[i]) : array[i];
        max = (sum > max) ? sum : max;
    }
    return max;
}

```

空间复杂度n
```c
/**
 * 
 * @param array int整型一维数组 
 * @param arrayLen int array数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int FindGreatestSumOfSubArray(int* array, int arrayLen ) {
    // write code here
    if(array == NULL) return NULL;
    if(arrayLen == 1) return array[0]; 
    
    int* DynamicProg = (int*) malloc(sizeof(int)*arrayLen);
    int max = array[0];
    DynamicProg[0] = array[0];
    
    for(int i=1;i<arrayLen;i++){
        DynamicProg[i] = ((DynamicProg[i-1]+array[i]) > array[i]) ?
                    (DynamicProg[i-1]+array[i]) : array[i];
        max = (DynamicProg[i] > max) ? DynamicProg[i] : max;
    }
    return max;
}

```

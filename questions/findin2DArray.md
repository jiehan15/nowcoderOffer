# JZ4 二维数组中的查找

在一个二维数组array中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。  
[  
[1,2,8,9],  
[2,4,9,12],  
[4,7,10,13],  
[6,8,11,15]  
]  
给定 target = 7，返回 true。  
给定 target = 3，返回 false。

要求空间复杂度为O(1), 时间复杂度为O(n+m)  

`bool Find(int target, int** array, int arrayRowLen, int* arrayColLen ) ` 

既然已知数据的行列数，且每行，每列元素递增。  
从左下角开始遍历，  
如果当前数字大于target,那么查找往上移一位,如果当前数字小于target,那么查找往右移一位。  
查找到target,返回true; 如果越界，返回false;

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param target int整型 
 * @param array int整型二维数组 
 * @param arrayRowLen int array数组行数
 * @param arrayColLen int* array数组列数
 * @return bool布尔型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
bool Find(int target, int** array, int arrayRowLen, int* arrayColLen ) {
    // write code here
    if(array == NULL) return false; 
    if(target < array[0][0]) return false; 
    if(target > array[arrayRowLen-1][arrayColLen[arrayRowLen-1]-1]) return false; 
    
    int row = arrayRowLen-1; 
    int col = 0; 
    int maxcol = arrayColLen[0];

    while(row >= 0 && col < maxcol){
        if(target > array[row][col]) col++;
        else if(target < array[row][col]) row--;
        else return true; 
    }
    
    return false; 
}
```

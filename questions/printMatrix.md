# JZ29 顺时针打印矩阵

描述  
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下4 X 4矩阵：  
```
[[1,2,3,4],
[5,6,7,8],
[9,10,11,12],
[13,14,15,16]]
```
则依次打印出数字  
```
[1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10]
``` 
数据范围:  
$0 \le matrix.length \le 100$  
$0 \le matrix[i].length \le 100$  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param matrix int整型二维数组 
 * @param matrixRowLen int matrix数组行数
 * @param matrixColLen int* matrix数组列数
 * @return int整型一维数组
 * @return int* returnSize 返回数组行数
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int* printMatrix(int** matrix, int matrixRowLen, int* matrixColLen, int* returnSize ) {
    // write code here
    if(matrix == NULL || (matrixRowLen==0 && matrixColLen[0]==0)) return NULL; 
    
    int left = 0;
    int right = matrixColLen[0] - 1;
    int up = 0;
    int down = matrixRowLen - 1; 
    
    int size = matrixRowLen * matrixColLen[0]; 
    *returnSize = size; 
    int* returnArr = (int*) malloc(size*sizeof(int));
    int returnArrptr = 0;
    
    while(left <= right && up <= down){
        // at up boundary, from left to right 
        for(int i=left;i<=right;i++){
            returnArr[returnArrptr++] = matrix[up][i];
        }
        up++; 
        if(up > down) break; 
        
        for(int i = up; i <= down; i++){
            returnArr[returnArrptr++] = matrix[i][right];
        }
        right--;
        if(left > right) break;

        for(int i = right; i >= left; i--){
            returnArr[returnArrptr++] = matrix[down][i];
        }
        down--;
        if(up > down) break;
        
        for(int i = down; i >= up; i--){
            returnArr[returnArrptr++] = matrix[i][left];
        }
        left++;
        if(left > right) break;
    }
    
    return returnArr; 
}
```

# JZ81 调整数组顺序使奇数位于偶数前面(二)

描述  
输入一个长度为 n 整数数组，数组里面可能含有相同的元素，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前面部分，所有的偶数位于数组的后面部分，对奇数和奇数，偶数和偶数之间的相对位置不做要求，但是时间复杂度和空间复杂度必须如下要求。  

数据范围：$0 \le n \le 50000$，数组中每个数的值 $0 \le val \le 10000$  
要求：时间复杂度 $O(n)$，空间复杂度 $O(1)$  

---
step 1：准备双指针从首尾开始，相互对撞。  
step 2：如果左右都是奇数，说明左边没问题，因为奇数要在左边，因此左指针右移，右指针暂时不动。  
step 3：如果左奇数右偶数，符合要求，左右指针都向中间走。  
step 4：如果左偶数右奇数，符合要交换的条件，将偶数换到后面，奇数换到前面。  
step 5：如果左右都是偶数，只移动右指针，右边是偶数一定正确，指针左移，但是左边需要待定，于是暂时不动。  
step 6：两指针相遇时就一定能保证左指针以左一定是奇数，右指针以右一定是偶数，做到了调整数组顺序使奇数位于偶数前面。  

---
不满足空间复杂度要求？，在原数组上操作:如上操作
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
 */
int* reOrderArrayTwo(int* array, int arrayLen, int* returnSize ) {
    // write code here
    if(arrayLen==0) return NULL; 
    
    int front = 0;
    int end = arrayLen-1;
    *returnSize = arrayLen; 
    
    int* returnArr = (int*) malloc(arrayLen*sizeof(int));
    
    for(int i =0;i<arrayLen;i++){
        if(array[i] % 2 == 0){
            returnArr[end--] = array[i];
        } else {
            returnArr[front++] = array[i];
        }
    }
    
    return returnArr;
}
```

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
 */
int* reOrderArrayTwo(int* array, int arrayLen, int* returnSize ) {
    // write code here
    if(arrayLen==0) return NULL; 
    *returnSize = arrayLen;
    int* returnArr = (int*) malloc(arrayLen*sizeof(int));

    int odds = 0;
    for(int i =0;i<arrayLen;i++){
        if(array[i] % 2){
            odds++;
        }
    }
    
    int x = 0; int y = odds; 
    for(int i =0;i<arrayLen;i++){
        if(array[i] % 2 == 0){
            returnArr[y++] = array[i];
        } else {
            returnArr[x++] = array[i];
        }
    }
    
    return returnArr;
}
```

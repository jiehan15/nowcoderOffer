# JZ11 旋转数组的最小数字 

有一个长度为 n 的非降序数组，比如[1,2,3,4,5]，将它进行旋转，即把一个数组最开始的若干个元素搬到数组的末尾，变成一个旋转数组，比如变成了[3,4,5,1,2]，或者[4,5,1,2,3]这样的。请问，给定这样一个旋转数组，求数组中的最小值。  

二分法  
如果[mid]大于[right]，则最小的元素处于[mid]和[right]之间，使left=mid+1;  
如果[mid]小于[right], 则最小的元素处于[mid]和[left]之间，使right=mid;  
如果相等则无法判断，去掉末尾一个元素重新循环。

```c
/**
 * 
 * @param rotateArray int整型一维数组 
 * @param rotateArrayLen int rotateArray数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int minNumberInRotateArray(int* rotateArray, int rotateArrayLen ) {
    // write code here
    if(rotateArray == NULL) return NULL;
    
    int left = 0; 
    int right = rotateArrayLen-1;
    int mid = (left+right)/2;
    
    while(left < right) {
        if(rotateArray[mid] > rotateArray[right]){
            left = mid + 1;
            mid = (left+right)/2;
        } else if (rotateArray[mid] < rotateArray[right]){
            right = mid;
            mid = (left+right)/2;
        } else {
            right--;
            mid = (left+right)/2;
        }
    }
    
    return rotateArray[right]; 
}
```

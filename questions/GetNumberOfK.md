# JZ53 数字在升序数组中出现的次数

其中二分法的时间复杂度为O(log n)

```c
/**
 * 
 * @param data int整型一维数组 
 * @param dataLen int data数组长度
 * @param k int整型 
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int GetNumberOfK(int* data, int dataLen, int k ) {
    // write code here
    // 简单遍历
//     int res = 0; 
    
//     for(int i=0;i<dataLen;i++){
//         if(data[i] == k) res++;
//         else if(data[i] > k) break;
//     }
    
//     return res; 
    // 二分法
    int left = 0;
    int right = dataLen-1; 
    float k1 = k+0.5;
    
    int upper; int lower;
    
    while(left <= right){
        int mid = (left+right)/2;
        if(data[mid] < k1) left = mid + 1;
        else if(data[mid] > k1) right = mid - 1; 
    }
    upper = left; 
    
    left = 0;
    right = dataLen-1; 
    k1 = k-0.5;
    while(left <= right){
        int mid = (left+right)/2;
        if(data[mid] < k1) left = mid + 1;
        else if(data[mid] > k1) right = mid - 1; 
    }
    lower = left; 
    
    return upper-lower;
}
```

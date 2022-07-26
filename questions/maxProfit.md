# JZ63 买卖股票的最好时机(一)

假设你有一个数组prices，长度为n，其中prices[i]是股票在第i天的价格，请根据这个价格数组，返回买卖股票能获得的最大收益  
1.你可以买入一次股票和卖出一次股票，并非每天都可以买入或卖出一次，总共只能买入和卖出一次，且买入必须在卖出的前面的某一天  
2.如果不能获取到任何利润，请返回0  
3.假设买入卖出均无手续费  

数据范围： $0 \le n \le 10^5$ , $0 \le val \le 10^{4}$  
 
要求：空间复杂度 $O(1)$，时间复杂度 $O(n)$  

示例1  
```
输入：
[8,9,2,5,4,7,1]

返回值：
5

说明：
在第3天(股票价格 = 2)的时候买入，在第6天(股票价格 = 7)的时候卖出，最大利润 = 7-2 = 5 ，不能选择在第2天买入，第3天卖出，这样就亏损7了；同时，你也不能在买入前卖出股票。 
```

该问题要求给定数组中两个数字只差的最大值，而且第一个数字（买入价格）必须小于第二个数字（卖出价格）  

1、使用变量记录历史最低价格 minprice  
2、则在第 i 天卖出股票能得到的利润就是 prices[i] - minprice  
3、因此，我们只需要遍历价格数组一遍，记录历史最低点  

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param prices int整型一维数组 
 * @param pricesLen int prices数组长度
 * @return int整型
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */
int maxValue(int a, int b){
    return (a>b) ? a : b; 
}

int minValue(int a, int b){
    return (a>b) ? b : a; 
}

int maxProfit(int* prices, int pricesLen ) {
    if(pricesLen == 0 || prices == NULL) return 0; 
    // write code here
    int maxProfit = 0; 
    int minimumprice = 10001; // max value <= 10^4 
    
    for(int i=0;i<pricesLen;i++){
        maxProfit = maxValue(maxProfit, prices[i]-minimumprice); 
        minimumprice = minValue(minimumprice, prices[i]); 
    }
    
    return maxProfit; 
}
```

# JZ73 翻转单词序列

牛客最近来了一个新员工Fish，每天早晨总是会拿着一本英文杂志，写些句子在本子上。同事Cat对Fish写的内容颇感兴趣，有一天他向Fish借来翻看，但却读不懂它的意思。例如，“nowcoder. a am I”。后来才意识到，这家伙原来把句子单词的顺序翻转了，正确的句子应该是“I am a nowcoder.”。Cat对一一的翻转这些单词顺序可不在行，你能帮助他么？  

1. 获取字符串长度
2. 从结尾开始，讲字母推入栈1，直到遇见空格。
3. 讲栈1中字母推入栈2，并在最后添加一个空格。回到2
4. 直到遍历完str, 返回栈2地址

```c
/**
 * 代码中的类名、方法名、参数名已经指定，请勿修改，直接返回方法规定的值即可
 *
 * 
 * @param str string字符串 
 * @return string字符串
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 *
 * C语言声明定义全局变量请加上static，防止重复定义
 */

#include <string.h>

static char stack1[101] = {0}; 
static int s1ptr = 0; 

static char stack2[101] = {0}; 
static int s2ptr = 0; 

char* ReverseSentence(char* str ) {
    // write code here
    int len = strlen(str);
    int strptr = len - 1; 
    
    while(strptr>=0){
        if(str[strptr] != ' '){
            stack1[s1ptr++] = str[strptr];
        } else {
            while(s1ptr){
                stack2[s2ptr++] = stack1[--s1ptr];
            }
            stack2[s2ptr++] = ' '; 
        }
        strptr--;
    }
    
    // the last word 
    // the input word can start with space
    while(s1ptr){
        stack2[s2ptr++] = stack1[--s1ptr];
    }
    stack2[s2ptr++] = '\0'; 
    
    return stack2; 
}
```

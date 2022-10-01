
```cpp
while(*str)
//quit when *str is '\0'
```



## 处理字符串的参数
- 就是char类型的指针--char *


## 内联函数
关键字 -- inline
使用要求：
- 一个函数不断被调用
- 函数很短

## 定义相同的变量值，但是不同的变量名
```cpp
    int a = 101;
    int & Aa = a;
```
&是一个类型标识符
它的作用是引用
姑且叫它 引用符

## 交换注意点
```cpp
#include "chapter_3.h"
void swap(int a , int b);
int main(void)
{
    int a = 10;
    int b = 20;
    swap(a,b);
    cout << a << endl;
    cout << b << endl;
    return 0;
}
void swap(int a , int b)
{
    int temp;

    temp = a;
    a = b;
    b = temp;
}

```
这种交换，不会影响主函数的输出。

```cpp
#include "chapter_3.h"
void swap(int a , int b);
int main(void)
{
    int a = 10;
    int b = 20;
    swap(a,b);
    return 0;
}
void swap(int a , int b)
{
    int temp;

    temp = a;
    a = b;
    b = temp;
    cout << a << endl;
    cout << b << endl;
}
```
这样写就不一样了 ，
因为swap函数的a和b是主函数
扔给它的，所以在swap函数内部输出的话
对应的值就会改变。
但是第一种情况就是把a和b的值扔给swap函数
仅仅只是在swap函数内部改变了a和b的值
在main函数里面没有改变

所以啊所以，那些非空函数，就是那些有返回值的函数
才会对主函数变量的值产生影响
这也是return存在的原因。
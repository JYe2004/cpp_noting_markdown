```cpp
while(*str)
//quit when *str is '\0'
```

# c++中的函数

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

## 函数重载

```cpp
#include "chapter_3.h"
using namespace std;
//交换 int 变量的值
void Swap(int *a, int *b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}
//交换 float 变量的值
void Swap(float *a, float *b)
{
    float temp = *a;
    *a = *b;
    *b = temp;
}
//交换 char 变量的值
void Swap(char *a, char *b)
{
    char temp = *a;
    *a = *b;
    *b = temp;
}
//交换 bool 变量的值
void Swap(bool *a, bool *b)
{
    char temp = *a;
    *a = *b;
    *b = temp;
}
int main()
{
//交换 int 变量的值
    int n1 = 100, n2 = 200;
    Swap(&n1, &n2);
    cout << n1 << ", " << n2 << endl;
//交换 float 变量的值
    float f1 = 12.5, f2 = 56.93;
    Swap(&f1, &f2);
    cout << f1 << ", " << f2 << endl;
//交换 char 变量的值
    char c1 = 'A', c2 = 'B';
    Swap(&c1, &c2);
    cout << c1 << ", " << c2 << endl;
//交换 bool 变量的值
    bool b1 = false, b2 = true;
    Swap(&b1, &b2);
    cout << b1 << ", " << b2 << endl;
    return 0;
}
```

一句话：函数名字相同，
功能相近，但是函数的参数类型
注意啊，一定是要参数类型不同
参数类型不同！！！
比如以下：

```cpp
void swap(int a);

void swap(int *a);
```

就是不行的，因为就算它一个是指针，一个是普通类型
但是都是int；类型就是错的！！

---

## 补充

namespace关键字

```cpp
namespace Jill{
    double bucket(double n){  }
    double fetch;
}
int main(void)
{
   using namespace Jill
   cin >>Jill::fetch 
}
```

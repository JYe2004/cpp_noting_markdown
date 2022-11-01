# Auto_ptr
```cpp
#include<memory>
```
- new和new[]的内存需要用delete和delete]释放。
- 程序员的主观失误，忘了或漏了释放。
- 程序员也不确定何时释放。
## 智能指针
### 遍历
```cpp
vector<int> v;
v.push_back(12);
v.push_back(241);
for( auto i : v) 
	cout << i << " "; // 12 241
```
只能**遍历所有**
如果要指定的内容进行遍历，需要另选方法。


>后期用来再回来补充笔记了
### unique_ptr
```cpp
#include <iostream>
#include<memory>
using namespace std;

class AA{

public:
    string m_name;
    AA(){cout << m_name << "Constructor_AA() is called!" << endl;}
    AA(const string &name):m_name(name){cout << "Constructor_AA() is called(" << m_name << ")\n";}
    ~AA(){cout << "Destructor is called!(" << m_name <<")" << endl;}
};

#include "TestAutoPtr.h"
int main(void)
{
///1.   demo中用的是类，用c++本身的数据类型看不出析构效果
//    AA *p = new AA("Julia");
//    unique_ptr<AA>output_1(p);

////2.上下等效
//    unique_ptr<AA>output_1(new AA("Julia"));

///3.    unique_ptr<AA>output_1 = make_unique<AA>("Julia");
//    make_unique替代了new

//// - 它重构了* 和 -> ;所以普通指针的用法它也具备
    unique_ptr<AA>output_1(new AA("julia"));
    cout << "m_name = " << output_1->m_name << endl;
    cout << "m_name = " << (*output_1).m_name << endl;
    return 0;
}
```
```cpp
//最后运行结果：
    Constructor_AA() is called(julia)
    m_name = julia
    m_name = julia
    Destructor is called!(julia)
```

### shared_ptr

### weak_ptr

## 自动转换类型(复习)
1. 本身不是一个数据类型，是一个占位符，用之前必须要先有初始化
2. 在对const和&类型的时候要格外注意
```cpp
const int num = 10;

auto num = 100; // 合法，此时auto为int类型
auto &num = 100;//报错，此时auto为const int类型

///////////////////////////////

int a = 10;
int &A = 100;//a = A =100

auto B = 1000;//报错
auto &B = 1000;//合法
```

3. 取代繁杂的数据类型
```cpp
std::vector<int>test;
std::vector<int>:: iterator it = test.begin();

//auto
std::vector<int>test;
auto it = test.begin();
//auto 代替了整个std::vector<int>:: iterator
```

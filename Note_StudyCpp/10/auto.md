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

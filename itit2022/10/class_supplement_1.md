## 友元(friend)

## 重载运算符

ostream 类对<<运算符进行了重载
总结:
- 友元函数的函数原型位于在类声明中，但并不是类的成员函数，在声明函数原型时，需要使用 friend 关键字。
- 友元函数的函数定义不需要 friend 关键字和 :: 运算符，和普通非成员函数是一样的。
- 友元函数可以直接访问类的私有成员。
- 通常在运算符重载中使用友元函数的情况是：**重载的运算符的第一个参数不是该类的对象。**

/*
————————————————
版权声明：本文为CSDN博主「柚咖」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_40395874/article/details/123783307
*/

可以把运算符重载函数声明为类的友元函数，
可以调换参数
事实上，就如果用普通的*类成员*来重载运算符
第一个参数就只能够传**类定义**
比如：
- i
```cpp
Time::Time operator*(double n)const;
```
这种就只能够
```cpp
Time A,B;
A = B * 2.5;

A = 2.5 * B;//报错
```
- ii 
但是换成友元就不一样了
```cpp
//如果在类定义中用了友元函数
//首先就不用加上Time::前缀
Time operator*(double n,const Time &m)const;
//这样子，注意，第一个参数不是一个类定义了
//第二个参数才是类定义
//于是就有了下面的语句
A = 2.5 * B;//不会报错！
//于是每每写重载运算符（*）的时候
//将i和ii结合在超级功能在一起！！
```
- 重载运算符<<也是
如果不用友元函数，那么第一个函数就只能够是Time（类定义）
于是普通的类成员函数重载就只能：
```cpp
Time trip;
trip << cout;
//用来确保第一个参数是Time(类定义)
```
- 用了友元就能够
```cpp
cout << trip; 
```

- iii
补充：在重载二元运算符时，如果两个运算对象的类不一样，比如(double)2.5 * (Time)B
的时候就要用友元重载多一次，如果就是简单的(Time)A+(Time)B就不用用友元！

>class Time
> Time x;
> -- x就会类创建的对象

```cpp
//  a.h
    friend void operator<<(std::ostream &out, const Time &);
    //or
    friend std::ostream operator<<(std::ostream &output , const Time x);
```
```cpp
// a.cpp
std::ostream operator<<(std::ostream &output , const Time x)
{
    output << x.hours << "hours" << x.minutes << "mins";
    
    return output;
}
```

引用是为了提高效率
肯定是直接把参数传进来快过
变来变去啊
### 重构，主要是转化成这两种形式
```cpp
T1 = T2.operator+(T3);
T1 = operator+(T2,T3);
```
### 重构的时候，必须两者都是同一种类定义类型
```cpp
Time time1;
Time time2;
Time time 3;
time3 = time1 + time2;
```

## &

```cpp
void swap(int &r1, int &r2){
    int temp = r1;
    r1 = r2;
    r2 = temp;
}
```
这样写，怎么样都不能交换值
因为&创建的是一个临时变量
临时变量不能寻址
所以必须在同一段代码源才能改变


但是：
```cpp
//该函数用来判断数字是否为奇数
bool isOdd(const int &n){  //改为常引用
    if(n/2 == 0){
        return false;
    }else{
        return true;
    }
}

int main(){
    int a = 100;//
	isOdd(a);  //正确
	isOdd(a + 9);  //正确
	isOdd(27);  //正确
	isOdd(23 + 55);  //正确
}
```
这样是可以的
因为const int &会直接捆绑！
比2345还硬~



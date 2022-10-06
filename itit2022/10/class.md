# 面向对象

c++中结构体和类的最大不同是
在类中有数据隐藏（private），
但是结构体中
全部默认是公有（public）

基本特点

> 抽象
> 封装和数据隐藏
> 多态
> 继承
> 代码的可重用性

此处再补充**对象**的定义
1、**对象**是客观世界中的物体**在计算机中的反映和描述**，是***描述这个事物的数据***和***对这些数据的操作方法***的集合；
2、(就是你视频中的意思)对象就是事物，一切事物都是对象。
这两种定义区别很大，主要是关于对客观事物和对象关系的区别。
第一种定义认为：(Java中的)对象在描述事物；
第二种定义认为：对象=事物。
我个人是*偏向* **第一种**的，我们说Java中创建一个对象，并不是说创建了一个事物，而是说
**创建这个对象是为了描述一个事物**，创建这个对象会在Java中开辟一片内存空间并定义一组数据和方法，这组数据和方法都是为了描述这个事物而存在的。

记住这种说法：创建一个对象
（没有对象new一个）

## 抽象

- 其实就是把对象的特点描述清楚

## 封装

- 将对象的特点描述出来之后用一个**函数**表示
  使之区别于结构体
- 然后把那个函数扔到class定义里面


## 区别
在C++中 ,
类和结构是只有一个区别的：
类的成员默认是private，
而结构是public


# 编写程序
## cin.clear()在cpp中的重要性
```cpp
while (!(cin >> temphandicap))
    {
        cin.clear();
//        清空数组
        while (cin.get() != '\n')
            continue;
        cout << "Please enter an number: ";
    }
    cin.get();
```
不用clear会使

## this指针的理解
先上代码
```cpp
Golf::Golf()
{
    using std::cin;
    using std::cout;
    char tempname[40];
    int temphandicap;

    cout << "Please enter the fullname(enter to quit): ";
    cin.getline(tempname, Len);
    cout << "Please enter the handicap: ";
    while (!(cin >> temphandicap))
    {
        cin.clear();
//        清空数组
        while (cin.get() != '\n')
            continue;
        cout << "Please enter an number: ";
    }
    cin.get();
    *this = Golf(tempname, temphandicap);
    //调用默认构造函数创建一个临时对象赋值给调用对象;
}
```
主要把注意力放在第83行
this指针其实就是类定义函数的本身
有一个比喻就是this指针就是房子
当你走进房子的时候可以看到家具
但是已经看不到房子了
家具就是类定义的成员
房子就是this *

## 初始化和默认函数的理解
每次写类的public都有两个和**类定义长得一样**的函数
第一个函数（真身）：
- 用来初始化
- 作为函数本身（注意不是以第二个为标准的）
- 如果第一个没有参数，第二个再搞参数是传不进去的 
  报错一个无限递归！！（自己给自己传参！！大错特错）

第二个函数（化身）：
- 用来给用户自己定义的
- 在主函数里面使用的时候 第二个 <--> 第一个
这两个函数会融化成一个

>这两个一样的类定义会作为访问private的专属函数
>敲黑板了：两个一样的类定义和类定义函数本身长得一样
是访问私有的函数！！！

如果在编写第二个类函数时需要传参的，就请在第一个函数里面假如参数
并且通过参数来初始化函数
```cpp
//默认函数
Golf::Golf(const char *name, int hc)
{
    strncpy(this->fullname, name, 40);
    this->fullname[39] = '\0';
    this->handicap = hc;
}
```
## 对于关于类定义隐藏(private)功能的理解
都说这是class和struct的最大不同
class的隐藏功能表示在每次访问private的内容的时候
只能通过类函数本身来访问
并且访问的时候
它不会想public那样把函数名也写出来
它质押直接传参就行了，
无需写出函数名

因为一般我们说知道函数名就是到函数大概是拿来干什么的
但是private不用写出函数名，直接就可以又仅可以通过类函数本身（真身）传参访问
这就是隐藏！

## 再看 *初始化*
```cpp
        Sales(double ar[], int n = 0); //默认构造函数;
```
看到这个int n = 0;这个是将n初始化了
所以就不用再在类函数本身哪里初始化了

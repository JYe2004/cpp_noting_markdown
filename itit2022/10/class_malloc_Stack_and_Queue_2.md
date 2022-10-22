## 初始化类的私人数组要注意的地方
Note:
```cpp
//name[20]
strcpy(this -> name ,"\0");
```
参考
```cpp
Cow::Cow()
{
    std::strcpy(name, "\0");
    hobby = new char[1]; //对应析构函数释放内存;
    hobby[0] = '\0';
    weight = 0.0;
}

Cow::Cow(const char *nm, const char *ho, double wt)
{
    std::strncpy(name, nm, 20);
    name[19] = '\0';
    hobby = new char[strlen(ho) + 1];
    std::strcpy(hobby, ho);
    weight = wt;
}
/*
————————————————
版权声明：本文为CSDN博主「MZZDX」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/m0_46181359/article/details/109561218
 */

```

## 对类定义规律的解释
其实写了这么多类定义，我发现
和this有关的私有数据都是在左侧的
都是**等外部数据来赋值**给他的

## 
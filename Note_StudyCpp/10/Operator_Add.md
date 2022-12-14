## 作用域解析运算符(::)

### C++中的双冒号::

第一种，类作用域，用来标明类的变量、函数

```cpp
Human::setName(char*name);
```


第二种，命名空间作用域，用来注明所使用的类、函数属于哪一个命名空间的

```cpp
std::cout <"Hello World"<std::endl;
```

第三种，全局作用域，用来区分局部、全局的。最容易被忽视的一种，很多时候写了一个全局函数或者想要调用一个全局函数，却发现IDE或者Editor找不到该函数，原因是因为局部函数与想要调用的全局函数名字一样，然后找了很久也找不到原因，甚至放弃解决的。其实原因就是因为
【局部变量/函数】与【全局变量/函数】的名字相同，DE无法区分，这时候加上::就可以调用到全局函数，访问到全局变量了。

> 简单来讲就系话比你知，endl尼个野系来自std个

## << 流插入（提取）运算符
流提取运算符（>>）
和
流插入运算符（<<）

```c
int** generate(int numRows, int* returnSize, int** returnColumnSizes) {
    int** ret = malloc(sizeof(int*) * numRows);
    *returnSize = numRows;
    *returnColumnSizes = malloc(sizeof(int) * numRows);
    for (int i = 0; i < numRows; ++i) {
        ret[i] = malloc(sizeof(int) * (i + 1));
        (*returnColumnSizes)[i] = i + 1;
        ret[i][0] = ret[i][i] = 1;
        for (int j = 1; j < i; ++j) {
            ret[i][j] = ret[i - 1][j] + ret[i - 1][j - 1];
        }
    }
    return ret;
}
```



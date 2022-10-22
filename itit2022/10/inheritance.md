# 继承

## 公共继承
```cpp
class Son_test_1:public Base_Test{
```
父类 公共属性在子类还是 公共属性
父类 保护属性在子类还是 保护属性
父类 私有属性在子类还是 私有属性

## 保护继承
```cpp
class Son_test_2:protected Base_Test{
```
父类 公共属性 在子类变成了 保护属性
父类 保护属性在子类还是 保护属性
父类 私有属性在子类还是 私有属性
## 私有继承
```cpp
class Son_test_3:private Base_Test{
```
父类 公共属性 在子类变成了 私有属性
父类 保护属性 在子类变成了 私有属性
父类 私有属性在子类还是 私有属性


# charit

## get()
>getline() 
>get() 
>cin.get()

### getline()
- 每次只读取一行，以\n为结尾。
- getline()针对string类型！
    ```cpp
    string pizza;
      getline(cin , pizza[0].name); 
  ```
### get()
- 不丢弃换行
### cin.get()
- 可以用于截断\n
```cpp
     cout << "Weight!" << endl;
     cin >> candy[0].weight;
     cin.get();
  ```

## cin

### 注意
- 自动跳过空白字符 
    >意味着每次只读一个word
- 会自动添加\0
  
(其实我真的觉得它和scanf()很像)

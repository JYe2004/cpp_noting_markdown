## Queue
```cpp
//链表的实现
struct Node{
        Item item;
        struct Node *next;
    };
```

```cpp
//入队
bool Queue::enqueue(const Item &itemii)
{
    if(isfull())
        return false;
    Node * add = new Node;
    add->item = itemii;
    add->next = nullptr;
    items++;
    if(front == nullptr)
        front = add;
    else
        rear->next =add;
    rear = add;
    return true;
}
```
```cpp
class Queue{
    enum {Q_SIZE = 10};
private:
    struct Node{
        Item item;
        struct Node *next;
    };

    Node * front;
    Node * rear;
    int items;
    const int qsize;
    Queue(const Queue & q):qsize(0){ }
    Queue & operator=(const Queue & q)
            { return *this;};
```


```cpp
//出队
bool Queue::dequeue(Item & itemii)
{
if (front == NULL)
    return false;
itemii = front->item; //将队首元素赋值给item
items--;
Node * temp = front; //保存队首元素位置
front = front->next; //将front设置成指向下一个节点
delete temp; //删除以前的第一个节点
if (items == 0)
    rear = NULL;
return true;
}
```

```cpp
//处理内存
Queue::~Queue()
{
    Node * temp;
    while(front != nullptr)
    {
        temp = front;
        front = front->next;
        delete temp;
    }
}
```


## 遇到的Bug
```cpp
    Customer(){可以在这里初始化};
```
注意一定是在**花括号**内

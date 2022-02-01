## STl
STL(标准模板库)，是目前C++内置支持的library。它的底层利用了C++类模板和函数模板的机制，由三大部分组成：容器、算法和迭代器。

### 目前STL有六大组件
    - 容器 container
    - 算法 algorthm
    - 迭代器 iterator
    - 仿函数 function object
    - 适配器 adaptor
    - 空间配置器 allocator

### STL容器
容器是STL中很重要的一种数据结构。常见的容器包括
    - vector容器
    - deque双端数组
    - stack栈模型
    - queue队列模型
    - list链表模型
    - priotriy_queue优先级队列
    - set与multiset容器
    - map与multimap容器
除了容器，STL还封装了强大的算法，能够实现查找、删除、替换、删除等很多常见操作。

另外，迭代器也是STL重要的一环，通过迭代器，我们可以很方便对容器中的元素进行遍历，以及操作容器。

参考：岁与禾[https://www.jianshu.com/p/497843e403b4]https://www.jianshu.com/p/497843e403b4
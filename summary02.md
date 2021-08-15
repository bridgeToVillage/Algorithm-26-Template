## 第二周总结

### 1、哈希表、映射、集合的实现与特性

### hash table

哈希表，也叫散列表，是根据关键码值（key value）而直接进行访问的数据结构

它通过把关键码值映射到表中的一个位置来访问记录，以加快查找的速度。

这个映射函数叫作散列函数(Hash Function)，存放记录的数组叫作哈希表(或飞散列表)。

**实际运用**

像Redis就用到了很多哈希表


![](https://files.mdnice.com/user/5287/bb9c8161-dec5-409f-8569-4a5cf8934bd1.png)

这里有个完整结构，是发生过哈希碰撞的

![](https://files.mdnice.com/user/5287/79a031d8-d15a-4e5c-926e-c78a19887bd4.png)
发生过碰撞的会在对应节点拉出一个链表
**复杂度分析**

![](https://files.mdnice.com/user/5287/d036ec7d-f4d3-4f7d-8b76-4fa700487a4b.png)

**对应的数据结构**

![](https://files.mdnice.com/user/5287/f594d618-c298-4167-9ae2-8739ee5b9841.png)


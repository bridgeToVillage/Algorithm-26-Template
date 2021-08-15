## 预习总结

大脑不习惯记忆零散的知识，把知识串成脑图就比较好记忆。

### 数据结构

**一维**

- 基础：数组array，链表linked list
- 高级：栈stack，队列queue，双端队列deque，集合set，映射map，etc

**二维**

- 基础：树，图graph
- 高级: 二叉搜索树binary search tree(red-black tree,AVL)，堆heap，并查集disjoint set，字典树Trie，etc

**特殊**

- 位运算 Bitwise，布隆过滤器 BloomFilter
- 缓存LRU Cache

### 算法

- if-else, switch ——>branch

- for , while loop ——>iteration

- 递归Recursion(Divide & Conquer, Backtrace)

- 搜索Search: 深度优先搜索 Depth first search，广度优先搜索 Breadth first search, A*, etc

- 动态规划 Dynamic Programming

- 二分查找 Binary Search

- 贪心 Greedy

- 数学 Math, 几何 Geometry

  注意：在头脑中回忆每种算法的思想和代码模板

## 第一周学习总结

 

由于时间紧迫，就总结下知识点吧！

#### 数组、链表、跳表

数组对应了内存中一串连续的地址，数组的查找复杂度是O(1)，缺点是添加删除不方便

链表就是为了解决数组的添加删除不方便的问题出现的。但是同样的，它也有问题，就是查找复杂度较高O(n)

![image-20210808234814815](E:\doc\学习资料\微信公众号\pic\image-20210808234814815.png)

跳表就是为了方便链表的查找出现的，原理就是在原来链表基础上添加新维度的索引，方便更快地查找

![image-20210808235044739](E:\doc\学习资料\微信公众号\pic\image-20210808235044739.png)



#### 栈、队列、优先队列、双端队列

栈（stack）：先入后出，类似于羽毛球筒；

队列(queen): 先入先出，类似于排队买东西



1、Stack、Queue、Deque的原理和操作复杂度

2、PriorityQueue的特点和操作复杂度

3、查询Stack、Queue、Deque、PriorityQueue的系统接口的方法
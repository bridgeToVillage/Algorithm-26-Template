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

### 2、树、二叉树、二叉搜索树的实现与特性

![](https://files.mdnice.com/user/5287/32db7ac5-7ed2-4d06-8422-b31924620e9a.png)

**二叉树**

![](https://files.mdnice.com/user/5287/29a5561a-7fa2-4a6e-ac44-3abba8d71885.png)

**重点理解**
Linked list 是特殊化的Tree
Tree是特殊化的Graph，没有环的图是树


**二叉搜索树**

![](https://files.mdnice.com/user/5287/a58b8e66-3516-41ff-bc80-34c371c8f8d8.png)

它的查找复杂度是O(log2N)

![](https://files.mdnice.com/user/5287/2701a2a9-a8b4-41f5-b0bb-65f9499eda3a.png)

**二叉搜索树的删除操作**
- 1、删除一个没有子节点的比较简单
- 2、删除一个关键节点（有子节点的），找到它的右子树中比其大的最小一个元素，替换它的位置即可

这个工具非常适合练习二叉树
[二叉搜索树 Demo](https://visualgo.net/zh/bst)

### 3、堆和二叉堆、图

#### 知识点
**堆的定义**
![](https://files.mdnice.com/user/5287/cce58971-f57b-41eb-b2e4-02d654c0c168.png)

**二叉堆性质**
![](https://files.mdnice.com/user/5287/4876fda4-6cad-4922-b4a3-55e8b6d6ee64.png)

![](https://files.mdnice.com/user/5287/8282b1a7-d8a7-43bd-b7cc-eeb4d9029e72.png)

二叉堆的复杂度是O(logN)

**二叉堆实现**
![](https://files.mdnice.com/user/5287/ef530fd7-b7f8-4663-a990-7c8c37077bf3.png)

![](https://files.mdnice.com/user/5287/057f21be-25a4-47b5-8315-ef650b720a9d.png)


**堆的插入**
- 1、先插入的堆尾
- 2、插入元素与其父节点比较，如果比父节点大，就交换位置
- 3、重复步骤二，将插入元素往上浮，直到它比父节点少为止

**删除堆顶**
- 1、将堆尾元素放到堆顶，替换掉
- 2、将当前堆顶元素与左右子元素比较，找到比其大且是最大的子元素，二者交换位置
- 3、重复步骤二，直到堆尾为止

**图**

![](https://files.mdnice.com/user/5287/a9c6dbf1-49b7-4912-92ad-df50e683c81f.png)


![](https://files.mdnice.com/user/5287/67cfa67c-49bb-4cd4-856e-d14239655120.png)


![](https://files.mdnice.com/user/5287/b1a0ce99-25fe-4fc1-bef1-a04948372fdd.png)


![](https://files.mdnice.com/user/5287/0e26d6d3-a8dd-4496-ad04-52468c92f331.png)

![](https://files.mdnice.com/user/5287/ad41f89d-5a46-45c8-af81-ee3724ec8661.png)

![](https://files.mdnice.com/user/5287/acd498b1-d51c-499e-98ff-350a23719ddc.png)


![](https://files.mdnice.com/user/5287/051c02e1-fecf-4dc3-838e-4b55bfc4eb8e.png)

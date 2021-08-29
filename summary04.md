## 第四周总结

### 二叉树的搜索

在树（图/状态集）中寻找特定结点

#### 遍历

- 每个节点都要访问一次
- 每个节点仅仅要访问一次
- 对于节点的访问顺序不限

     -深度优先：depth first search

     -广度优先：breadth first search

     -优先级优先

#### 深度优先


![](https://files.mdnice.com/user/5287/79102bb0-2f39-4b36-8f99-e0e6d3a82bb2.png)




![](https://files.mdnice.com/user/5287/dfc7324c-210b-4982-8a21-2948b6d078b0.png)



![](https://files.mdnice.com/user/5287/cd816f02-c7cc-4806-9724-ce1b29480fe9.png)


#### 广度优先


![](https://files.mdnice.com/user/5287/481bb0c6-87b9-4ff6-aa48-e76506c79d5e.png)



![](https://files.mdnice.com/user/5287/c1c23c42-c7a5-4620-8a09-ebcd333f44d4.png)


### 贪心算法


![](https://files.mdnice.com/user/5287/bca8d9cd-823e-4bb0-8545-098591e2996f.png)


### 二分查找


![](https://files.mdnice.com/user/5287/e92379f5-6e15-4ac3-a7b8-9267baeda4f3.png)


二分查找理解：这是有一定套路的解法，主要就是约定几个索引位，从数组两头向中间进行夹逼推进，最终找到目标值。而在每次推进过程中都会舍弃掉当前资源中的一半，这样算下去，最终的时间复杂度就是O(logn)。

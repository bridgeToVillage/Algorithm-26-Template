## 第三周总结

### 递归的实现，特性及思维要点
递归类似于循环
通过函数体实现的循环

**盗梦空间**


![](https://files.mdnice.com/user/5287/b63bc41e-d5bc-48e1-8627-2f1d04e7f509.png)


![](https://files.mdnice.com/user/5287/94511335-b2f7-4a7b-ba50-246a7fac254f.png)

思维要点：
- 1、不要人肉递归
- 2、找到最近最简的重复问题，将其拆解成可重复解决的问题
- 3、数学归纳法思维


![](https://files.mdnice.com/user/5287/a836dfc4-682c-45a4-abf9-8afa5465940f.png)


### 分治和回溯

本质上是一种递归，它是把问题拆分为好几个子问题，然后每个子问题最终又都能迭代到同一个最小元问题，简单来说就是分情况进行递归，最终回到同一个简单的重复问题上再通过递归去解决问题。


![](https://files.mdnice.com/user/5287/ef6258b8-450a-4bdc-b163-1d815ccac40a.png)

分治


![](https://files.mdnice.com/user/5287/0c31c8fc-d914-4616-9b80-6c62ac9bfc34.png)


![](https://files.mdnice.com/user/5287/a05f2b1d-c2e7-4266-8c89-9344cd3ac9b5.png)

回溯的定义


![](https://files.mdnice.com/user/5287/df0cfc7f-601d-4b37-8f82-6fbb0b48680f.png)


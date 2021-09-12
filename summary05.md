## 第五周总结




![](https://files.mdnice.com/user/5287/ec29dd91-2abc-4149-be4a-8d6f7ab74431.png)


dfs是用栈，bfs用队列

二叉搜索树，左子树比其节点小，右子树比其节点大



### 完成了上半程，继续坚持


![](https://files.mdnice.com/user/5287/08f39674-286c-4a83-8ecf-c28b7d2dda19.png)


### 动态规划

分治、回溯、递归及动态规划

#### 递归

```
public void recur(int level,int param){
	//terminator 递归终止条件
	if(level > MAX_LEVEL){
		//process result
		return;
	}
	
	//process current logic 执行当前层逻辑
	process(level,param);
	
	//drill down 下探到下一层
	recur(level:level +1,newPram)
	
	//restore current status 有需要就恢复当前层状态
}
```



![](https://files.mdnice.com/user/5287/afaf44f1-5699-43c1-a2da-b082df9aeb04.png)


#### 分治

也是一种递归


![](https://files.mdnice.com/user/5287/b731c8dc-5444-4459-9517-76545d300292.png)


分为五步

- 1、递归终止条件
- 2、拆分子问题
- 3、调子问题的递归函数
- 4、合并结果
- 5、有需要就恢复当前层状态


![](https://files.mdnice.com/user/5287/6c8d5da8-bbe8-46c8-9528-2f9854ae93d4.png)




![](https://files.mdnice.com/user/5287/a812f3d4-e132-43fe-a82b-2cbc5d03839f.png)




动态规划的定义


![](https://files.mdnice.com/user/5287/41f8c812-e5f9-42e2-96af-a5a6550b8125.png)


动态规划的关键点


![](https://files.mdnice.com/user/5287/2ffa3b84-92dd-4d41-b9ad-eb5afb3f4802.png)




#### Fibonacci数列


![](https://files.mdnice.com/user/5287/1827f1bd-d880-4cc8-90c1-c3ff1616945e.png)


Fibonacci数列的优化


![](https://files.mdnice.com/user/5287/279afc07-318c-4dbc-8d25-002ff1fe305e.png)



![](https://files.mdnice.com/user/5287/faaa33da-9b7d-4687-bdf0-a50498296d12.png)

## 第六周总结

### 动态规划（二）

- [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/description/)（阿里巴巴、腾讯、字节跳动在半年内面试常考）

递推DP方程：

  F(n) = F(n-1) + F(n-2)

**第一种思路**

**第二种思路**





- [三角形最小路径和](https://leetcode-cn.com/problems/triangle/description/)（亚马逊、苹果、字节跳动在半年内面试考过）

- 1. brute-force,递归，n层：left or right:2^n
  2. DP

  ​       a.重复性（分治） problem(i, j) = min(sub(i+1, j), sub(i+1, j+1)) + a[i, j]

  ​       b.定义状态数组

  ​       c.DP方程 f[i, j] = min(f[i+1, j], f[i+1, j+1]) + a[i, j]

### 

- [最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)（亚马逊、字节跳动在半年内面试常考）



- [打家劫舍](https://leetcode-cn.com/problems/house-robber/)（字节跳动、谷歌、亚马逊在半年内面试中考过）

**两种思路**

- 1、增加一个偷或者不偷的维度

```js
//a[i][0,1]: 0..i能偷到的max value
//0:不偷， 1：偷
//dp方程
a[i][0] = max(a[i-1][0],a[i-1][1])
a[i][1] = a[i-1][0] + nums[i]
```

![image-20210912215027712](E:\doc\学习资料\微信公众号\pic\image-20210912215027712.png)

- 2、不增加偷或者不偷的维度

```js
//a[i]:0..i能偷到 max value,第i个房子可偷可不偷
//0：不管，1:偷
//dp方程
a[i] = Math.max(a[i-1], num[i]+a[i-2])
```

![image-20210912215313736](E:\doc\学习资料\微信公众号\pic\image-20210912215313736.png)

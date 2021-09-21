## 第7周作业

### 作业1

- [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)（阿里巴巴、腾讯、字节跳动在半年内面试常考）

#### 题目描述

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

**示例 1：**

```js
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。

1.  1 阶 + 1 阶
2.  2 阶
```

**示例 2：**

```js
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。

1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

#### 题解

这就是传统的动态规划题目`爬楼梯`，很容易想到，如果总共一级台阶就一种方法，如果总共二级就有二种方法。这是两个临界值。而dp方程就是一个斐波那契数列的表达式：dp[n] = dp[n-1] + dp[n-2]。到这里，代码就比较好写了。

需要注意的就是，在js数组里，索引0表示第一个元素，索引1表示第二个元素。那dp[0]就表示总共有一级台阶的方法总数，dp[1]就表示总共有两级台阶的方法总数。最终要求n级台阶的走法总数，就是求dp[n-1]的值。

```js
var climbStairs = function(n) {
    const dp = [];
    dp[0] = 1;
    dp[1] = 2;
    for(let i = 2; i < n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n-1];
};
```

这个解法，时间复杂度是O(n);空间复杂度是O(1)。

这题如果要体现剪枝解法，就得将题目切换到原始递归的思路去，代码就是这样：

```js
var climbStairs = function(n) {
     // 递归终止条件
     if(n == 1) return 1;
     if(n == 2) return 2;

     // 当前递归层的逻辑处理
     return climbStairs(n - 1) + climbStairs(n - 2);
};
```

思路跟上面的动态规划是一样的，不过是用了递归的思路。思路是没问题，不过实际执行后就直接超时了。为什么会这样？来看这张图：

![image.png](https://pic.leetcode-cn.com/1624713559-UBxbwC-image.png)

以n=5为例，用递归算法推算下去，每下探一层，复杂度呈指数级增长，即O(2^n)。而实际上，从这棵树上来看，有些节点是重复的。那实现剪枝的需求就来了！

![image.png](https://pic.leetcode-cn.com/1624713847-TsJPwi-image.png)

前面的动态规划解法就是剪枝后的方法，仔细观察会发现，动态规划的解法与这个递归解法的推算方向是相对的。动态规划是从已知的值向后推理，每一步都会把当前位置的值缓存起来，这样后面的计算就比较简单了。每次递归也只是一次简单的计算，不会向这个反向递归推理，呈指数级扩展。

链接：https://leetcode-cn.com/problems/climbing-stairs



### 作业2

- [括号生成](https://leetcode-cn.com/problems/generate-parentheses/)（亚马逊、Facebook、字节跳动在半年内面试中考过）

#### 题目描述

数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

有效括号组合需满足：左括号必须以正确的顺序闭合。

 

**示例 1：**

```js
输入：n = 3
输出：["((()))","(()())","(())()","()(())","()()()"]
```


**示例 2：**

```js
输入：n = 1
输出：["()"]
```



**提示：**

- 1 <= n <= 8



#### 题解

这题的难点是左括号的位置，不能出现在右括号的右边

```js
 /**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function(n) {
  const res = [];

  const dfs = (lRemain, rRemain, str) => { // 左右括号所剩的数量，str是当前构建的字符串
    if (str.length == 2 * n) { // 字符串构建完成
      res.push(str);           // 加入解集
      return;                  // 结束当前递归分支
    }
    if (lRemain > 0) {         // 只要左括号有剩，就可以选它，然后继续做选择（递归）
      dfs(lRemain - 1, rRemain, str + "(");
    }
    if (lRemain < rRemain) {   // 右括号比左括号剩的多，才能选右括号
      dfs(lRemain, rRemain - 1, str + ")"); // 然后继续做选择（递归）
    }
  };

  dfs(n, n, ""); // 递归的入口，剩余数量都是n，初始字符串是空串
  return res;
};
```



链接：https://leetcode-cn.com/problems/generate-parentheses

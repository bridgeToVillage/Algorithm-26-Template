## 第三周作业

### 作业1

- [ Pow(x, n) ](https://leetcode-cn.com/problems/powx-n/)（Facebook 在半年内面试常考）

#### 题目描述

实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数（即，xn）。

示例 1：

```js
输入：x = 2.00000, n = 10
输出：1024.00000
```


示例 2：

```js
输入：x = 2.10000, n = 3
输出：9.26100
```


示例 3：

```js
输入：x = 2.00000, n = -2
输出：0.25000
解释：2-2 = 1/22 = 1/4 = 0.25
```




提示：

- -100.0 < x < 100.0
- -231 <= n <= 231-1
- -104 <= xn <= 104

#### 题解

题目描述很简单，就是要用程序语言写出一个数学上的幂函数pow(x, n)。以2的n次方为例，2的0次方是1，2的3次方就是`2*2*2`，2的-3次方是`1/2*2*2`，2的4次方是`2*2*2*2`。

很显然当n很小的时候是很容易算出来的，但是如果n很大的时候就需要计算机帮忙了，那是不是可以把n分拆，最后再相乘就得到最终结果。那算法怎么写呢？如何用几行代码就能搞定n很大的情况？

这里介绍一个分治的解题思想，本质上来说，分治也是一种递归，不过是一种特殊的递归。分治，字面意思就是分开治理，意思就是把问题拆分开，把每个问题解决再合并在一起，得到最终答案。

在这个问题上，幂函数算法可以分为几种情况：n=0，n为奇数及n为偶数；比如2的5次方，可以分为两个2的平方相乘再乘以2。不管n多大，我们都可以通过不断递归，最终迭代到2*2这样一个最简单最小的单元。当n为奇数时，可以拆分为`x*(x的(n-1)次方)`，这样就转手递归到偶数情况下了，直至拆到`n=1`的情况结果就是`x*1` ；偶数情况下怎么算，可以拆分为`x*x的n/2次方`,这样可以一直拆到`2*2`的情况，还一个极端情况是`n=0`，那就是直接等于`1`了。

来看代码：

```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
    // n=0
    if(n===0) return 1 
    // n<0时 x的n次方等于1除以x的-n次方分
    if(n<0){   				
       return 1/myPow(x,-n)
    }
    //n是奇数时 x的n次方 = x*x的n-1次方
    if(n%2){    
       return x*myPow(x,n-1)
    }
    //n是偶数，使用分治，一分为二，等于x*x的n/2次方 
    return myPow(x*x,n/2) 
};
```

这个解法中，`n=0`即0次幂时会返回数值`1`，`n为偶数时`会拆分为`x*x`的`n/2`次幂计算单元，而`n/2`最终会变成奇数幂`1`，`n=1`情况下又可以拆为`x*x的0次幂`。注意，就是在`n=0`和`n为偶数`时会有计算结果，这两个最小计算单元就是我们最终拿到结果的核心之源，所有的分治方案都最终奔着这两个目标去拆分。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/powx-n



### 作业2

- [二叉树的最近公共祖先](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/)（Facebook 在半年内面试常考）

#### 题目描述

给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个节点 p、q，最近公共祖先表示为一个节点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”



示例 1：

![img](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)

```js
输入：root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
输出：3
解释：节点 5 和节点 1 的最近公共祖先是节点 3 。
```

示例 2：

![img](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)

```js
输入：root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
输出：5
解释：节点 5 和节点 4 的最近公共祖先是节点 5 。因为根据定义最近公共祖先节点可以为节点本身。
```


示例 3：

```js
输入：root = [1,2], p = 1, q = 2
输出：1
```

#### 题解

这道题如果用js解的话，也是可以的，不过由于在js中似乎没有二叉树这个数据结构，所以就算写好了代码，也是无法在除了leetcode之外的环境中运行吧？！我不太确定。

此题的解法，用的是递归，看了题解看好久才能明白。最终的情况无非三种：左子树上有这两个点、右子树上有这两个点、根节点上有其中一个点。前两种，显然还要继续递归下去找的，最后一种就是可以明确根节点就是要找的公共祖先。

由此，我们可以先写出一个递归基本框架：

```js
const dfs = (root, p, q) => {
    if (root === null) return false;
    const lson = dfs(root.left, p, q);
    const rson = dfs(root.right, p, q);
    //todo
    //找到公共祖先
    
    //lson或者rson会继续递归；
    //根节点有其一，就会停止递归，返回上一步的值
    return lson || rson || (root.val === p.val || root.val === q.val);
}
```

好了，框架有了，如何得到返回值？这个其实也可以想到：最简单模型就是根节点的左右节点就是输入的两个节点，这种情况此根节点就是公共祖先了；另一种，前面提到过，根节点是其中一个输入节点，那此根节点也是公共祖先。

ok，返回值模型有了，我就按最简单的情况输出返回值(假设这个二叉树就是最简单的那种)：

```js
    //1、左右都有一个的情况
    //lson && rson
    
    //2、根节点有其一，且子节点还有一个
    //(root.val === p.val|| root.val === q.val) && (lson||rson))

    //以上两种情况下，root就是所要的返回值
```

最后尝试组装下代码：

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    let ans;
    const dfs = (root, p, q) => {
        if (root === null) return false;
        const lson = dfs(root.left, p, q);
        const rson = dfs(root.right, p, q);
        if ((lson && rson) || ((root.val === p.val || root.val === q.val) && (lson || rson))) {
            ans = root;
        } 
        return lson || rson || (root.val === p.val || root.val === q.val);
    }
    dfs(root, p, q);
    return ans;
};
```

这里面有个情况需要测试才能确定是否正确：就是根节点有其一的情况，这种情况下，dfs执行后就得到了值，但是还是会走一次递归，不过递归中，不会再返回值了，上一次就返回的就是所要的结果。



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
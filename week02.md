## 本周作业



### 作业01

- [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/description/)（亚马逊、Facebook、谷歌在半年内面试中考过）

#### 题目描述

- 给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

  注意：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词。

   

  **示例 1**:

  ```js
  输入: s = "anagram", t = "nagaram"
  输出: true
  ```

  **示例 2**:

  ```js
  输入: s = "rat", t = "car"
  输出: false
  ```

  **提示**:

  - 1 <= s.length, t.length <= 5 * 104
  - s 和 t 仅包含小写字母

#### 题解

这个题我觉得就是用到哈希表的特性来解决，给一个字符串，经过哈希算法存到一个数组中，这个过程会有哈希碰撞的过程，每次碰撞都是重复累加；然后以此数组去评判另一个字符串，因为每个字符已经哈希化了，我可以在对应索引位置反向累减；这样操作之后，如果两个字符串满足条件，就能得到一个26个位置全是0的数组；

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    const num = new Array(26).fill(0);
    //哈希算法
    for(let ch of s){
        //碰撞重复累加
        num[ch.charCodeAt() - 'a'.charCodeAt()]++
    }
    for(let ct of t){
        num[ct.charCodeAt() - 'a'.charCodeAt()] > 0 && num[ct.charCodeAt() - 'a'.charCodeAt()]--
    }
    var rs = num.reduce(function(pre,cur,index){
        return pre+cur
    })
    return rs === 0 && s.length === t.length ? true: false;
};
```

有些细节要注意：

- 累减时，数组中的元素值不能小于0，这样可以避开后面的字符串中某个字符有多的情况；
- 最后判断时，要注意判断两个字符串长度是否一致



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/valid-anagram
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

### 作业02

- [ N 叉树的前序遍历](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/description/)（亚马逊在半年内面试中考过）

#### 题目描述

给定一个 N 叉树，返回其节点值的 前序遍历 。

N 叉树 在输入中按层序遍历进行序列化表示，每组子节点由空值 null 分隔（请参见示例）。

 

进阶：

递归法很简单，你可以使用迭代法完成此题吗?



**示例:**

![img](https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png)

```
输入：root = [1,null,3,2,4,null,5,6]
输出：[1,3,5,6,2,4]
```

**示例2：**

![img](https://assets.leetcode.com/uploads/2019/11/08/sample_4_964.png)

```js
输入：root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
输出：[1,2,3,6,7,11,14,4,8,12,5,9,13,10]

```



**提示：**

- N 叉树的高度小于或等于 `1000`
- 节点总数在范围 `[0, 10^4]` 内

#### 题解

**递归解法**

递归就比较简单了，从根节点开始，只要不是null就加到数组里去，然后子节点按序遍历，紧接着递归就行，是个程序员都会做。

```js
/**
 * @param {Node|null} root
 * @return {number[]}
 */
var preorder = function(root) {
  const res = []
  function traversal (root) {
    if (root !== null) {
      res.push(root.val)
      root.children.forEach(child => traversal(child))
    }
  }
  traversal(root)
  return res
}
```

**迭代解法**

没太看明白这个解法的意思

```js
/**
 * @param {Node|null} root
 * @return {number[]}
 */
var preorder = function(root) {
   if (!root) return [];
    const res = [];
    // 根节点入栈
    const stack = [root];
    // 栈还有值的时候
    while (stack.length) {
        // 栈顶元素出栈
        const n = stack.pop();
        // 将栈顶元素推入res队列
        res.push(n.val);
        let len = n.children.length;
        // 如果栈顶元素有子树，子树从右开始，依次推入栈
        while (len--) {
            stack.push(n.children[len]);
        }
    }
    return res; 
}
```



[作业02来源链接](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/)

### 作业03









### 作业0x




## 第四周作业

### 作业1

- [分发饼干](https://leetcode-cn.com/problems/assign-cookies/description/)（亚马逊在半年内面试中考过）

#### 题目描述

假设你是一位很棒的家长，想要给你的孩子们一些小饼干。但是，每个孩子最多只能给一块饼干。

对每个孩子 i，都有一个胃口值 g[i]，这是能让孩子们满足胃口的饼干的最小尺寸；并且每块饼干 j，都有一个尺寸 s[j] 。如果 s[j] >= g[i]，我们可以将这个饼干 j 分配给孩子 i ，这个孩子会得到满足。你的目标是尽可能满足越多数量的孩子，并输出这个最大数值。


示例 1:

```js
输入: g = [1,2,3], s = [1,1]
输出: 1
解释: 
你有三个孩子和两块小饼干，3个孩子的胃口值分别是：1,2,3。
虽然你有两块小饼干，由于他们的尺寸都是1，你只能让胃口值是1的孩子满足。
所以你应该输出1。
```


示例 2:

```js
输入: g = [1,2], s = [1,2,3]
输出: 2
解释: 
你有两个孩子和三块小饼干，2个孩子的胃口值分别是1,2。
你拥有的饼干数量和尺寸都足以让所有孩子满足。
所以你应该输出2.
```


提示：

- 1 <= g.length <= 3 * 104
- 0 <= s.length <= 3 * 104
- 1 <= g[i], s[j] <= 231 - 1



#### 题解

此题比车简单，主要是体会下贪心解法，贪心解法，意思就是每一步都要追求极致，局部最优，且无法回退。

```js
/**
 * @param {number[]} g
 * @param {number[]} s
 * @return {number}
 */
var findContentChildren = function(g, s) {
    g.sort((a, b) => a - b);
    s.sort((a, b) => a - b);
    let i = 0, j =0;
    while (i < g.length && j < s.length) {
        if(g[i] <= s[j])
            i++;
        j++;
    }
    return i;
};
```

这题的思路在题目中也给了，就是尽量让每个人都能分到刚好匹配自己胃口的饼干。这里先把胃口与饼干进行排序，从最小的饼干开始遍历，饼干满足的就记一个有效值，不满足就看下一个饼干是否满足要求；最终返回累加的有效值。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/assign-cookies



### 作业2

- [搜索旋转排序数组](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)（Facebook、字节跳动、亚马逊在半年内面试常考）

#### 题目描述

整数数组 nums 按升序排列，数组中的值 互不相同 。

在传递给函数之前，nums 在预先未知的某个下标 k（0 <= k < nums.length）上进行了 旋转，使数组变为 [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]（下标 从 0 开始 计数）。例如， [0,1,2,4,5,6,7] 在下标 3 处经旋转后可能变为 [4,5,6,7,0,1,2] 。

给你 旋转后 的数组 nums 和一个整数 target ，如果 nums 中存在这个目标值 target ，则返回它的下标，否则返回 -1 。

 

**示例 1：**

```js
输入：nums = [4,5,6,7,0,1,2], target = 0
输出：4
```


**示例 2：**

```js
输入：nums = [4,5,6,7,0,1,2], target = 3
输出：-1
```


**示例 3：**

```js
输入：nums = [1], target = 0
输出：-1
```



**提示：**

- 1 <= nums.length <= 5000
- -10^4 <= nums[i] <= 10^4
- nums 中的每个值都 独一无二
- 题目数据保证 nums 在预先未知的某个下标上进行了旋转
- -10^4 <= target <= 10^4

**进阶：**你可以设计一个时间复杂度为 O(log n) 的解决方案吗？



#### 题解

这题看着简单，因为常规解法很容易想到，直接暴力遍历就可以了。看代码：

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    var res = -1
    for(var i = 0; i <nums.length; i++) {
        if(nums[i] === target) {
            res = i
            return res;
        }
    }
    return res;
};
```

这种解法的时间复杂度是O(n);

此题还有更好的解法：二分查找！它的时间复杂度是O(logn)，题目中也提到了这个，向我们发起了挑战！来看如何接招吧！

先介绍下二分查找这个算法，非常适合这种题目。这是有一定套路的解法，主要就是约定几个索引位，从数组两头向中间进行夹逼推进，最终找到目标值。而在每次推进过程中都会舍弃掉当前资源中的一半，这样算下去，最终的时间复杂度就是O(logn)。它的套路解法还有一个代码模板，适合初学的人理解记忆：

```js
left,right = 0,len(array) -1
while left<= right;
	mid = (left + right)/2
	if array[mid] == target;
		#find the target!!
        break or return result
	elif array[mid]< target:
    	left = mid + 1
	else:
    	right = mid - 1
```

简单解释就是，初始变量设置数组的一头一尾的索引位置，然后取其中间位置，这个中间位置就可以将数组分为两段，接着去判断目标值所在的大概位置，同时调整查找范围，这样不断的排除查找，最终锁定目标值。

落到此题目中来，原本的一个顺序数组在某个位置旋转了，这样一来，取了中间值之后，左侧部分可能是有序的，也可能是包含旋转点即无序的。如果左侧有序，就判断目标值是否在左侧范围，不在就把左索引移至mid + 1；如果左侧无序，就判断目标值是否在左侧范围，不在就把左索引移至 mid + 1;其他情况（即在左侧）就移动右索引至mid；这样不断夹逼，头索引位(尾索引也是)会不断逼近目标值，直到他们相遇，此时目标值也好判断了。js要考虑特殊情况，因为像最后推到只有两个元素时，算出来的mid是0；这时直接判断两个元素是否匹配就可以了，不纠结！

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    var lo = 0,hi = nums.length -1;
    while(lo < hi){
        var mid = parseInt((lo + hi)/2);
        if(nums[mid] === target) return mid;
        if(nums[mid + 1] === target) return mid+1;
        if(nums[0] < nums[mid] && (target > nums[mid] || target < nums[0])){
            lo = mid + 1;
        } else if (target > nums[mid]&&target < nums[0]){
            lo = mid + 1;
        } else {
            hi = mid;
        }
    }
    return nums[lo] == target ? lo : -1;
};
```



来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/search-in-rotated-sorted-array
## 本周作业



### 作业01

- [删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)（Facebook、字节跳动、微软在半年内面试中考过）

#### 题目描述

给你一个有序数组 nums ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。

不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。



**说明:**

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以「引用」方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

```js
// nums 是以“引用”方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中 该长度范围内 的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

**示例 1：**

```js
输入：nums = [1,1,2]
输出：2, nums = [1,2]
解释：函数应该返回新的长度 2 ，并且原数组 nums 的前两个元素被修改为 1, 2 。不需要考虑数组中超出新长度后面的元素。
```

**提示：**

- `0 <= nums.length <= 3 * 104`
- `-104 <= nums[i] <= 104`
- `nums` 已按升序排列

#### 题解

首先注意审题，要注意以下几点：

1、有序数组，这个条件比较重要，直接决定了后面的算法设计思路

2、原地删除重复元素，不使用额外空间

这里用到的解法就是快慢指针法，由于数据是有序的，所以，如果有同的元素，那肯定是在一起了，所以这里设计快慢指针，就是为了把重复元素压缩，通过慢指针记录下最终的不重复的元素个数。来看具体解法代码：

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    const n = nums.length;
    if (n === 0) {
        return 0;
    }
    let fast = 1, slow = 1;
    // 从第二个元素开始遍历整个数组
    while (fast < n) {
        // 如果快指针对应元素与上一个元素不同
        // 则修改慢指针对应值，同进慢指针推进一位
        if (nums[fast] !== nums[fast - 1]) {
            nums[slow] = nums[fast];
            ++slow;
        }
        ++fast;
    }
    return slow;
};
```

这道题的解法其实比较容易理解，比较难理解的是，如果你的入参只是一个重复数组，这个解法是对的，但是如果你传入一个引用对象的数组，返回结果就是错误的。虽然原题中有分析，不过我还是没太明白怎么回事。



### 作业02

- [移动零](https://leetcode-cn.com/problems/move-zeroes/)（Facebook、亚马逊、苹果在半年内面试中考过）

#### 题目描述

给定一个数组 `nums`，编写一个函数将所有 `0` 移动到数组的末尾，同时保持非零元素的相对顺序。

**示例:**

```
输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
```

**说明**:

1. 必须在原数组上操作，不能拷贝额外的数组。
2. 尽量减少操作次数。

#### 题解

此题仍然是一个快慢指针法，定义两个指针，一个快指针i，一个慢指针j，i仍然是一个不停顿遍历，从0位开始，只要对应元素不是0，就给到慢指针对应索引位置，此时慢指针推进一位；这里需要注意的是，i快一些，在遇到非0元素已经给到了j位置，所以当前的i位置就要用0替换掉；后面的j追上了之前的i位置，会用非零替换0。总之，j走过的位置，一定是0：本身是0或者被替换为0，i走过的位置只会是非0。来看具体解法：

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var j = 0;
    for(var i = 0;i< nums.length; i++){
        if(nums[i] != 0){
            nums[j] = nums[i]
            if(i!=j){
                nums[i] = 0;
            }
            j++;
        }
    }
    return nums
};
```



### 作业03





来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array



### 作业0x

- 用 add first 或 add last 这套新的 API 改写 Deque 的代码


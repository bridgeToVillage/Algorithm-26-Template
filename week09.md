## 第九周作业

### 作业1

- 用自己熟悉的编程语言，手写各种初级排序代码，提交到学习总结中。

#### 选择排序

```js
function selectionSort(arr) {
    var len = arr.length;
    var minIndex, temp;
    for(var i = 0; i < len - 1; i++) {
        minIndex = i;
        for(var j = i + 1; j < len; j++) {
            if(arr[j] < arr[minIndex]) {    // 寻找最小的数
                minIndex = j;                // 将最小数的索引保存
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
} 
```



#### 插入排序

```js
// javascript
function insertionSort(arr) {
    varlen = arr.length;
    varpreIndex, current;
    for(vari = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while(preIndex >= 0 && arr[preIndex] > current) {
            arr[preIndex + 1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex + 1] = current;
    }
    return arr;
}
```



#### 冒泡排序

```js
// javascript
function bubbleSort(arr) {
    var len = arr.length;
    for(var i = 0; i < len - 1; i++) {
        for(var j = 0; j < len - 1 - i; j++) {
            if(arr[j] > arr[j+1]) {       // 相邻元素两两对比
                var temp = arr[j+1];       // 元素交换
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```



#### 快排代码

```js
// JavaScript
const quickSort = (nums, left, right) => {  
    if (nums.length <= 1) return nums  
    if (left < right) {    
        index = partition(nums, left, right)    
        quickSort(nums, left, index-1)    
        quickSort(nums, index+1, right)  
    }}      
const partition = (nums, left, right) => {  
    let pivot = left, index = left + 1  
    for (let i = index; i <= right; i++) {    
        if (nums[i] < nums[pivot]) {      
            [nums[i], nums[index]] = [nums[index], nums[i]]      
            index++    
        }  
    }  
    [nums[pivot], nums[index-1]] = [nums[index-1], nums[pivot]]  
    return index -1
}
```

#### 归并排序

```js
// JavaScript
const mergeSort = (nums) => {  
    if (nums.length <= 1) return nums  
    let mid = Math.floor(nums.length/2),       
        left = nums.slice(0, mid),       
        right = nums.slice(mid)  
    return merge(mergeSort(left), mergeSort(right))}
const merge = (left, right) => {  
    let result = []  
    while(left.length && right.length) {    
        result.push(left[0] <= right[0] ? left.shift() : right.shift())  
    }  
    while(left.length) 
        result.push(left.shift())  
    while(right.length) 
        result.push(right.shift())  
    return result
}
```



#### 堆排序

```js
// Javascript
function heapSort(arr) {  
    if (arr.length === 0) return;  
    let len = arr.length;  // 建堆  
    for (let i = Math.floor(len / 2) - 1; i >= 0; i--) {    
        heapify(arr, len, i);  }  // 排序  
    for (let i = len - 1; i >= 0; i--) {    
        // 堆顶元素与最后一个互换    
        [arr[0], arr[i]] = [arr[i], arr[0]];    // 对 0 ～ i 的数组建堆    
        heapify(arr, i, 0);  
    }}
function heapify(arr, len, i) {  
    let left = i * 2 + 1;  
    let right = i * 2 + 2;  
    let largest = i;  
    if (left < len && arr[left] > arr[largest]) {    
        largest = left;  
    }  
    if (right < len && arr[right] > arr[largest]) {    
        largest = right;  
    }  
    if (largest !== i) {    
        [arr[i], arr[largest]] = [arr[largest], arr[i]];    
        heapify(arr, len, largest);  
    }
}
```



### 作业2

- [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/)（Facebook、亚马逊、谷歌在半年内面试中考过）

#### 题目描述

给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的字母异位词。

注意：若 s 和 t 中每个字符出现的次数都相同，则称 s 和 t 互为字母异位词。

 

**示例 1:**

```js
输入: s = "anagram", t = "nagaram"
输出: true
```


**示例 2:**

```js
输入: s = "rat", t = "car"
输出: false
```



**提示:**

- 1 <= s.length, t.length <= 5 * 104
- s 和 t 仅包含小写字母



**进阶**: 如果输入字符串包含 unicode 字符怎么办？你能否调整你的解法来应对这种情况？



#### 题解

题目其实很简单，简单到想直接上手去数，如果手指头不够，可以加上脚指头。那如果用计算机语言来表达，是否有更合适的方法呢，肯定是有的！可以直接用上js数组的sort方法，先排序再重新组合为字符串，最后就能判断了。这是最简单的！直接上代码了：

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    return s.length == t.length && [...s].sort().join('') === [...t].sort().join('')
};
```

这个得复杂度分析，我有点不知如何下手，是不是得看下源码了。。

这道题如果按这个解法，其实也没必要写题解了，下面介绍另一个解法，也是值得掌握的一个技巧。由于字符串全是小写字母，再联想到`charCodeAt`api可以返回字母对应的`unicode值`，这就打开了一个新思路：先把一个字符串映射到一个数组中，索引位置代表26个英文字母，索引值代表该字母出现次数；然后另一个字符串映射之后与前一个一一对比就能有结果了。有了这个思路，就可以试着自己写下代码了。

下面给出代码：

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    var num = new Array(26).fill(0);
    for(var ch of s) {
        num[ch.charCodeAt() - 'a'.charCodeAt()]++
    }
    for(var ct of t){
        num[ct.charCodeAt() - 'a'.charCodeAt()] > 0 && num[ct.charCodeAt() - 'a'.charCodeAt()]--
    }

    var rs = num.reduce((pre, cur,index) =>{
        return pre + cur
    })
    return rs === 0 && s.length === t.length ? true : false
};
```




## 第十周作业

### 作业1

- [字符串中的第一个唯一字符
  ](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)（亚马逊、微软、Facebook 在半年内面试中考过）

#### 题目描述

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

 

**示例：**

```js
s = "leetcode"
返回 0

s = "loveleetcode"
返回 2
```



**提示：**你可以假定该字符串只包含小写字母。

#### 题解

这题用暴力解法就是遍历，每次遍历把当前字符串的个数统计一次，这样如果字符串的长度为n，则时间复杂度可能是n*n。

为了降低复杂度，得换一个思路，同样是统计字符串个数，这里可以用哈希法，巧用`charCodeAt`这个api，将入参字符串的每个字符的个数存在26位的数组中，索引0-25代表对应的字符a-z。

接着，只需要再次从头遍历入参字符串的每个字符，从上面的数组中找到其对应的个数，如果等于1，就找到结果了，因为我是从头遍历的，直接停止，返回结果就可以了。

```js
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function(s) {
    var az = new Array(26).fill(0);
    var re = s.split('');
    var res = -1;
    for(var x of s){
         az[x.charCodeAt() - 'a'.charCodeAt()]++;
    }
    for(var i =0;i<re.length;i++) {
        if(az[re[i].charCodeAt() - 'a'.charCodeAt()] === 1){
            res = i;
            break;
        }else {
            res = -1;
        }
    }
    return res;
};
```

#### 复杂度

时间复杂度：O(n)，其中 n 是字符串 s 的长度。第一次遍历字符串的时间复杂度为 O(n)，第二次遍历哈希映射的时间复杂度一定小于 s 的长度，因此 小于 O(n)O(n)，可以忽略。

空间复杂度：O(∣Σ∣)，其中Σ 是字符集，在本题中 s 只包含小写字母，因此∣Σ∣≤26。我们需要 O(∣Σ∣) 的空间存储哈希映射。


题目链接：https://leetcode-cn.com/problems/first-unique-character-in-a-string/



### 作业2

- [反转字符串 II ](https://leetcode-cn.com/problems/reverse-string-ii/)（亚马逊在半年内面试中考过）

#### 题目描述

给定一个字符串 s 和一个整数 k，从字符串开头算起，每计数至 2k 个字符，就反转这 2k 字符中的前 k 个字符。

- 如果剩余字符少于 k 个，则将剩余字符全部反转。
- 如果剩余字符小于 2k 但大于或等于 k 个，则反转前 k 个字符，其余字符保持原样。

**示例 1：**

```js
输入：s = "abcdefg", k = 2
输出："bacdfeg"
```


**示例 2：**

```js
输入：s = "abcd", k = 2
输出："bacd"
```



**提示：**

- 1 <= s.length <= 10<sup>4</sup>
- s 仅由小写英文组成
- 1 <= k <=10<sup>4</sup>

#### 题解

```js
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var reverseStr = function(s, k) {
    let res = '';
    const n = s.length;
    for(let i = 0;i < n;i += 2 * k){
        res += s.substr(i,k).split('').reverse().join('') + s.substr(i+k,k);
    }
    return res;
};

作者：javascript-8
链接：https://leetcode-cn.com/problems/reverse-string-ii/solution/jian-dan-zi-fu-chuan-pin-jie-by-javascri-loru/
```

学习下尤雨溪的题解



题目链接：https://leetcode-cn.com/problems/reverse-string-ii
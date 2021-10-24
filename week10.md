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



### 作业3

- [字符串解码](https://leetcode-cn.com/problems/decode-string/)

#### 题目描述

给定一个经过编码的字符串，返回它解码后的字符串。

编码规则为: k[encoded_string]，表示其中方括号内部的 encoded_string 正好重复 k 次。注意 k 保证为正整数。

你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。

此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 k ，例如不会出现像 3a 或 2[4] 的输入。

 

示例 1：

输入：s = "3[a]2[bc]"
输出："aaabcbc"
示例 2：

输入：s = "3[a2[c]]"
输出："accaccacc"
示例 3：

输入：s = "2[abc]3[cd]ef"
输出："abcabccdcdcdef"
示例 4：

输入：s = "abc3[cd]xyz"
输出："abccdcdcdxyz"



#### 题解

```js
/**
 * @param {string} s
 * @return {string}
 */
var decodeString = function(s) {
    let numStack = [];        // 存倍数的栈
    let strStack = [];        // 存 待拼接的str 的栈
    let num = 0;              // 倍数的“搬运工”
    let result = '';          // 字符串的“搬运工”
    for (const char of s) {   // 逐字符扫描
        if (!isNaN(char)) {   // 遇到数字
            num = num * 10 + Number(char); // 算出倍数
        } else if (char == '[') {  // 遇到 [
            strStack.push(result); // result串入栈
            result = '';           // 入栈后清零
            numStack.push(num);    // 倍数num进入栈等待
            num = 0;               // 入栈后清零
        } else if (char == ']') {  // 遇到 ]，两个栈的栈顶出栈
            let repeatTimes = numStack.pop(); // 获取拷贝次数
            result = strStack.pop() + result.repeat(repeatTimes); // 构建子串
        } else {                   
            result += char;        // 遇到字母，追加给result串
        }
    }
    return result;
};
```



链接：https://leetcode-cn.com/problems/decode-string



#### 作业4

- [翻转字符串里的单词](https://leetcode-cn.com/problems/reverse-words-in-a-string/)（微软、字节跳动、苹果在半年内面试中考过）

#### 题目描述



给你一个字符串 s ，逐个翻转字符串中的所有 单词 。

单词 是由非空格字符组成的字符串。s 中使用至少一个空格将字符串中的 单词 分隔开。

请你返回一个翻转 s 中单词顺序并用单个空格相连的字符串。

说明：

输入字符串 s 可以在前面、后面或者单词间包含多余的空格。
翻转后单词间应当仅用一个空格分隔。
翻转后的字符串中不应包含额外的空格。


示例 1：

输入：s = "the sky is blue"
输出："blue is sky the"
示例 2：

输入：s = "  hello world  "
输出："world hello"
解释：输入字符串可以在前面或者后面包含多余的空格，但是翻转后的字符不能包括。
示例 3：

输入：s = "a good   example"
输出："example good a"
解释：如果两个单词间有多余的空格，将翻转后单词间的空格减少到只含一个。
示例 4：

输入：s = "  Bob    Loves  Alice   "
输出："Alice Loves Bob"
示例 5：

输入：s = "Alice does not even like bob"
输出："bob like even not does Alice"


提示：

1 <= s.length <= 104
s 包含英文大小写字母、数字和空格 ' '
s 中 至少存在一个 单词


进阶：

请尝试使用 O(1) 额外空间复杂度的原地解法。



#### 题解：

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    return s.trim().split(/\s+/).reverse().join(' ')
};
```




链接：https://leetcode-cn.com/problems/reverse-words-in-a-string


# 简单

## 387. 字符串中的第一个唯一字符
1. https://leetcode-cn.com/problems/first-unique-character-in-a-string/
2. 题目: 
+ 给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

+ 示例:
```
s = "leetcode"
返回 0

s = "loveleetcode"
返回 2
```

3. 思路:
+ 遍历一遍字符串，然后把字符串中每个字符出现的次数保存在一个散列表中
+ 遍历一次字符串，这一次利用散列表来检查遍历的每个字符是不是唯一的。如果当前字符唯一，直接返回当前下标就可以了

4. 代码: 
```js

var firstUniqChar = function (s) {
  let map = new Map();
  for (let i = 0; i < s.length; i++) {
    let count = map.get(s[i]) || 0;
    map.set(s[i], count + 1);
  }
  for (let i = 0; i < s.length; i++) {
    if (map.get(s[i]) === 1) return i;
  }
  return -1;
};

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  | 散列表 | 1|

## 541. 反转字符串 II
1. https://leetcode-cn.com/problems/reverse-string-ii/
2. 题目: 
+ 给定一个字符串 s 和一个整数 k，你需要对从字符串开头算起的每隔 2k 个字符的前 k 个字符进行反转。
  - 如果剩余字符少于 k 个，则将剩余字符全部反转。
  - 如果剩余字符小于 2k 但大于或等于 k 个，则反转前 k 个字符，其余字符保持原样。

+ 示例:
```
输入: s = "abcdefg", k = 2
输出: "bacdfeg"
```

3. 思路:
+ 将字符串分割，依次去反转。

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  |  | 1|




## 151. 翻转字符串里的单词
1. https://leetcode-cn.com/problems/reverse-words-in-a-string/
2. 题目: 
+ 给定一个字符串，逐个翻转字符串中的每个单词。
+ 示例:
```
输入: "the sky is blue"
输出: "blue is sky the"

输入: "  hello world!  "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。

输入: "a good   example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

```
说明
+ 无空格字符构成一个单词。
+ 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
+ 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

3. 正则
    ```js
        var reverseWords = function(s) {
            return s.trim().replace(/\s+/g, ' ').split(' ').reverse().join(' ')
        };

    ```

4. 双端队列
+ 首先去除字符串左右空格
+ 逐个读取字符串中的每个单词，依次放入双端队列的对头
+ 再将队列转换成字符串输出（已空格为分隔符） 
参考 https://leetcode-cn.com/problems/reverse-words-in-a-string/solution/tu-jie-leetcodefan-zhuan-zi-fu-chuan-li-de-dan-ci-/


5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  | 双端队列 | 1|


## 917. 仅仅反转字母
1. https://leetcode-cn.com/problems/reverse-only-letters/

2. 题目:  
给定一个字符串 S，返回 “反转后的” 字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。
+ 示例:
```
输入："ab-cd"
输出："dc-ba"

输入："a-bC-dEf-ghIj"
输出："j-Ih-gfE-dCba"

```

3. 思路:
+ 将 s 中的所有字母单独存入栈中，所以出栈等价于对字母反序操作。（或者，可以用数组存储字母并反序数组。）
+ 然后，遍历 s 的所有字符，如果是字母我们就选择栈顶元素输出。


4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  |  | 1|

## 205. 同构字符串
1. https://leetcode-cn.com/problems/isomorphic-strings/
2. 题目: 
+ 给定两个字符串 s 和 t，判断它们是否是同构的。
  - 如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。
  - 所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。

+ 示例:
```
输入: s = "egg", t = "add"
输出: true

输入: s = "foo", t = "bar"
输出: false

```

3. 思路:
+ 参考: https://leetcode-cn.com/problems/isomorphic-strings/solution/xiang-xi-tong-su-de-si-lu-fen-xi-duo-jie-fa-by-42/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  |  | 1|


## 680. 验证回文字符串 Ⅱ
1. https://leetcode-cn.com/problems/valid-palindrome-ii/
2. 题目: 
+ 给定一个非空字符串 s，最多删除一个字符。判断是否能成为回文字符串。
+ 示例:
```
输入: "aba"
输出: True

```

3. 思路:
+ https://leetcode-cn.com/problems/valid-palindrome-ii/solution/cong-liang-ce-xiang-zhong-jian-zhao-dao-bu-deng-de/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03 |   1  |  | 1|



# 中等

## 300. 最长上升子序列 [dp]
1. https://leetcode-cn.com/problems/longest-increasing-subsequence/
2. 题目: 
+ 给定一个无序的整数数组，找到其中最长上升子序列的长度。
+ 示例:
```
输入: [10,9,2,5,3,7,101,18]
输出: 4 
解释: 最长的上升子序列是 输入: [10,9,2,5,3,7,101,18]

```

3. 思路:
+ 参考 : https://leetcode-cn.com/problems/longest-increasing-subsequence/solution/dong-tai-gui-hua-er-fen-cha-zhao-tan-xin-suan-fa-p/
+ dp[i] = Math.max(dp[i], dp[j] + 1);

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  |  | 1|



## 91. 解码方法 [dp]
1. https://leetcode-cn.com/problems/decode-ways/

2. 题目: 
+ 一条包含字母 A-Z 的消息通过以下方式进行了编码
  ```
    'A' -> 1
    'B' -> 2
    ...
    'Z' -> 26
  ```
+ 示例:
```
输入: "12"
输出: 2
解释: 它可以解码为 "AB"（1 2）或者 "L"（12）。
```

3. 思路:
+ 参考 https://leetcode-cn.com/problems/decode-ways/solution/dong-tai-gui-hua-java-python-by-liweiwei1419/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 09.03  |   1  | dp | 1|



## 5. 最长回文子串
1. https://leetcode-cn.com/problems/longest-palindromic-substring/
2. 题目: 给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。
3. 示例:
```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。
```
4. 思路:
https://leetcode-cn.com/problems/longest-palindromic-substring/solution/zhong-xin-kuo-san-dong-tai-gui-hua-by-liweiwei1419/


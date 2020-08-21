# Lesson 13 Trie树(字典树) - [08.17]

## 102. 二叉树的层序遍历 [week4] [!!!] [BFS的主要应用: 层序变量]
1. https://leetcode-cn.com/problems/binary-tree-level-order-traversal/
2. 题目: 
+ 给你一个二叉树，请你返回其按 层序遍历 得到的节点值。 （即逐层地，从左到右访问所有节点）。
+ 示例:
```
二叉树：[3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7

```

返回: 
```

[
  [3],
  [9,20],
  [15,7]
]
```

3. 思路:
+  参考: https://leetcode-cn.com/problems/binary-tree-level-order-traversal/solution/bfs-de-shi-yong-chang-jing-zong-jie-ceng-xu-bian-l/

4. core code: 
```js
  for: 0 to n
    let node = queue.pop();
    level.push(node.val);
    if(node.left) queue.unshift(node.left)
    if(node.right) queue.unshift(node.right)

  result.push(level)

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20  |   1  | BFS | 1|





## 208. 实现 Trie (前缀树)
1. https://leetcode-cn.com/problems/implement-trie-prefix-tree/#/description
2. 题目: 
+ 实现一个 Trie (前缀树)，包含 insert, search, 和 startsWith 这三个操作
+ 示例:
```
  Trie trie = new Trie();

  trie.insert("apple");
  trie.search("apple");   // 返回 true

```

3. 思路:
+ 参考: https://xxoo521.com/2020-02-29-trie-prefix-tree/
+ 封装节点:
  - next: next[i] 保存着下一个字符i的节点引用
  - isEnd: 当前节点是否可以作为一个单词的结束位置
+ 节点本身不存储字符，字符是保存在next对象中的 key 中。直观来看，字符是保存在节点之间的连线上的

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20  |   1  |  | 1|







## 212. 单词搜索 II [too hard] [Trie] [TODO]
1. https://leetcode-cn.com/problems/word-search-ii/
2. 题目: 
+ 略
+ 示例:
```
输入: 
words = ["oath","pea","eat","rain"] and board =
[
  ['o','a','a','n'],
  ['e','t','a','e'],
  ['i','h','k','r'],
  ['i','f','l','v']
]

输出: ["eat","oath"]

```

3. 思路:
+ 把所有单词构造成前缀树
+ 再遍历 board, 用DFS分别在前缀树上跑

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |






# Lesson 13 并查集 - [08.17]

## 547. 朋友圈 [并查集] [想法高亮]
1. https://leetcode-cn.com/problems/friend-circles/
2. 题目: 
+ 给定一个 N * N 的矩阵 M，表示班级中学生之间的朋友关系。如果M[i][j] = 1，表示已知第 i 个和 j 个学生互为朋友关系，否则为不知道。你必须输出所有学生中的已知的朋友圈总数

+ 示例:
```
输入：
[[1,1,0],
 [1,1,0],
 [0,0,1]]
输出：2 
解释：已知学生 0 和学生 1 互为朋友，他们在一个朋友圈。
第2个学生自己在一个朋友圈。所以返回 2 。

```

3. 思路: 
+ 参考: 
  - https://leetcode-cn.com/problems/friend-circles/solution/union-find-suan-fa-xiang-jie-by-labuladong/
  - https://leetcode-cn.com/problems/friend-circles/solution/547-peng-you-quan-by-alexer-660/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20  |   1  | Union-Find| 1|


## 200. 岛屿数量 [week3:dfs] [union-find] 
1. https://leetcode-cn.com/problems/number-of-islands/
2. 题目: 
+ 
+ 示例:
```
输入:
[
['1','1','1','1','0'],
['1','1','0','1','0'],
['1','1','0','0','0'],
['0','0','0','0','0']
]
输出: 1

```

3. 思路:
+ dfs
+ union-find
+ refers: https://leetcode-cn.com/problems/number-of-islands/solution/dfs-bfs-bing-cha-ji-python-dai-ma-java-dai-ma-by-l/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.18  |   1  | union-find | 1|


## 130. 被围绕的区域 [medim]
1. https://leetcode-cn.com/problems/surrounded-regions/
2. 题目: 
+ 给定一个二维的矩阵，包含 'X' 和 'O'（字母 O. 找到所有被 'X' 围绕的区域，并将这些区域里所有的 'O' 用 'X' 填充。
+ 示例:
```
X X X X
X O O X
X X O X
X O X X

```
返回: 
```
X X X X
X X X X
X X X X
X O X X
```
+ 被围绕的区间不会存在于边界上，换句话说，任何边界上的 'O' 都不会被填充为 'X'。 任何不在边界上，或不与边界上的 'O' 相连的 'O' 最终都会被填充为 'X'。如果两个元素在水平或垂直方向相邻，则称它们是“相连”的。

3. 思路:
+ 参考: https://leetcode-cn.com/problems/surrounded-regions/solution/dfs-bfs-bing-cha-ji-by-powcai/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20  |   1  | union-find | 1|


# Lesson 14 高级搜索 - 减枝 - [08.18]

## 22. Generate Parentheses  [review]
1. https://leetcode-cn.com/problems/generate-parentheses/
2. code:
```js
var generateParenthesis = function(n) {
    let res = [];
    function helper(countL, countR, str) {
        if(countL == n && countR == n){
            res.push(str);
            return;
        }

        if(countL < n) {
            helper(countL+1, countR, str+"(");
        }

        if(countR < countL) {
            helper(countL, countR+1, str+")");
        }
    }
    
    helper(0, 0, "");
    return res;
  }
```


## 51. N皇后 [hard]
1. https://leetcode-cn.com/problems/n-queens/
2. 题目: 
+ 
+ 示例:
```

```

3. 思路:
+ 

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |



## 36. 有效的数独 [medium] [高亮]
1. https://leetcode-cn.com/problems/valid-sudoku/description/
2. 题目: 
+ 略

3. 思路:
+ 参考:
  - https://leetcode-cn.com/problems/valid-sudoku/solution/you-xiao-de-shu-du-by-leetcode/
  - https://leetcode-cn.com/problems/valid-sudoku/solution/36-you-xiao-de-shu-du-by-alexer-660/

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20 |   1  |  | 1|

## 37. 解数独 [too hard] [TODO]
1. https://leetcode-cn.com/problems/sudoku-solver/#/description
2. 题目: 
+ 
+ 示例:
```

```

3. 思路:
+ 

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |


# Lesson 14 高级搜索 - 双向BFS - [08.19]

## 127. 单词接龙 [week4] [BFS] [双向广度优先搜索]
1. https://leetcode-cn.com/problems/word-ladder/
2. 题目: 
+ 示例:
```
输入:
beginWord = "hit",
endWord = "cog",
wordList = ["hot","dot","dog","lot","log","cog"]
输出: 5
解释: 一个最短转换序列是 "hit" -> "hot" -> "dot" -> "dog" -> "cog",
     返回它的长度 5。

```

3. 思路:
+ 

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.19  |   1  | 双向BFS | 1|



## 433. 最小基因变化 [week4] [BFS] [双向广度优先搜索]
1. https://leetcode-cn.com/problems/minimum-genetic-mutation/
2. 题目: 
+ 略
+ 示例:
```
start: "AAAAACCC"
end:   "AACCCCCC"
bank: ["AAAACCCC", "AAACCCCC", "AACCCCCC"]
返回值: 3

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.20  |   1  | 双向BFS | 1|


# Lesson 14 - 启发式搜索 [08.20]

## 1091. 二进制矩阵中的最短路径 [BFS] [启发式]
1. https://leetcode-cn.com/problems/shortest-path-in-binary-matrix/

2. 题目: 
+ 
+ 示例:
```

```

3. 思路:
+ 

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.21  |   1  | 启发式搜索 | 1|


## 773. 滑动谜题 [too hard]
1. https://leetcode-cn.com/problems/sliding-puzzle/

2. 题目: 
+ 
+ 示例:
```

```

3. 思路:
+ 

4. 代码: 
```js

```
5. 刷题记录

|  时间   | 次数  | 备注  |   |
| :---- | :----: | :---- |:----: |
| 08.21  |   1  |  xxxx | 1|



